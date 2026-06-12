---
title: "Ubuntu 11.04 hangs in dual core processor mode"
date: 2011-05-15
forum: Hardware
---

### Post by skud on 2011-05-15
HI all,

    My PC is having a Intel Pentium D processor in an Intel original motherboard (D102GGC2) with ATI Radeon Express 200 series chipset. When i tried to install Ubuntu 11.04 in my PC it hanged on the login screen in the live session. It was the same problem with Ubuntu 10.04 and 10.10. But it was just working fine with all the other previous releases from 8.04. Recently i changed the processor mode to single core using BIOS settings and now i could install Ubuntu onto my PC. The problem is that i can use only one core of my dual core processor. Please help...

---

### Post by johnny.minty on 2011-06-13
Hello,

I have almost exactly the same setup with similar problems using 10.04 - through to 11.04. I will have my setup information up here shortly. I'm going to try single processor mode tonight to test if that works for me.

I will get back to you once i have some results.


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Edit : 13/6/2011 

Enabled "single processor mode" which stopped the stalling in ubuntu version 11.04.


Motherboard : Intel Desktop Board D102GGC2
CPU : Intel Pentium D 2.80 GHZ
GPU : ATI Express 200 series.
Ubuntu Version : 11.04
Kernel : Linux 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux


Messages : 
Ata: lost interuption A(STATUS 0x50)
ata2.00 limiting speed to UDA/66
ata2.00 exception emask 0x0 sact 0x0 serr 0x0
ata2.00 failed command : WRITE DMA

Notes : Sata drive was continually dropped and brought back up resulting in the freezing etc.

---

### Post by rohit6699 on 2011-06-13
Same goes with me.
Processor -> Pentium D 2.66 Dual core.
Motherboard -> DF102GGC2
Graphics -> Onboard 256 MB ATI Raedon 200 series
 
Screen stuck after I log in whe dual processor mode is enabled.
Runs fine in single processor mode.
 
Can anyone please please please help.
 
Regards,
Rohit

---

### Post by pablin88 on 2011-07-12
Same problem here

Inteld102ggc2
Pentium D 2.8ghz

Instead of desabling one core in bios just turned off acpi in grub.

[http://www.thinkdigit.com/forum/open-source/126392-ubuntu-10-04-lts-not-working.html](http://www.thinkdigit.com/forum/open-source/126392-ubuntu-10-04-lts-not-working.html)

Is there any way to get ubuntu running properly on dual core mode? I have been serching for several days without success... :confused:

thanks in advance

---

### Post by psusi on 2011-07-12
Sounds like you have a broken APIC.  Try booting with the "noapic" option.

---

### Post by pablin88 on 2011-07-13
Nice! ubuntu starts with both cores, but keyboard and mouse freezes after a minute or so. Tried with ps2 and usb.

---

### Post by psusi on 2011-07-13
You should check to see if there is an update to your bios, or an option in it to select the MPS compatibility.

---

### Post by skud on 2011-07-21
Dear johnny.minty, could you fix the problem?...

Dear psusi after disabling acpi Ubuntu not at all booting. Also tried with updating the bios. But it also returns no progress. 

If you could install Ubuntu in single core processor mode, enable dual core mode in bios and try to boot using failsafeX in recovery mode. It works. This indicates that the video driver is causing the problem. I googled the problem and I found posts suggesting that it is the problem with KMS and I tried to disable it. But still I couldn't resolve the problem.

---

### Post by armax on 2011-07-23
I got the similar problem with the frozen devices trying to install 11.04 version. 

Sometimes it gets to the screen where i only see the POWER OFF button near some UP and DOWN arrows and sometimes it stucks in the loading screen. 

Just for the records, I found many lines SQUASHFS errors appearing behind the loading screen

My device:

Pentium D 3ghz
894 RAM
D11020M

---

### Post by jtreach on 2012-04-04
I also have this problem. I get to the initial screen upon installation but then when I click 'install' all I get is a blank screen.

---

### Post by jtreach on 2012-04-04
Anyone eventually manage to solve this?

---

### Post by AaronD12 on 2012-06-16
> Anyone eventually manage to solve this?
Guess not. I came here for the same information. I guess we should pat ourselves on the back to even realize that it's a dual-core issue...

---

