# DITA-NG Relax NG support for DITA-OT

## Building

The source is built using gradle. If you don't have gradle installed, you can use the provided gradlew command.

The default target assembles a DITA-OT compatible plugin zip archive in the dist directory.

## Installation

## Installation

The *dita* command included in DITA-OT versions 2.0 or greater can be used to install the plugin:


```
x:\dita-ot\bin\dita -install x:\files\org.dita-ng.library-0.1.zip -v
```

## Schema validation

The Relax NG support provided by DITA-NG includes adding attribute default values to the parsed result and validating the documents.

Validation can be disabled by creating a properties file:

**Properties file**:

```
x:\dita-ot\plugins\org.dita-ng.library\dita-ng.properties
```

**Validation property**:

```
validation=false
```

The default value is yes, if no configuration file is found. Any value other than "yes" or "true" is treated as "false".

## Associating a schema with a document

DITA-NG uses pseudo-attributes conforming to the W3C recommendation
"Associating Style Sheets with XML Documents".

The pseudo-attributes resemble XML attribute specifications, within
the data of a processing instruction. The attributes are:

* href - A system identifier.
* type - A MIME type (application/xml or application/relax-ng-compact-syntax)
* schematypens - The Relax NG XML syntax namespace: "http://relaxng.org/ns/structure/1.0". 

Example pseudo-attribute PIs identifying a RelaxNG schema in XML syntax:

```
<?xml-model href="specialized-concept.rng"?>

<?xml-model href="urn:oasis:names:tc:dita:rng:concept.rng"?>

<?xml-model href="urn:oasis:names:tc:dita:rng:concept.rng" type="application/xml"?>

<?xml-model href="urn:oasis:names:tc:dita:rng:concept.rng" schematypens="http://relaxng.org/ns/structure/1.0"?>
```

Example pseudo-attribute PIs identifying a RelaxNG schema in compact syntax:

```
<?xml-model href="specialized-concept.rnc"?>

<?xml-model href="urn:oasis:names:tc:dita:rng:concept.rnc"?>

<?xml-model href="urn:oasis:names:tc:dita:rng:concept.rnc" type="application/relax-ng-compact-syntax"?>
```
