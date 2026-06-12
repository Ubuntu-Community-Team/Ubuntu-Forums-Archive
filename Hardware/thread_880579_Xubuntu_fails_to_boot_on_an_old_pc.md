---
title: "Xubuntu fails to boot on an old pc"
date: 2008-08-05
forum: Hardware
---

### Post by bramfeld on 2008-08-05
I don't even know where to start this topic... The problem is quite funny. I han an old pc and I just clean installed Xubuntu 8.04.1 on it. And it won't boot. It just gets stuck in one point without any error. Even in safe mode it does'n show anything interesting. The funny thing is that live worked just fine. I could use it normally but when installed it just won't boot.

The computer is like: abit BE6-II, Pentium III 600E, about 256 mb ram, 20 GB hdd and some ATI radeon graphics card with 64 mb memory. It also has a some cd-rw driwe I took from a newer fujitsu-siemens pc, but I tried disconnecting it and it doesn't help. Also the computer does'n have soundcard and an ethernet card.

Any ideas?

---

### Post by overdrank on 2008-08-05
> **bramfeld said:**
> I don't even know where to start this topic... The problem is quite funny. I han an old pc and I just clean installed Xubuntu 8.04.1 on it. And it won't boot. It just gets stuck in one point without any error. Even in safe mode it does'n show anything interesting. The funny thing is that live worked just fine. I could use it normally but when installed it just won't boot.

The computer is like: abit BE6-II, Pentium III 600E, about 256 mb ram, 20 GB hdd and some ATI radeon graphics card with 64 mb memory. It also has a some cd-rw driwe I took from a newer fujitsu-siemens pc, but I tried disconnecting it and it doesn't help. Also the computer does'n have soundcard and an ethernet card.

Any ideas?

Hi and welcome, so you just end up with a blank screen. Have you tried to reach the command prompt with ctrl, alt, F1 keys?

---

### Post by bramfeld on 2008-08-05
Not a blank screen. Sorry. GRUB loads normally and I can also access it and select recovery mode etc. But if I start it normally it loads the screen with ubuntu text and progress bar and then gets stuck. If I select recovery mode, the last line is sda: driver 'sr' needs updating and so on. And then nothing happends.

---

### Post by overdrank on 2008-08-05
> **bramfeld said:**
> Not a blank screen. Sorry. GRUB loads normally and I can also access it and select recovery mode etc. But if I start it normally it loads the screen with ubuntu text and progress bar and then gets stuck. If I select recovery mode, the last line is sda: driver 'sr' needs updating and so on. And then nothing happends.

You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add noapic and then hit enter and then  b to boot. Hope this helps. Good luck!

---

### Post by snowpine on 2008-08-05
> **overdrank said:**
> You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add noapic and then hit enter and then  b to boot. Hope this helps. Good luck!

+1 this is great advice... by removing the splash screen, you can see exactly where the hang-up is occurring. Copy whatever message is on screen when things stall, and post it back here. 

There are a number of parameters you can set on the kernel line to get around various problems; on my old Dell laptop, for example, adding 'all_generic_ide' speeds things up.

---

### Post by bramfeld on 2008-08-05
Adding noapic didn't help anything and with no "quiet splash" I saw again "sda: driver 'sr' needs updating...".

'all_generic_ide' didn't help also but now it stopped at just showing "sda:" in the last line.

Where can I find those parameters? And anyway I don't know what's wrong so it's hard to know what to fix... I can put here a picture of what I see when it gets stuck.

---

### Post by overdrank on 2008-08-05
> **bramfeld said:**
> Adding noapic didn't help anything and with no "quiet splash" I saw again "sda: driver 'sr' needs updating...".

'all_generic_ide' didn't help also but now it stopped at just showing "sda:" in the last line.

Where can I find those parameters? And anyway I don't know what's wrong so it's hard to know what to fix... I can put here a picture of what I see when it gets stuck.

Ok last idea, clear the motherboard cmos. This will set it back to the default settings. Then you may want to try and fsck on the hard drive using the live cd. 
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by bramfeld on 2008-08-05
I cleared cmos after I upgraded the BIOS and xubuntu doesn't work before or after it. Xubuntu doesn't seem to like this HDD. It's an IBM Deskstar if someone wants to know. I attached a picture of what I got from fdisk and fsck. Sorry about the quality.

---

### Post by bramfeld on 2008-08-05
Thank you for help. The problem was that I connected the HDD to third IDE channel (I don't actually understand how there are four of them). Now I tried connecting to the first and it worked fine. Well don't ask me. The motherboard manual is in german and I don't understand anything of it...

---

