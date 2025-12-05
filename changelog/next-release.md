# Changelog for next release

### Bug fixes

- Fix `Attachment::xmlSerialize()` to not output `EmbeddedDocumentBinaryObject` when only an `externalReference` is set. Previously, the method always wrote the embedded document element even when there was no file content, causing invalid XML. Now the embedded document is only written when `filePath` or `base64Content` is provided.

### New features & improvements

- Add `<cac:AddressLine>` support to `<cac:Address>` for additional unstructured address lines
  - New `AddressLine` class with `getLine()` / `setLine()` methods
  - `Address::getAddressLines()` - returns array of AddressLine objects
  - `Address::setAddressLines(array $addressLines)` - set all address lines
  - `Address::addAddressLine(AddressLine $addressLine)` - add a single address line
  - Supports multiple `<cac:AddressLine>` elements per address (UBL 2.1 compliant)
- Add `<cac:OriginCountry>` support to `<cac:Item>` for specifying country of origin
- Add `DespatchDocumentReference` support to `Invoice`
  - New `DespatchDocumentReference` class with `id` property
  - Added `getDespatchDocumentReference()` / `setDespatchDocumentReference()` methods to `Invoice`
  - Full support for XML serialization and deserialization

