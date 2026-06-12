---
title: "Installed but no boot"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by InFESTation on 2006-01-02
Hello,
Like many others I have toyed with trying Linux OS' for a while and thought I'd give this a try, sadly not going too well, I have trawled the forums no joy to what I was trying to find (probably there just didn't understand/realise).
Anyhow, I am trying to install (dual boot winXP pro) to a 5GB partition on the IDE HD that I use for documents etc, windows boots/installed on the SATA drive, the installation appears to go fine and even says it is writing the grub for the dual OS to the MBR and then reboots only then the machine goes straight to windows no choices menu or anything.
Any help or guidance would be greatly appreciated.
Thanks in advance.

Sys spec
120 GB SATA; 40 GB IDE; ASUS A7N8X MB, ATI 9500 pro Graphics; SB live 5.1 Sound card; athlon xp 3200+; optical drives - DVD + CDROM
maybe of help?

---

### Post by UbuWu on 2006-01-02
Make sure you install grub to the first partition (probably the windows partition in your case). Otherwise it will still boot the windows bootloader instead of grub.

---

### Post by InFESTation on 2006-01-03
Thanks for the reply, I am still unable to boot into ubuntu, I canned the idea of putting it onto my secondary drive and partitioned my primary drive with a swap and a linux partition, these were placed before the windows partition, I then tried a installation again and it appears to do all the business but still when it says that it writing the MBR and reboots it still goes through to windows with no options, is there any way to ensure that the Grub goes to the correct position or place it through windows.

---

### Post by InFESTation on 2006-01-03
Update:
Not sure what changed if anything, but I got it installed and managed to boot into it once then when going back into windows first of all couldn't get in on restart the grub has vanished again is this windows somehow binning the grub loader?
ubuntu while still there (I think/probably) is just unaccessible; time to search again.
Thanks anyhow.

---

### Post by UbuWu on 2006-01-03
You could use the instructions on the following wiki page, but I wouldn't recommend that to beginners:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by InFESTation on 2006-01-03
Thanks for that, I've decided to download some not so light reading, try to go through it and get some understanding of what I am supposed to be doing/ what is happening then will have another play, as I have done some additional reshuffling with the windows install and partitions now, just to sort this grub disappearance now; it is a touch frustrating going through the install procedure only to lose it all after the first log off.

---

### Post by UbuWu on 2006-01-03
If you want to know more about it, this is also a good read:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by InFESTation on 2006-01-03
Nice one thanks, that seems to break things down nicely, easier start than some of the other pages I've got.

---

