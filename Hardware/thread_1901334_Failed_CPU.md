---
title: "Failed CPU"
date: 2011-12-28
forum: Hardware
---

### Post by bravo sierra echo on 2011-12-28
Well, this is a bit of a weird one.  My machine used to have twin CPUs, and now it only appears to have one.  It's still working fine and in normal desktop use I haven't noticed the difference - I haven't played any games yet though.

Relevant bits from dmidecode:

System Information
        Manufacturer: FUJITSU SIEMENS
        Product Name: GA-8I915PM
        Version:  
        Serial Number:  
        UUID: 30303134-3835-3630-3146-3744FFFFFFFF
        Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
        Manufacturer: GIGA-BYTE Technology
        Product Name: GA-8I915PM
        Version:  
        Serial Number:  

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
        Manufacturer: FUJITSU SIEMENS
        Type: Desktop
        Lock: Not Present
        Version:  
        Serial Number:  
        Asset Tag:  
        Boot-up State: Unknown
        Power Supply State: Unknown
        Thermal State: Unknown
        Security Status: Unknown
        OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
        Socket Designation: Socket 775
        Type: Central Processor
        Family: Pentium 4
        Manufacturer: Intel
        ID: 43 0F 00 00 FF FB EB BF
        Signature: Type 0, Family 15, Model 4, Stepping 3
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (Fast floating-point save and restore)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Hyper-threading technology)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Pentium(R) 4 CPU
        Voltage: 1.4 V
        External Clock: 200 MHz
        Max Speed: 4000 MHz
        Current Speed: 3000 MHz
        Status: Populated, Enabled
        Upgrade: Socket 478
        L1 Cache Handle: 0x000A
        L2 Cache Handle: 0x000B
        L3 Cache Handle: Not Provided
        Serial Number:  
        Asset Tag:  
        Part Number:  

My questions are:  Is there anything software-related I can do to try and resurrect the dead CPU?  Maybe something in the BIOS settings that I can tweak?

And should I be worried that my whole motherboard is about to fail?  Do I replace it now, or just leave it alone if I'm still satisfied with the performance?

Thanks in advance for any advice.

---

### Post by Mark Phelps on 2011-12-28
Your CPU isn't dead, otherwise, your PC would not boot.  Would check in your BIOS and confirm that Hyperthreading is Enabled.

Not aware of any software that will force multi-core CPUs to operate all of the cores.  As far as I know, that is done by default.

---

### Post by bravo sierra echo on 2011-12-28
Thanks for the answer.  I was also very surprised that the computer boots at all!

BIOS settings checked, and hyper-threading is on.  I hadn't changed anything in the BIOS recently, anyway.

Could it be that it's working fine but just not reporting its existence?  I haven't noticed a drop in performance but that's purely subjective, I don't have any "before" data to compare.

---

