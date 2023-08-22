# Cartesi API Specification

Version: 0.0.1-wip

## Introduction

The Cartesi API Specification defines a standard, language-agnostic interface
to Cartesi DApps, to better document how to interact with the distributed
applications. The definition can be automatically generated from an existing
DApp and also used to generate both the DApp and client codes.

## Specifications

### Format

The Cartesi API Specification file is a JSON object, which may be represented
either in JSON or YAML format.

## Schema

### CartesiAPI Object

This is the root object of a Cartesi API Description document.

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| cartesiapi | string | **REQUIRED**. This must be the version of the CartesiAPI Specification for the current document, as a string. This is not related to the Dapp version, which should be in the `info.verion` key. |
| info       | [Info Object](#info-object) | **REQUIRED**. Provides metadata about the DApp. |
| routes     | \[[Route Object](#route-object)\] | **REQUIRED**. Available ways to interact with the DApp. |
| components | [Components Object](#components-object) | Element to hold various schemas for the document |
| tags       | \[[Tag Object](#tag-object)\] | A list of tags used by the document with additional metadata. |
| externalDocs | [External Documentation Object](#external-documentation-object) | Additional external documentation |

### Info Object

Metadata about the DApp. These metadata may be used by the clients and may be
used to generate a presentation of the documentation.

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| title      | string | **REQUIRED**. The title of the DApp. |
| version    | string | **REQUIRED**. The version of the DApp. |
| summary    | string | A short summary of the DApp. |
| description | string | A long form description for the document. Can use Markdown for rich text representation. |
| termsOfService | string | A URL to the Terms of Service for the DApp. |
| license    | [License Object](#license-object) | The license information for the DApp |
| contact    | [Contact Object](#contact-object) | The contact information for the DApp |

### License Object

Licensing information for the DApp

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| name       | string | **REQUIRED**. The license name for the DApp. |
| identifier | string | An [SPDX](https://spdx.org/spdx-specification-21-web-version#h.jxpfx0ykyb60) license expression for the DApp. The `identifier` field is mutually exclusive of the `url` field. |
| url | string | A URL to the license used for the DApp. The `url` field is mutually exclusive of the `identifier` field. |

### Contact Object

Contact information for the DApp

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| name       | string | Name of the contact person/organization. |
| url        | string | The URL pointing to the contact information. |
| email      | string | The email address of the contact person/organization |

### Route Object

TODO

### Schema Object

TODO

### Tag Object

Adds metadata to a single tag. It is not mandatory to have a Tag Object per tag.

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| name       | string | **REQUIRED**. Name of the Tag. |
| description | string | A description for the tag. Markdown may be used for tich text representation. |
| externalDocs | [External Documentation Object](#external-documentation-object) | The email address of the contact person/organization |

### External Documentation Object

Reference for an external resource for extended documentation.

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| description | string | Description for the target documentation. Markdown may be used for rich text representation. |
| url        | string | The URL pointing to the documentation. |

### Components Object

Holds a set of reusable objects for different aspects of the Cartesi API
Specification. The objects defined within the components object will have no
effect unless explicitly referenced from outside, using a
[Reference Object](#reference-object)

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| schemas    | Map\[string, [Schema Object](#schema-object)\] | An object to hold reusable Schema Objects

### Reference Object

A simple object to allow referencing other components in the document.

Fields:

| Field Name | Type   | Description |
| ---------- | ------ | ----------- |
| $ref       | string | **REQUIRED**. The reference identifier. This MUST be in the form of a RFC3986 URI |
| summary    | string | A short summary which should override that of the referenced component. If the referenced object type does not allow a `summary` field, then this field has no effect. |
| description | string | A description which should override that of the referenced component. Markdown may be used for rich text representation. If the referenced object type does not allow a `description` field, then this field has no effect. |
