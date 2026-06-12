---
title: "Memory barriers on 86x running 32-bit OSs"
date: 2010-09-19
forum: Hardware
---

### Post by puppi on 2010-09-19
I'm assuming a 32 bits x86 processor (specifically, of IA-32 architecture).
Due to the 32 bit size of the GPR (General Purpose Registers), clearly a maximum of 4GB is allocated for any running program (for simplicity sake, I'm including memory reserved for kernel activity as "program memory"). In protected mode, any program effectively addresses memory in flat model. Nevertheless, the Segment Registers exist and are 32-bits wide, and thus theoretically could account for a 16x4GB=64GB of total addressable memory (in segment:offset fashion), but I don't know in details how those registers are handled in protected mode. So my question is: in protected mode, even tough a single program can only address a maximum of 4GB of memory, can the whole of running programs, each accessing a segment of at most 4GB, be allocated in a range of 64GB? Or, equivalently, can (or does) a 32-bit OS see and make use of up to 64GB of RAM for programs running in parallel? Or, for some reason, the Segment Registers are fixed and all running programs are necessarily concatenated in a single 4GB segment?

---

### Post by puppi on 2010-09-19
As a particular case of my question: If I have 4GB of RAM, setting a swap partition under 32-bit Ubuntu will be of any worth?

---

