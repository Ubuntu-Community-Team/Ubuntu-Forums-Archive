---
title: "Buggy DSDT for ThinkPad L420 (and probably others)"
date: 2011-11-15
forum: Hardware
---

### Post by rootbert on 2011-11-15
Hi everybody,

this is not directly about hardware, but it was the closest match I could find, since it seems to be a common problem on newer ThinkPad laptops:

I recently bought a ThinkPad L420 and  decided to run Ubuntu on it. Unfortunately, it only works (i.e. boots)  when booting with disabled [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface").  Otherwise, the boot process would just not finish. Of course this means  HyperThreading is disabled and other stuff is not working (no suspend,  hibernation, need to press the power button after shutdown etc) which is  pretty annoying. Updating to the latest BIOS version did not change a  thing (BIOS ID: 1.14 (8GET37WW), ECP ID: 1.08 (8GHT26WW)).
So I  decided to do some investigation and I came across the fact that the  DSDT (Differentiated System Description Table) might be buggy. So I  dumped the DSDT using acpidump and acpixtract to find the following  AML-code:

```
OperationRegion (SPRT, SystemIO, 0xB2, One)
```... snip ...

```
OperationRegion (SMI2, SystemIO, 0xB2, One)
```To me as the unsavvy user it seemed like two memory areas were mapped  to the same address which might not be a good idea, especially with the  information that some debugging showed that access to the SMI2 region  was the cause for the boot hang (see last code snippet).
So I  changed the memory address from 0xB2 to 0xB3, recompiled the DSDT (using  iasl) with many errors and warnings, compiled the new DSDT into my  kernel and just like that, the system was booting past the critical  point. Unfortunately, the boot process now hangs at another point (no  idea where that might be). I do not have time to investigate this issue  right now, but I suspect it is related to some other ACPI errors in the  DSDT. This is the last output I get  now when booting and nothing happens thereafter:


```
rtc_cmos rtc_cmos: setting system clock to 2011-11-15 10:13:44 UTC (1321352024)
```Before "fixing" the memory address issue in the DSDT AML code the last line was this one:

```
[0.386486] bio: create slab <bio-0> at 0
```and the corresponding, blocking line in the DSDT was this one (a few  lines below the previously wrong operation region declaration):

```
Store (0xB5, APMC)
```Btw, Windows 7 (not the OEM version but the very original one) is the  only OS that works properly on my system, so I guess they have some  workarounds.
 
Now I am running Ubuntu 11.10 with Kernel 3.1 with disabled ACPI on my ThinkPad L420
- Intel Core i5-2540M Processor (2,6 GHz, 3 MB L3-Cache)
- Mobile Intel HM65 Express Chipset with integrated Intel HD Graphics
- 8 GB PC3-10600 DDR3-SDRAM 1.333 MHz SODIMM
- Bluetooth 3.0
- ThinkPad b/g/n
- 500GB HDD at 7200rpm
 
Has anyone experienced the same problems? Solutions? Hints? Any help appreciated!
Fixing the DSDT in one of the next BIOS updates would be the preferred solution of course ...
 
Cheers

EDIT: I also posted this question [here]("http://forums.lenovo.com/t5/Linux-Discussion/Buggy-DSDT-for-ThinkPad-L420-and-probably-others/td-p/591955")

---

### Post by 2F4U on 2011-11-15
I found these certification notes on the L420

[http://www.ubuntu.com/certification/hardware/201102-7325](http://www.ubuntu.com/certification/hardware/201102-7325)

which basically say it only works with pre-installed Ubuntu 10.10 images and that others may fail to work.

When you say the boot process does not finish, what does that mean? Does it get stuck?

---

### Post by rootbert on 2011-11-15
thanks for the reply. i also found these notes, but 10.10 did not work either, nor did the 32bit version. 
yes, the boot process would just get stuck, no input possible (reisub), no hdd activity, no apparent cpu usage. also the detect hung tasks timeout kernel compile option did not help, nor did any of the other debugging or tracing compile and boot options... any idea how i could trace the module loading order to find the one that causes the boot process to hang?

no pre-installed or lenovo-specific ubuntu images out there...

---

### Post by nzlbob24 on 2011-11-16
Hi

Same problem on my L420 - no boot with 64 bit.

Using 'noapic' it boots fine though. 32bit version also works fine.

With debug on, last line of output before freeze reads:
ACPI: CE: Look up EC in DSDT

I asked on the Lenovo forum but no reply yet - isn't this something Lenovo will have to fix with a BIOS update?

Cheers
Steve

---

### Post by rootbert on 2011-11-16
So 32bit worked for you? Maybe I confused something then and it might also work for me, but only being able to use half of my installed RAM is kind of not what I want for the future though. But my current configuration is not desirable either with no HyperThreading ...

I also posted this in the Lenovo forums and gave them the same hints (if you want to name it that way) for fixing the buggy DSDT file for future BIOS updates, but each update I tried did fix the issues. I guess we need to keep our fingers crossed for future BIOS updates ...

EDIT: true, with debug on this is the last line printed here as well ...

---

### Post by rootbert on 2011-11-24
Firmware update available at [http://support.lenovo.com/en_SE/downloads/detail.page?LegacyDocID=MIGR-77080](http://support.lenovo.com/en_SE/downloads/detail.page?LegacyDocID=MIGR-77080)

Has someone already tried it?

---

### Post by nzlbob24 on 2011-11-27
> **rootbert said:**
> Firmware update available at [http://support.lenovo.com/en_SE/downloads/detail.page?LegacyDocID=MIGR-77080](http://support.lenovo.com/en_SE/downloads/detail.page?LegacyDocID=MIGR-77080)

Has someone already tried it?

Yeah tried it and no change. :/

---

### Post by rootbert on 2011-11-27
Yep, same here, also not working with latest kernel 3.1.2 ...

I also found that fixing the errors reported by iasl in the DSDT (something about Buffers and Packages) made the system boot further instead of changing the address of the OperationRegion, which did not seem to have any effect at all ...

Also, the nosmp boot option does the job for me (like enabling suspend, hibernation, battery monitoring, function keys and such) but boots up only one CPU (instead of 2 + 2 for HT)

---

### Post by rootbert on 2012-06-12
Hey everybody,

just wanted to say that with the newest BIOS (1.17) at least the 64-bit live version of 12.04 booted without any special boot options and showed all of my 8GB of RAM and 4 cores in the system monitor. 

I switched to using 12.04 32-bit a while ago and probably won't switch to 64 unless I really have to, so that's why I only checked the live version of the 64-bit edition. But please feel free to share your experiences of the 64-bit edition on your L420/L520!

Cheers

---

