---
title: "Dual-booting frustration (Intrepid/Studio)"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Lull The Conqueror on 2009-02-08
I've searched for other posts about getting Ubuntu 8.10 to properly dual-boot with Ubuntu Studio 8.10, but none of them seem to be having my problem, so I figured it wouldn't hurt to ask.

As the thread title implies, I'm trying to get "regular" 8.10 to dual-boot with Studio 8.10; actually, it would be a triple-boot, as I also have a Windows partition, but that's on a different drive and I highly doubt it has anything to do with this in the first place.

The first problem is that while the Ubuntu Studio installer says it reinstalls GRUB to the MBR, apparently it's still using the menu.lst file from my other Ubuntu install.  No problem, I just get in and edit menu.lst to point to the partition where Studio is installed, right?  Trying that gives me one of two problems:

If I mount the Studio partition and copy/paste its entry from its own menu.lst file into the one GRUB is reading, it shows up on the menu, but when I try to enter it I get the loader screen for a couple of seconds, then several devices fail to mount, I get "target filesystem doesn't have /sbin/init" and "try passing init= bootarg" along with a host of other error messages, and I get a command prompt from which I don't know how to do anything.

Things are simpler if I write my own entry, with root (hd1,2) - this being the partition on which Studio is installed - makeactive, and chainloader +1.  Then I just get something like "Error 13: No valid executable on device" or somesuch, and I have to reboot.  I guess I should be transcribing the exact error messages it gives me, but I get frustrated easily, and I've already deleted my Studio partition.

Any suggestions for doing an install that actually works?  I suppose I could just reformat and install it on my main Ubuntu partition (all my important files are on another partition, so it wouldn't be a big deal), but I like the idea of being able to boot into either, depending on what I want to do.

---

### Post by lha on 2009-02-10
Try to reinstall Studio. When you are done, add
```

title        Ubuntu Studio
configfile   (hd1,2)/boot/grub/menu.lst

```
to Intrepix's /boot/grub/menu.lst. Hopefully, that will do the trick. If you still experience mount fails or some other boot problems, please report them - there shouldn't be any reason why you couldn't have a fully working  triple-boot.

---

### Post by Lull The Conqueror on 2009-02-10
Thanks, didn't know you could do that with menu.lst.  Yeah, I'm not exactly a guru. ;)

Unfortunately, when it loads the Studio version of menu.lst and I try to boot into Studio, it gives me exactly the same error it did when I copy/pasted the entry.  This time I didn't delete the partition, and I wrote down all the error messages:

> Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/sda3) = dev(8,3)
kinit: trying to resume from /dev/sda3
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/(uuid here; didn't write it down) on /root failed: Device or resource busy
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found.  Try passing init= bootarg.

Then it goes into BusyBox, and I shake my head and reboot.  Not even sure what it's trying to do here.

---

### Post by snowpine on 2009-02-10
What is the goal of dual-booting Ubuntu with Ubuntu Studio? You can install all of the Studio apps in Ubuntu without dual booting, for example:

```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt
```

Which will install all of the audio applications and real time kernel. If it's a theming issue, you could have separate user accounts for "regular" and "studio".

---

### Post by Lull The Conqueror on 2009-02-10
Maybe I should just do that, then.  Is there any real difference in how they work as OSes, or is Studio basically just the current Ubuntu with extra packages installed?

---

