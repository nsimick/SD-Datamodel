# Insurance Distribution Management — Data Model

Salesforce metadata for the proposed Insurance Distribution Management data model.
All 14 entities are new custom objects (`__c`). Names are logical Core names with the
custom-object suffix added so the metadata deploys to an org.

Source: *Salesforce Insurance Distribution Management Data Model* workbook. Every entity
is marked **Proposed — validate**: confirm physical object names, ownership, and whether
each relationship target already exists before relying on this model.

## Objects

| Object | Purpose | Sharing |
| --- | --- | --- |
| DistributionAgreement__c | Contract governing a producer's distribution rights | Private |
| ProducerAffiliation__c | Time-bound producer-to-parent-producer hierarchy | Private |
| CredentialSnapshot__c | Point-in-time licensing and appointment evaluation | Private |
| ProductAuthority__c | Producer authorization to sell or service a product | Private |
| ProducerReadiness__c | Readiness outcome for a producer against an authority | Controlled by parent |
| BindingAuthority__c | Binding limits on a product authority | Controlled by parent |
| TerritoryAssignment__c | Producer assignment to a territory, optionally by product | Private |
| ProductionScorecard__c | Periodized production measures | Private |
| GrowthOpportunity__c | Actionable growth recommendation | Private |
| ProducerPolicyAssignment__c | Effective-dated policy-to-producer assignment | Private |
| BookTransfer__c | Transfer of a book of business between producers | Private |
| BookTransferItem__c | Single policy moved under a book transfer | Controlled by parent |
| CommissionOverride__c | Producer-specific override of a commission schedule | Private |
| CommissionDispute__c | Dispute against a commission statement line | Private |

## Relationship targets that must already exist

These lookups point at standard or industry objects and are not created here:
`Producer`, `Contract`, `Product2`, `Territory2`, `User`, `Case`, `BusinessLicense`,
`AuthorizedInsuranceLine`, `InsurancePolicy`, `InsurancePolicyTransaction`,
`CommissionSchedule`, `CommissionStatementLineItem`.

`Territory` in the workbook is mapped to `Territory2` (Enterprise Territory Management).
`CurrencyIsoCode` is omitted because Salesforce supplies it automatically when
multi-currency is enabled.

## Deploy

```bash
sf project deploy start --source-dir force-app
```
