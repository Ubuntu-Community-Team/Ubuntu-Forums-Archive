---
title: "External monitor not working after install"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by sagyvolkov on 2006-11-08
Hi,

I'm installing 6.10 from the DVD.
Working on Dell D620 with a docking station connected via DVI to a DELL 2001FP LCD display.
The laptop has nVidia Quadro NVS 110M graphic card (256MB).
Initially when i used the CD, i kept getting a blank screen on my external monitor though i heard the laptop was running and the Ubuntu startup sound was heard. 
I then change (I think its F6 on the DVD menu) the resolution of my external monitor from VGA to the largest resolution possible on that menu which i think is 1024*1280 32. 
that got the LiveCD to run properly and the install went fine.
Once the install is done and i remove the DVD, i can hear Ubuntu boots (the start sound), but nothing on my external monitor.
If i open at that point the laptop monitor lid (The laptop is connected to a docking station so the lid was close all that time), i can see Ubuntu running just fine, but i still can't see anything on my external monitor.

so to sum this weird behavior, the external monitor works from the LiveCD, but not from the install files themselves, but Ubuntu is installed properly and running fine from the laptop screen.

Any help will be appreciated.

---

### Post by sagyvolkov on 2006-11-08
Just an update,
I've manage to get the external monitor to work but in a very weird  way.
I have to boot the laptop while the lid is open and then once i see the grub menu i hit Fn+F8 which in my laptop change the screen output to either Laptop LCD, External LCD or both, so i change so the grub menu will show up on the external LCD and then continue to load and i see the picture working fine on my external monitor.

I wonder if someone encountered a problem like this in the past and if there is some kind of fix for it.

Thanks.

---

### Post by gleenn on 2006-12-22
I don't know if our problems are related but my external monitor never works. It seems the Fn+F8 has no effect ever, even during Grub and gdm and in X. I have a dell inspiron 6000 with the intel 915 chipset and it just has been giving me great trouble.

Hope you found your answer.

I even tried this:

[https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915]("https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915")

---

