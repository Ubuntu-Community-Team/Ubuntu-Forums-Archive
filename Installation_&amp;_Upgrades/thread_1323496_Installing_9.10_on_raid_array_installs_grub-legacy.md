---
title: "Installing 9.10 on raid array installs grub-legacy, not grub2"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Ginsu543 on 2009-11-11
[LEFT]I've been trying to install Karmic on my RAID0 array (2 x WD 74 GB Raptors on Intel ICH7R SATA RAID on motherboard), and every time the installer installs grub-legacy, not grub2. Does anyone know a workaround to get grub2 installed? I tried upgrading the grub-legacy to grub2 per this site ([http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/](http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/)), but that didn't work.__ I don't understand why Karmic installs grub-legacy on RAID but grub2 on single drives. Is this normal?

Thank you in advance.
[/LEFT]

---

### Post by huuan on 2009-11-18
This might be some help though not exactly the same, see comments #14,#15,#16 here:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340)

---

### Post by Ginsu543 on 2009-11-18
Thanks for the post. I'd pretty much come to the same conclusion as the last poster on that thread and just decided to stick with grub-legacy. Now I am able to triple-boot Karmic off my RAID array, Jaunty off one of my WD Caviar Blacks, and Win XP Pro off the other WD Caviar Black. It's just that when I posted this, I thought something was wrong because grub 2 was supposed to be the default bootloader for Karmic.

---

### Post by amp88 on 2009-11-18
It appears as though I'm suffering from the same issue ([in my thread here](http://ubuntuforums.org/showthread.php?t=1330540)). Could you please tell me how you fixed your issue? "Decided to stick with grub-legacy"...how do you do that during installation? Thanks for any help.

---

### Post by Ginsu543 on 2009-11-19
I read through your original thread and it seems to me that you want to set up your system slightly differently than what I've got. I have all my OSes on different drives (Karmic on the RAID array, Jaunty on one 1 TB drive, Windows on the other 1 TB drive) and I have set the boot order in BIOS to start up the RAID array first. This ensures that grub comes up first, which I have set up to chainload the other two. I prefer this setup because I don't have to worry about grub erasing NTLDR and vice versa. Each drive's MBR remains intact and I just choose which to boot first in BIOS.

You, however, want to have both Karmic and Windows on two partitions on the same RAID array. To make this work (as I understand it), you would install Windows in the first partition and put Karmic in the second (Windows likes to be first). If you want Windows to have 110 GB, then you would have to reformat the RAID array so that the first partition is 110 GB and the second partition is 30 GB. Then, when you install Karmic in the second partition, you would install grub in (hd0) and have it chainload Windows.

As far as sticking with grub-legacy is concerned, I just found that once I installed Karmic onto my RAID array, it had grub-legacy, not grub2, as its bootloader. Initially, I thought something was wrong because when I installed Karmic on a single drive, it (as it should) installed grub2 by default. But on my RAID array, I had grub-legacy by default. I tried upgrading my grub-legacy to grub 2 after the fact, but found that this didn't work. So I decided to just stick with grub-legacy.

---

### Post by amp88 on 2009-11-19
Ok, thanks for the reply. For the moment I've just installed 9.1 on a portion of the 1TB drive again, leaving the RAID alone.

---

### Post by Ginsu543 on 2009-11-19
Are you using grub-legacy or grub2?

---

