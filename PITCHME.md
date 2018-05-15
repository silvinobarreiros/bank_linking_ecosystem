# Bank Linking Overview
---

# Purpose
Improve bank linking at Stash
---

# Current Projects and Services

* External Accounts
* Institution Search Service
* Stash Platform
* Stash Quovo v2 Client
* Stash Quovo v3 Client
---

# System Architecture

---?image=assets/eat_system_architecture.png&size=auto 90%
---

# External Accounts

### Purpose

External Accounts Service provides a vendor agnostic view of externally linked accounts. WTF is an externally linked account? Good question, take a seat, this is going to be a short and very boring ride. An external account is any account (checking, savings, credit card etc) linked to a Stash account using a 3rd party provider. So far we support Quovo and Plaid. External Accounts owns a Stash centric view of resources created with these providers. Meaning we create a Stash id and manage the mapping between this Stash id and the original source of the resource.
---

### Some External Accounts Features

* account linking
* account access health
* account stats
* balance check
* user information
---

### Linking an account with no MFA

---?image=assets/good_sync_flow.png&size=auto 90%
---

# Institution Search

### Purpose

Provide a cleaner search mechanism for customers when they link a bank account. Institutions are agnostic of provider and have a Stash unique identifier. 
---

### Features

* Elastic search backed type and search (there's a more producty name for this)
* Provider to Stash unique id mapping (used by External Accounts)
---

# Stash Platform

### Purpose

* Common Stash library for shared service code and domain models.
* Publishes to S3
* Easy to share client code, like quovo
* S3 == Artifactory, mimics Maven/Ivy style repo
* S3 is cheap and we already use it
---

### Shared Service Code

* Thin base server and controller wrapper for Akka Http
* Thin environment trait for cake pattern use
* Health endpoint and response
---

### Other Shared Code

* Repository layer trait
* Account, Portfolio, Transaction and User repositories
* Mongo and Plaid Mongo repository concrete implementations
* Common Json serializers and deserializers (DateTime, Enums)
---

### Domain Models

* Account, Portfolio, Transaction and User
---

# Stash Quovo v2 Client

* Client for Quovo v2
* Uses play libraries
* Part of Stash Commons repo
* Will be deprecated soon (internally only?)
---

# Stash Quovo v3 Client

* Client for Quovo v3
* Uses new nomenclature
* Uses [sttp](https://github.com/softwaremill/sttp)
* Separate repo in Github