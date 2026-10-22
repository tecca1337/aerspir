# aerspir

An experimental, open-source compatibility layer and high-level runtime designed to run 64-bit iOS applications (`.ipa`) natively on desktop operating systems (Windows & Linux) without requiring a full virtual machine or Apple operating system.

---

## Overview

Unlike traditional virtualization, which runs an entire guest operating system with heavy overhead, **aerspir** acts as a user-space runtime environment. It intercepts iOS system calls and framework interactions, translating them directly to native desktop APIs on the fly—similar to how Wine translates Windows applications for POSIX systems.

The primary goal of this project is digital software preservation: breathing new life into classic, discontinued, and delisted iOS applications and games that are no longer accessible on modern mobile hardware.

---

## How It Works

1. **Package & Binary Ingestion**  
   Parses application bundles (`.ipa`), extracting the core Mach-O executable, dynamic libraries, and assets into a sandboxed environment.

2. **CPU Architecture Execution**  
   Executes ARM64 application code on host `x86_64` hardware via dynamic CPU instruction translation and execution layers.

3. **High-Level Emulation (HLE) & ABI Bridging**  
   Reimplements essential Darwin user-space subsystems, the Objective-C/Swift runtime dispatchers, and foundational frameworks (`Foundation`, `UIKit`, `CoreFoundation`).

4. **Graphics & Audio Pipeline**  
   Bridges mobile graphics rendering contexts (OpenGL ES / Metal) directly into modern desktop graphics APIs (Vulkan / Desktop OpenGL), mapping mobile framebuffers to desktop application windows. Positional audio calls are mapped to host audio sub-systems.

5. **Input & Interaction Mapping**  
   Translates desktop mouse clicks, dragging, and keyboard input into native iOS multi-touch events, swipe gestures, and screen orientation notifications.

---

## Project Status

> **Note:** This project is currently in early prototype/R&D stage. Features are being implemented iteratively using a conformance-driven approach.

---

## License

This project is licensed under the terms of the **GNU General Public License v2.0 or later** ([GPL-2.0-or-later](LICENSE)).

> This program is free software; you can redistribute it and/or modify
> it under the terms of the GNU General Public License as published by
> the Free Software Foundation; either version 2 of the License, or
> (at your option) any later version.
> 
> This program is distributed in the hope that it will be useful,
> but WITHOUT ANY WARRANTY; without even the implied warranty of
> MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
> GNU General Public License for more details.
