---
title: "Single Boot-XP &amp; Ubuntu 9.04"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by kenanton on 2009-08-06
I have a desktop system that I built running XP. I would like to add a drive and install Ubuntu 9.04 on it but I do not want it to be dual boot. What I want to do with Ubuntu 9.04 is use Wine to try to run some old Windows software and try to run some old hardware that does not have XP drivers. If the programs didn't work I would simply remove the Ubuntu 9.04 drive. I would boot into either XP or Ubuntu 9.04 by selecting the boot drive in the bios. Is this possible? If so, what is the best way to do the install?

By the way, I am quite familiar with the dual boot process as I am typing this on a Toshiba laptop that boots either into Vista Ubuntu 9.04 but lacks the ports needed to connect my old hardware.

Thanks.

---

### Post by Sef on 2009-08-06
Do you mean that you have two hard drives: one with XP on it and the other with Ubuntu?

---

### Post by kenanton on 2009-08-06
Well I will have if someone tells me this plan will work well.

---

### Post by oldfred on 2009-08-06
You can unplug windows drive and install Ubuntu to a new drive and it will not set up dual boot. But, you will have to go into your BIOS every time you boot to select which drive or mechanically plug in the drive you want. 
Why not set up dual boot with Windows selected first and only a 3 second timeout, and hidden menu so that you so not "see" the dual boot unless you press escape within the 3 seconds.

---

### Post by stlsaint on 2009-08-06
agreed!!

---

### Post by kenanton on 2009-08-06
Oldfred, so I actually have to unplug the windows drives and then install Ubuntu to a new drive and it will not set up dual boot? I can't simply disable the XP drives in the bios to avoid setting up the dual boot?

I do not mind having to go into the BIOS every time I boot to select which drive or mechanically plug in the drive I want.

I do not want to set up a dual boot with Windows selected first and only a 3 second timeout as this is an experiment. More than a year ago I had dual boot setup on this machine and had a very difficult time removing Ubuntu.  If under Ubuntu and Wine I can run the old Windows hardware and software I will set up a dual boot system.

I have a Toshiba laptop that boots either into Vista or Ubuntu 9.04 but lacks the ports needed to connect my old hardware.

By the way, why can't I find this thread when I search under my name?

Thanks again.

---

### Post by oldfred on 2009-08-06
I have never tried disabling a drive in the BIOS, it probably would work. During the install it should not see the windows drive. If the install shows both drives then you know you have to unplug it.
Reinstalling Windows or Grub is not a huge problem, many questions on this forum and others have how to solve boot issues, and updating/fixing the MBR.
If you decide to go dual boot later it would not be difficult to add the 4 or five lines it would take to have Windows boot in the grub menu.

---

