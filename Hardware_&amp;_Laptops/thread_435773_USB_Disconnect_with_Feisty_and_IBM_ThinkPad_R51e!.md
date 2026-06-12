---
title: "USB Disconnect with Feisty and IBM ThinkPad R51e!"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by misho on 2007-05-07
Hi guys,
I have very irritating problem with my IBM ThinkPad R51e UR2DWBM.
I install Ubuntu 7.04 two days ago and everything seems to works fine from the beginning but later on from time to time (from 10 to 30 minutes after boot)  USB Mouse (Logitech) and/or USB drive (or whatever I have plugged into USB ports disconnects and cant be connected again.

I see this: "Workaround for random device disconnections" into Feisty Guide and I do what is described but with no result. In fact my system use ohci_hcd no ehci_hcd as was described there. If I turn that off, cant connect USB device at all.

Please did anyone have idea what to do to fix this ... its really annoying because I use USB devices very often.

P.S.
I haven't found anything useful info (at least for me) in the dmesg or other logs that I look.

---

### Post by leha on 2007-05-07
add noapic to kernel options in /boot/grub/menu.lst

in case you dont know what i am talking about, here is a line from my /boot/grub/menu.lst

> 

kernel  /vmlinuz-2.6.20-15-generic root=UUID=somelongnumber ro quiet splash noapic



PS:
by the way how fast your laptop boots? i have big problems atm with acpi, it takes 30-60s to load some modules

---

### Post by misho on 2007-05-07
Hi,
I just do this (in fact I try both this " noacpi acpi=off " before I see you post) and its about 30-40 minutes without any problems with USB devices (Mouse and Drive) ... I hope this will be it ...

But tell me if you know ... can I work without any problems now when I turn off acpi power management (I still have apmd on, but I cant get any applet to show me battery status or power source mode Batter/AC)? Is there any chance to damage the laptop or so ...?

Thank you very much for you time

---

### Post by leha on 2007-05-08
> **misho said:**
> Hi,
I just do this (in fact I try both this " noacpi acpi=off " before I see you post) and its about 30-40 minutes without any problems with USB devices (Mouse and Drive) ... I hope this will be it ...

But tell me if you know ... can I work without any problems now when I turn off acpi power management (I still have apmd on, but I cant get any applet to show me battery status or power source mode Batter/AC)? Is there any chance to damage the laptop or so ...?

Thank you very much for you time

I am not an expert on hardware but i dont think you can damage your laptop by disabling stuff in linux. Batteries are indeed dangerous they tend to blow up :) but they have electronic circuit on them that controls charging and should prevent explosions (unless you bought it from sony , by the way there was a recall on some batteries from lenovo)

ACPI battery and ibm_acpi modules are screwed up in feisty kernel (it is kernel problem not feisty actually) there is a bug submitted 

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516)

that has some more details. Summary is that you have 3 options
acpi=off   - acpi is completely down
blacklist battery and ibm_acpi  -  battery meter does not work but some acpi is up
ec_intr=0   -  not sure how it works but it works including battery monitor

I got fed up with glitches in feisty and rolled back to edgy, good luck.

---

