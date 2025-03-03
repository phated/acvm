# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.5.0](https://github.com/phated/acvm/compare/root-v0.4.1...root-v0.5.0) (2023-02-17)


### ⚠ BREAKING CHANGES

* **acir:** make PublicInputs use a BTreeSet rather than Vec ([#99](https://github.com/phated/acvm/issues/99))
* refactor ToRadix to ToRadixLe and ToRadixBe ([#58](https://github.com/phated/acvm/issues/58))
* **acir:** Add keccak256 Opcode ([#91](https://github.com/phated/acvm/issues/91))
* Reorganiser compiler in terms of optimisers and transformers ([#88](https://github.com/phated/acvm/issues/88))

### Features

* **acir:** Add keccak256 Opcode ([#91](https://github.com/phated/acvm/issues/91)) ([b909146](https://github.com/phated/acvm/commit/b9091461e199bacdd073cc9b31f03dade0b4fb2d))
* **acir:** make PublicInputs use a BTreeSet rather than Vec ([#99](https://github.com/phated/acvm/issues/99)) ([53666b7](https://github.com/phated/acvm/commit/53666b782d89c65cd755f9e4ded2c9cf5a141e46))
* **ci:** Add release workflow ([#89](https://github.com/phated/acvm/issues/89)) ([db8e828](https://github.com/phated/acvm/commit/db8e828341f59241ef7f437c908277fb8fbca9e3))
* **ci:** Publish crates upon release ([427d446](https://github.com/phated/acvm/commit/427d4468da8fb934895acce5c39f975a2c494655))
* Update Arkworks' dependencies on `acir_field` ([#69](https://github.com/phated/acvm/issues/69)) ([65d6130](https://github.com/phated/acvm/commit/65d61307a12f25e04afad2d50e4c4db5ce97dd8c))


### Bug Fixes

* Clean up Log Directive hex output  ([#97](https://github.com/phated/acvm/issues/97)) ([d23c735](https://github.com/phated/acvm/commit/d23c7352523ffb42f3e8f4229b61f9803ab78a7e))


### Miscellaneous Chores

* refactor ToRadix to ToRadixLe and ToRadixBe ([#58](https://github.com/phated/acvm/issues/58)) ([2427a27](https://github.com/phated/acvm/commit/2427a275048e598c6d651cce8348a4c55148f235))
* Reorganiser compiler in terms of optimisers and transformers ([#88](https://github.com/phated/acvm/issues/88)) ([9329307](https://github.com/phated/acvm/commit/9329307e054de202cfc55207162ad952b70d515e))

## [0.4.1] - 2023-02-08

### Added

### Fixed

- Removed duplicated logic in match branch

### Changed

### Removed

## [0.4.0] - 2023-02-08

### Added

- Add log directive
- Expose `acir_field` through `acir` crate
- Add permutation directive
- Add preprocess methods to ACVM interface

### Fixed

### Changed

- Changed spellings of many functions to be correct using spellchecker

### Removed

## [0.3.1] - 2023-01-18

### Added

### Fixed

### Changed

- ACVM compile method now returns an Error for when a function cannot be reduced to arithmetic gates

- Backtrack changes from noir-lang/noir/587

### Removed

## [0.3.0] - 2022-12-31

### Added

- Added stdlib module to hold all of the standard opcodes
- added `read` , `write` methods for circuit

### Fixed

### Changed

- XOR, Range and AND gates are no longer special case. They are now another opcode in the GadgetCall
- Move fallback module to `stdlib`
- Optimizer code and any other passes will live in acvm. acir is solely for defining the IR now.
- ACIR passes now live under the compiler parent module
- Moved opcode module in acir crate to circuit/opcode
- Rename GadgetCall to BlackBoxFuncCall
- Rename opcode file to blackbox_functions . Similarly OPCODE is now BlackBoxFunc
- Renamed GateResolution::UnsupportedOpcode to GateResolution::UnsupportedBlackBoxFunc
- Renamed GadgetDefinition to FuncDefinition
- Rename GadgetInput to FunctionInput
- Rename Gate -> Opcode . Similarly gate.rs is now opcodes.rs
- Rename CustomGate::supports_gate -> CustomGate::supports_opcode
- Rename GateResolution to OpcodeResolution
- Rename Split directive to ToBits
- Field element printing function was modified to uses ascii superscript numbers and ascii multiplication
- Refactor the way we print ACIR (This is a first draft and will change with more feedback)
- Rename `solve_gadget_call` trait method on ProofSystemCompile to `solve_blackbox_function_call`
- API for `compile` now requires a function pointer which tells us whether a blackbox function is supported
- Renamed Directive::Oddrange to Directive::OddRange
- Renamed FieldElement::to_bytes to FieldElement::to_be_bytes

### Removed

- Selector struct has been removed as it is no longer being used. It is also not being used by Noir.
- CustomGate trait -- There is a method in the ProofSystemCompiler Trait that backends can use to indicate whether
they support a particular black box function
- Remove OpcodeResolution enum from pwg. The happy case is strictly when the witness has been solved

## [0.2.1] - 2022-12-23

- Removed ToBits and ToBytes opcode
