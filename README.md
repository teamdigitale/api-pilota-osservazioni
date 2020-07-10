# Pilota per API Osservazioni e Parametri

[![CircleCI](https://circleci.com/gh/teamdigitale/api-pilota-osservazioni.svg?style=svg)](https://circleci.com/gh/teamdigitale/api-pilota-osservazioni)
[![Join the #api channel](https://img.shields.io/badge/Slack-%23api-blue.svg?logo=slack)](https://developersitalia.slack.com/messages/CDKBYTG74)
[![Get invited](https://slack.developers.italia.it/badge.svg)](https://slack.developers.italia.it/)

Questo repository contiene il template di un'API per il Pilota Osservazioni e Parametri

## Contenuto

- Un progetto di esempio in python-flask
- Una directory `openapi` con le specifiche in formato OpenAPI 3+


### Risolvere le dipendenze negli OpenAPI

Le specifiche OpenAPI possono contenere riferimenti a schemi esterni
o [yaml anchors](). E' possibile risolverli tramite il modulo python
`openapi_resolver`, richamato dal `Makefile`.

In questo repository, i file con anchor e ref hanno estensione `.yaml.src`
ma sono a tutti gli effetti file OAS3 validi e la maggior parte dei
tool li interpreta correttamente. E' comunque possibile dereferenziarli
per comodità tramite il comando:

	make yaml



### Generare il codice del server

Il `Makefile` contiene:

  - un esempio di code generation python direttamente via openapi v3. Basta
    lanciare:

        make python-flask

Il generatore non sovrascrive i file contenuti in `.swagger-codegen-ignore`.

Il server generato viene servito tramite il wsgi container di default di `connexion`.


### Dipendenze

Per eseguire questa app servono:

```
make
python 3 + tox
docker
```


### Test

E' possibile testare in locale tramite circleci, con:

        circleci build
