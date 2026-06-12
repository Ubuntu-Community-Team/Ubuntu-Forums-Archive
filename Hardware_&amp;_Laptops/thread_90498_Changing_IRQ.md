---
title: "Changing IRQ"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by GangBoy on 2005-11-15
How can I change the IRQ's for some hardware in ubuntu 5.10 ?? I have problems with pcmcia cardbuss and when i have something plugged in ubuntu freeze. I think if I change the IRQ it will help. I tried to look in bios but there are no irq's for pcmcia.

---

### Post by Teroedni on 2005-11-15
Well you could disable parralell port serial ports and such
You can even disable pci ports. Disable all you dont need and tell if that works

---

### Post by GangBoy on 2005-11-15
I don't think it will work, but I try. I can in bios change or disable infra ( irq 3 or 4) and paralel port (irq 5 or 7), but pcmcia bus have irq 18 and 19.

---

### Post by GangBoy on 2005-11-15
I tried but didn't help :(  Any other ideas??

---

### Post by Teroedni on 2005-11-15
Can you use this cardbuss?
It is also a pcmia to card device?
can you see it in hal or do it frezze before that?
can you see it from console?
Do you got more information about it(Manufactor modelname and such)
so i can look it up and check what the result in linux have been with that card?

---

### Post by GangBoy on 2005-11-16
It's Texas instruments carbuss. But yesterday i plugged in pcmcia card reader and ubuntu didn't freeze. It freezes only with Audigy 2 zs. When starting ubuntu it freezes on hotplug subsystem, exactly enabling device .... 
I tried this card in some other linux distributions, but it wasn't recognized. 
I like ubuntu from the first moment i install it :p , but how can i make card working if ubuntu freeze when i plug in card. :(

---

### Post by GangBoy on 2005-12-09
When booting system it freezes on:
.
.
.
via 82 cxxx: already loaded
[45.499254] via 82xxx: Assuming DXS channels with 48k fixed sample rate
[45.499295] Please try dxs-support=5 option
[45.499328] and report if it works on your machine.
[45.499368] For more details, read ALSA-Configuration.txt
[45.499527] ACPI:PCI Interrupt 0000:00:11.5[C]->GSI 22(level,low)->IRQ22
[45.499590] PCI:via IRQ fixup for 0000:00:11.5 from 11 to 6
[46.086124] PCI:Enabling device 0000:06:00.0(0000->0001)
[46.086170] ACPI:PCI Interrupt 0000:06:00.0[A]->GSI 18(level,low)->IRQ 18

and there it freeze. Have you got any idea how to solve this problem?? I am runnig now on kubuntu breeze amd64, but i tried before ubuntu breeze amd64 and also both 32bit version and the problem was the same. Please help me.

---

### Post by Falados on 2006-01-09
I'm having this exact same problem.  Not sure how it solve it.  However I'm running this on a Dell Inspiron 1150, and the bios options are sub-par.  I can't really fiddle with anything in bios. Maybe kernel options would help?

I'm interested in knowing the solution, if there is one.

Seems to be trouble with IRQ 11 for me?

It is Creative Labs Audigy 2 ZS Notebook: Model SB0530

---

### Post by samk on 2006-03-03
I had th same issue with an Audigy 2 card.
here is what I did to resolve it
[http://www.ubuntuforums.org/showthread.php?t=114363](http://www.ubuntuforums.org/showthread.php?t=114363)

sam

---

### Post by wrtrdood on 2006-03-03
IRQ are hardware assignments.  The only way to change them most of the time is via firmware for the card or jumpers.  Conflicts can cause lockups.  That is, something else in your system is using IRQ 18 when this driver is loaded and it freezes.  It sounds like something might be wrong with the card.  Are you sure it's good?  Might also be driver init sequence.

---

