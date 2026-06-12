---
title: "Ubuntu Installation boot issue"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by AnirudhVyas on 2009-06-19
Hi,

My setup right now is like this:

RAID 0 -> Windows Vista Ultimate 64 bit (250 + 250 GB)
Non Raid -> Ubuntu Server edition (1 TB)

I set the boot order up so that the one with Ubuntu boots, but currently only Vista boots up, I check the device, (on vista disk management), the drive is fine and partition is healthy and Non Windows as expected.


Any suggestions?

Rick

---

### Post by dstew on 2009-06-19
Does the Ubuntu disk have a boot loader installed?

---

### Post by AnirudhVyas on 2009-06-19
Well yes, but the strange thing is when it was installing boot loader, it recognized vista as the OS (even though this is a new disk) and then asked to say yes if it'd be safe to install GRUB.

I "think" i hit yes, I am complete noob at Linux so bear with me. How do I make sure that its there ...

?
Rick

---

### Post by raymondh on 2009-06-19
Hello Rick,

If you wish, there is a bootinfo script (thnaks to meierfra) that can assist you in troubleshooting boot errors.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

When you download it, open a terminal to type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

which will produce (and save to desktop) a RESULTS.TXT file that you can post back.  Remember, when you post, to wrap the results.txt file in codes (#) to make the scrolling easier :)

---

