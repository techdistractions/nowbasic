# NowBasic — New Old Windows BASIC

NowBasic is an experimental, open-source BASIC programming language, native-code compiler and integrated development environment (IDE) for early versions of Microsoft Windows, including Windows 1.01.

The language supports native Windows controls, graphics, audio, communications and lightweight networking, allowing developers to create graphical applications without working directly with low-level Windows APIs. Programs compile into compact, standalone machine-code executables without requiring a separate BASIC runtime.

Designed with original hardware in mind, NowBasic supports the complete development cycle on an 8088-based PC with 640 KB RAM and CGA graphics. Developers can build the 16-bit compiler (NOWN16) from source, write and visually design applications using TIDE, compile NowBasic source (.NBS) files and run the resulting executables on the same machine.

Compiled applications can run on systems with even less memory, depending on their requirements. NowBasic's modular design also provides a foundation for future expansion to other retro computing platforms.

## Project Components & Distribution

The NowBasic source tree is organised into five primary components, covering the language specification, native compilers and integrated development environments.

All components are experimental and under active development, with varying levels of maturity.

### NowBasic Language (LANGREF)

The controlled language reference defines the syntax, structure, semantics and expected behaviour of the NowBasic programming language.

It serves as the authoritative specification for all compiler implementations and supported platforms, ensuring consistent language behaviour as the project evolves.

The language is designed to remain largely platform-independent, allowing its underlying concepts and syntax to be reused across different operating systems and hardware architectures.

### Win16 Compiler (NOWN16)

NOWN16 is the original NowBasic compiler, designed to operate under real-mode 16-bit Windows, including Windows 1.01.

It accepts plain-text NowBasic source files (`.NBS`), processing them through a series of front-end parsing, semantic analysis, lowering and native code-generation stages.

The resulting output is a 16-bit Windows New Executable (NE), containing native 8086-compatible machine code and selectively included supporting routines.

Unlike traditional interpreted BASIC environments, compiled applications execute directly without requiring a separate language interpreter or BASIC runtime installation.

The compiler is designed to operate on modest hardware, including 8088-based PCs with 640 KB of RAM, while generating applications suitable for even more memory-constrained systems.

### Win16 IDE (TIDE)

TIDE (EDIT backwards) is a lightweight integrated development environment written in assembly language, designed specifically for early Windows systems and limited hardware configurations.

It provides source-code editing and visual form design, allowing developers to create Windows applications directly on machines such as the original IBM PC/XT.

The interface is deliberately compact, prioritising responsiveness, low memory consumption and practical usability over elaborate development tools.

Despite its modest hardware requirements, TIDE provides access to the same NowBasic language and compiler capabilities available in the larger development environments.

### Win32 Compiler (NOWN32)

NOWN32 is the 32-bit compiler variant, designed to operate under Windows 3.1 with Win32s 1.1 on 386-class hardware or later.

Derived from the authoritative NOWN16 compiler source, NOWN32 shares the underlying language implementation while adapting the compiler to the 32-bit Windows environment.

The compiler has two required native executable output branches:

- **16-bit Windows New Executable (NE):** Produces native executables for the supported 16-bit Windows environments.
- **32-bit Windows Portable Executable (PE):** Produces native 32-bit executables for compatible Windows environments.

Both output branches are integral parts of the project and remain under active development, with PE generation currently at an earlier stage of maturity than NE.

The shared-source approach is intended to maintain language consistency, minimise duplicated compiler logic and allow improvements to benefit both compiler variants.

### Win32 IDE (SIDE)

SIDE is the 32-bit Standard Integrated Development Environment, building upon the principles of TIDE while taking advantage of the additional processing power, memory and graphical capabilities available on newer systems.

It provides a more conventional and feature-rich development environment, with enhanced source editing, visual form design and project management facilities.

SIDE targets Windows 3.1 with Win32s 1.1, requiring a 386-class processor or later.

While TIDE prioritises operation on the earliest supported hardware, SIDE aims to provide a more convenient development experience without changing the underlying language or limiting compatibility with older target systems.

### Additional Development Tools & Experimental Platforms

The primary NowBasic source tree focuses on the Windows compilers, IDEs and controlled language specification.

Experimental platform work, including Atari ST, Macintosh 128K, Commodore 64 GEOS and MS-DOS GEM/3, is maintained separately. These experiments explore the portability of the language and alternative implementations suited to different hardware and operating systems.

Supporting utilities such as AUTOUAT and NOWBAT, together with various auditing, testing and development tools, are also maintained outside the core distribution.

These tools assist with compiler development, automated testing, regression analysis and compatibility validation but are not required by end users of compiled NowBasic applications.

## Compiling Components

NowBasic uses two build toolchains:

1. **MS-DOS (16-bit):** Uses JWASMR to assemble source code and NBLINKNE to link native 16-bit Windows New Executable (NE) files, compatible with early real-mode Windows.

2. **32-bit Windows:** Uses JWASM to assemble source code and NBJWLINK to link both 16-bit Windows NE and 32-bit Portable Executable (PE) files.

NBLINKNE is a purpose-built NowBasic linker, while NBJWLINK is derived from Open Watcom's JWLINK and retains the Sybase Open Watcom Public License.

## Licensing

NowBasic is a free, open-source project with component-specific licensing.

| Component | License |
| --- | --- |
| **LANGREF** (Language Specification) | CC BY-ND 4.0 |
| **NBJWLINK** (Windows Linker) | Sybase Open Watcom Public License 1.0 |
| **All other NowBasic components** | CC0 1.0 Universal (Public Domain) |

### Language Specification (LANGREF)

The authoritative NowBasic language specification is distributed under [Creative Commons Attribution-NoDerivatives 4.0](https://creativecommons.org/licenses/by-nd/4.0/), with the copyright holder expressly waiving the requirement for personal author attribution. The specification remains controlled, while independent implementations of the language are permitted.

### Windows Linker (NBJWLINK)

Derived from JWLINK and distributed under the [Sybase Open Watcom Public License 1.0](https://opensource.org/license/Watcom-1.0), retaining applicable copyright and license notices.

### Other Components

All other original NowBasic components, including NOWN16, NOWN32, TIDE, SIDE, NBLINKNE and project utilities, are dedicated to the public domain under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).

Third-party dependencies retain their respective licenses.

## Development Notes & Background

NowBasic began in 2026 as an experiment in bringing BASIC programming to the earliest versions of Microsoft Windows. The project has since evolved through several compiler architectures, from interpreted and P-code implementations to native 8086 machine-code generation, with an emphasis on efficiency, low memory consumption and original hardware compatibility.

**Artificial intelligence has played a significant role in the project's development.** ChatGPT, OpenAI Codex and Qwen Coder have contributed extensively to compiler implementations, development utilities, testing infrastructure, documentation and debugging.

AI has enabled rapid experimentation with compiler architectures, ports to other retro platforms and solutions to complex compatibility challenges. Development remains human-directed, with the language specification, requirements and technical priorities established by the project maintainer.

The development process has evolved alongside the software, incorporating version control, reproducible builds, automated regression testing and compatibility audits. Failures and architectural revisions have helped establish a disciplined approach to AI-assisted software engineering.

NowBasic makes no claim to being entirely hand-written or free from defects. It remains an experimental project exploring both programming for classic computers and the capabilities of modern AI-assisted development tools.
