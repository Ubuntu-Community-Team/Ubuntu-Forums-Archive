---
title: "About  Hyper-Threading"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by frankabel on 2007-08-29
Hi all,

I install Ubuntu 6.06.1 LTS on my compaq nx9010 and when see the output of the x86info command appear as I my processor have Hyper-Threading but I don't see two processor in top commands or even in the same x86info ouput. How can I get advance of Hyper-Threading? Is posible that the ubuntu installer don't detect the Hyper-Threading in the processor and then not installed a SMP kernel? That can be solved installing a SMP kernel?



Salute
Frank Abel

---

### Post by s3a on 2007-08-29
Try enabling it through the BIOS.

---

### Post by ddrichardson on 2007-08-29
In my experience SMP kernels are needed for dual core support - try the generic SMP kernel in the repositories and see if it makes a difference, you can keep your current one too incase it all goes wrong.

---

### Post by frankabel on 2007-09-03
Thanks for the reply, but my BIOS don't have any option about Hyperthreading and after install the 686 last  kernel of the 6.06.1 Ubuntu(that support SMP, see what uname -a output now "Linux miriam 2.6.15-29-686 #1 SMP PREEMPT Wed Aug 29 13:42:01 UTC 2007 i686 GNU/Linux
") top command keep showing just one CPU after press "1" and the output of "dmesg | grep Hyp" is "[17179573.252000] CPU: Hyper-Threading is disabled"

Even I following others topics (for example [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)) that say that adding the ht=on as kernel parameter at boot time the hyperthreading must get enabled but I get nothing.

What can I do now? Just contemplate the HT flag on my CPU info?

Salute
Frank Abel

---

### Post by ddrichardson on 2007-09-04
I've just had a quick check on that laptop model and it appears to be a Pentium 4 Mobile, not a Pentium 4 Mobile M - only the latter supports hyper threading, see [here]("http://www.intel.com/products/processor/mobilepentium4/index.htm").

It is possible if this works under Windows that there is some kind of proprietry driver involved, which is common with particularly Sempron 3200+.

Can you confirm the processor type?

---

### Post by frankabel on 2007-09-04
Thanks again...look the following.



frankabel@miriam:~$ x86info -v
x86info v1.17.  Dave Jones 2001-2005
Feedback to <davej@redhat.com>.

Found 1 CPU
--------------------------------------------------------------------------
Found unknown cache descriptors: 64 81 91 102 112 123
Family: 15 Model: 2 Stepping: 7 Type: 0 Brand: 9
CPU Model: Pentium 4 (Northwood) [C1] Original OEM
Processor name string: Intel(R) Pentium(R) 4 CPU 2.66GHz

Feature flags:
        Onboard FPU
        Virtual Mode Extensions
        Debugging Extensions
        Page Size Extensions
        Time Stamp Counter
        Model-Specific Registers
        Physical Address Extensions
        Machine Check Architecture
        CMPXCHG8 instruction
        SYSENTER/SYSEXIT
        Memory Type Range Registers
        Page Global Enable
        Machine Check Architecture
        CMOV instruction
        Page Attribute Table
        36-bit PSEs
        CLFLUSH instruction
        Debug Trace Store
        ACPI via MSR
        MMX support
        FXSAVE and FXRESTORE instructions
        SSE support
        SSE2 support
        CPU self snoop
        Hyper-Threading
        Thermal Monitor
        Pending Break Enable
 cntx-id xTPR
Extended feature flags:

Instruction trace cache:
        Size: 12K uOps  8-way associative.
L1 Data cache:
        Size: 8KB       Sectored, 4-way associative.
        line size=64 bytes.
L2 unified cache:
        Size: 512KB     Sectored, 8-way associative.
        line size=64 bytes.
Instruction TLB: 4K, 2MB or 4MB pages, fully associative, 128 entries.
Found unknown cache descriptors: 64 81 91 102 112 123
Data TLB: 4KB or 4MB pages, fully associative, 64 entries.
The physical package supports 1 logical processors

frankabel@miriam:~$

---

### Post by ddrichardson on 2007-09-04
[Here's the problem]("http://en.wikipedia.org/wiki/Pentium_4#Northwood"), although hyper threading was in all the Northwood processors it was disabled in all but the 3.06 GHz chip.

---

### Post by frankabel on 2007-09-04
Thanks

---

