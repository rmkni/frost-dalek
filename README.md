# FROST [![](https://img.shields.io/crates/v/frost-dalek.svg)](https://crates.io/crates/frost-dalek) [![](https://docs.rs/frost-dalek/badge.svg)](https://docs.rs/frost-dalek) [![](https://travis-ci.com/github/isislovecruft/frost-dalek.svg?branch=master)](https://travis-ci.org/isislovecruft/frost-dalek)

## About

### What are Threshold Signature Schemes

Threshold signature schemes are cryptographic protocols that enable a group of participants to collectively share ownership of a private key. In such schemes, a predefined threshold determines the minimum number of participants who must work together in order to perform operations such as signing a piece of data. This approach enhances both security and distributed authority.

### What is Schnorr Signature

Schnorr signatures are a type of digital signature scheme that relies on the mathematical principles of discrete logarithms. They offer security features such as resistance to forgery and support for efficient signature verification. Additionally, Schnorr signatures can be utilized in zero-knowledge protocols, allowing one party to prove knowledge of a secret without revealing the secret itself.

### What is FROST

FROST, or Flexible Round-Optimized Schnorr Threshold Signatures, is a cryptographic protocol that aims to improve the efficiency of **threshold signatures** using **Schnorr signatures**. A common challenge with traditional threshold signature schemes is the need for participants to exchange data and perform operations over multiple rounds in a pre-defined order. FROST addresses this limitation by separating the distributed key generation phase from the signature phase, enabling signature creation to occur in a single network round. This optimization reduces latency and enhances overall performance.

See the [paper](https://eprint.iacr.org/2020/852) by **Chelsea Komlo** and **Ian Goldberg**.

### What is FROST-Dalek

FROST-Dalek is a Rust implementation of the FROST protocol, utilizing the [Dalek](https://github.com/dalek-cryptography/curve25519-dalek) library for elliptic curve cryptography. This project provides a secure and efficient implementation of FROST, enabling developers to leverage the benefits of threshold signatures in their applications.

## Features

### Phase 1: Key Pair Generation

- Generate key pairs for participants within a specified group.
- Generate a corresponding key pair for the group itself.

*Note: Phase 1 must be completed before proceeding to Phase 2.*

### Phase 2: Signature Management

- Initiate a signature round using the previously generated key pairs.
- Allow participants to securely sign messages during the signature round.
  - No order is required for signing messages.
- Close the signature round and verify the final signature.

*Note: Once Phase 1 is complete, Phase 2 can be executed an arbitrary number of times.*


### Limitations

*   The subset of participants required to meet the threshold must be predetermined before the signature round commences.
*   Participant secrets are only valid within a specific group, so users must maintain different identities for each group.
*   The current implementation lacks a dynamic data structure to manage an arbitrary number of participants.
*   There is no functionality for serializing data, saving state, or transmitting data over a network.

## Installation

To include the `frost-dalek` crate in your Rust project, ensure you have Cargo (Rust package manager) installed. If not, you can install it by following the instructions on the [official Rust website](https://www.rust-lang.org/tools/install).

Add the `frost-dalek` crate to your project by running the following command in your project directory:
```bash
cargo add frost-dalek
```

## Usage

Refer to the [documentation](https://docs.rs/frost-dalek) for usage examples.

## Contributing

This project is not actively maintained.

The repository owner may not be available to review, engage in discussions, or accept pull requests.

Please note that there is no formatting configuration in place; thus, cosmetic changes will not be accepted as they are not considered significant and may disrupt PR or forks reviews.

If you wish to propose enhancements, consider forking the repository.

## Forks

- [no-std feature](https://github.com/isislovecruft/frost-dalek/compare/main...imsk17:frost-dalek:no-std)
- [adjustments for keys distribution](https://github.com/isislovecruft/frost-dalek/compare/main...takimata:frost-dalek:main)

## Disclaimer

This project is in the research and development phase. The code may be unstable and is not recommended for production use.
