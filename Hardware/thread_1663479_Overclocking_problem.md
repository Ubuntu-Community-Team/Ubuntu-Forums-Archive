---
title: "Overclocking problem"
date: 2011-01-09
forum: Hardware
---

### Post by Thomas Kenobi on 2011-01-09
I am a experiencing some problems with overclocking my CPU.
My rig is:
Core i5 750@2.66GHz
Asus P7P55D

After some testing to determine a stable configuration and a 9hr Prime95 session in Windows I attempted to boot into Ubuntu to do some work before continuing Prime95 testing only to be confronted by a number of error messages after the GRUB2 menu.
This is the configuration I had at the time:
[http://valid.canardpc.com/show_oc.php?id=1584814](http://valid.canardpc.com/show_oc.php?id=1584814)

This is an assortment of some of the error messages I had the time to write down before the system rebooted:
```

No human readable MCE
Kernel panic - not syncing

Bad page map in process init
Bad page state in process init
vma -> vm_ops -> fault: filemap_fault +0x0/0x450

Fixing recursive fault but reboot is needed

various access errors

```I can boot using the configuration BCLK:191MHz, Vcore: 1.392V using Win7 (64bit), Ubuntu 9.04 (64bit, boot from cd) and Ubuntu 10.04 (32bit, boot from cd), but not using my 10.10 (64bit) installation on the SSD.
In order to boot using the installed 10.10 I have to bring BCLK down to 166MHz (next number tested 171MHz, system didn't boot) which is rather low. I can go higher than that without even giving it more than the default Vcore current. Yet Ubuntu will not boot with anything higher.

Any help would be welcome.

---

### Post by Thomas Kenobi on 2011-01-10
I've done some more digging and it looks like the problem is connected to the kernel. I can boot using 2.6.32-25, but not using 2.6.35-(24 or 23 or 22).

In addition I run memtest86 and it looks like my RAM is doing just fine.


Any ideas would be more than welcome. I really don't know what else to try here. Every test I'm running tells me I have a stable overclock and yet Ubuntu will not boot with the latest kernel.

---

### Post by The Fiddler on 2011-01-10
[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

> Some of the main hardware problems that cause MCEs include:
[LIST]
[*]System bus errors (error communicating between the processor and the motherboard).
[*]Memory errors that may include parity / Error correction code (ECC) problems. Error checking ensures that data is stored correctly in the RAM; if information is corrupted, then random errors occur.
[*]Cache errors in the processor; the cache stores important data and code. If this is corrupted, errors often occur.
[/LIST]

Note that you need to use Orthos or four instances of Prime95 compiled for amd64 for a valid stability test. Even that won't guarantee absolute stability, especially in +50% overclocks.

What you could do:
1. try upping your motherboard voltage by 0.1V and see if that helps.
2. try installing a newer kernel (2.36 or 2.37)

Kernel developers will generally not investigate issues on hardware running out of specs.

---

### Post by Yellow Pasque on 2011-01-10
EDIT: Nevermind

---

### Post by The Fiddler on 2011-01-10
(Fake edit)

3. try disabling CPU power management in your BIOS (typically called "EIST" and "C1E" on Intel).
4. check if any BIOS updates are available for your motherboard (reset to stock clocks first!)
5. a few people suggest that disabling USB3 may help. Sounds far fetched but still worth trying out.

---

### Post by Thomas Kenobi on 2011-01-10
Ok so the problem has been fixed but certainly not in the way I had expected. To elaborate:

I did some more testing and found out that disabling SpeedStep (C1E was already off) allowed Linux to boot at the higher BCLK settings. I then flashed the latest BIOS (Plenty of BIOS updates last year. ASUS has been busy) and found out that I no longer have the choice of activating SpeedStep and TurboMode after a certain BCLK. Apparently the latest BIOS and Linux agree that this should be off when overclocking. I did some digging and it seems that people experience random BSODs if they leave this on when OCing.

I'm now testing a 181x21 MHz, 1.32V configuration to see if it's stable and if it works I think I'll make it permanent as I get much more reasonable temps with it than I do with 191x21 MHz, 1.392V.


Thanks for the help mate!

PS: You no longer need to run more than one instance of Prime95 now. It automatically spawns one worker for each core you have.

---

### Post by Thomas Kenobi on 2011-01-14
I looks like I rushed to declare success. I could run Ubuntu with BCLK: 181, multiplier: x20, but when I switched to x21 the problem returned.
I tried compiling kernel 2.6.37 but I'm still having the same issue.
This is the Machine Code Exception log:
```

HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 0
CPU 0 BANK 5 
MISC 1 ADDR 3f1c855701c6 
TIME 1295007898 Fri Jan 14 14:24:58 2011
MCG status:
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
MCA: Internal Timer error
STATUS be00000000800400 MCGSTATUS 0
MCGCAP 1c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 30

```I want to emphasise again that I've run Prime95 for 24hrs under Win7 and I've had no stability or excessive temperature problems.

Any help would be most welcome.

---

