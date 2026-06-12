---
title: "Running Ubuntu on Lenovo Yoga 920 2-in-1"
date: 2018-01-16
forum: Hardware
---

### Post by chadjohnson on 2018-01-16
Hi! I'd just like to report that I was able to successfully install Ubuntu on a Lenovo 920 2-in-1. I also completely removed Windows and all existing partitions from the machine. It is **not necessary** to have Windows on the machine in order to boot Linux; no remnants of Windows exist any longer on my machine.

First, I made a clone of the entire harddrive and backed it up on another machine: [FONT=Courier New]dd if=/dev/nvme0n1 bs=8M | gzip -9 -c | ssh chad@192.168.0.2 'dd of=/Users/chad/lenovo-yoga-920-restore.dd.gz'[/FONT]

Once done, I downloaded Ubuntu 17.10 (the Yoga 920 is not affected by the BIOS corruption bug) and created a bootable USB drive from my MacBook following [these instructions]("https://apple.stackexchange.com/a/179785"). Next, I entered the BIOS by pressing fn+F2 immediately after pressing the power button and changed the boot order so that the USB was first in the boot order. Then I was able to boot Ubuntu.

To enable wifi I had to unload the ideapad_laptop module: [FONT=Courier New]modprobe -r ideapad_laptop[/FONT]

I then ran GParted, deleted all partitions, and followed step 2 [here]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_System_Partition") to create a 200MB FAT32 partition with the "boot" flag on (I did not have to set the /boot/efi mount point in GParted). I then applied the changes.

After this, I ran the Ubuntu installer and selected the option to manually define partitions. I first selected the partition I just created and set it to type EFI System Partition. Then I created partitions as I normally would (100GB for /, 400GB for /home, and 8GB for swap).

The installer finished, removed the USB drive, rebooted, and was able to boot into Ubuntu with no problems.

Everything is working fine so far except for the fingerprint reader and screen rotation. Be sure to blacklist the ideapad_laptop module for wifi to continue working: [FONT=Courier New]sudo echo ideapad_laptop >> /etc/modprobe.d/blacklist.conf[/FONT]

---

### Post by yeckel on 2018-01-28
In the case you would like to control battery saving feature accessible just in windows (it's charging the battery just to ~59%) you can check [https://github.com/yeckel/yoga920/](https://github.com/yeckel/yoga920/) I'm still struggling with F1..F12 keys. How are you toggling them?

---

### Post by chadjohnson on 2018-01-29
I actually returned this laptop and went back to Mac. The laptop and Ubuntu are super nice, but...the trackpad hardware and software simply aren't as refined as those on Mac. Also just overall more comfortable with that platform. Otherwise, this is a super nice laptop, and Ubuntu is fantastic.

I didn't experience any problems with the battery not charging to 100% (or at least, it showed 100% in the battery charge indicator).

The sound and brightness F keys worked fine for me. I didn't really play with the others.

---

