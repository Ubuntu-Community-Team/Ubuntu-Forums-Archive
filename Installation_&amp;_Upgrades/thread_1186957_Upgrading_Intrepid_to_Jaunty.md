---
title: "Upgrading Intrepid to Jaunty"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by lotster on 2009-06-14
Hi! I'm running intrepid at the moment, but I already ordered my Jaunty CD from Canonical.  However, then I heard that I need another disc in order to do an upgrade.

Since I don't really want to format (though I will if I have to), and I don't want to download another disc's ISO, I was thinking of upgrading through the Update Manager.  However, due to limited internet bandwidth, I was wondering if someone could please confirm how much information will be downloaded from the internet?  Altrenatively, is there a way for me to upgrade using the normal 9.04 CD when it arrives?

---

### Post by expelledboy on 2009-06-14
You can do a dist-upgrade using the cd when it arrives.

If you want to find out how much will be downloaded for a dist-upgrade run this
```
sudo apt-get dist-upgrade
```
and if you decide it is too much just type in **n** and hit enter to cancel or ctrl+C to kill the process..

---

### Post by presence1960 on 2009-06-14
I would recommend a clean install. The reason being that as I read the forums most people complaining about Jaunty are people who have done an upgrade rather than a clean install. For whatever reason there seems to be a lot of problems with the upgrade process to Jaunty.

---

### Post by raymondh on 2009-06-14
> **presence1960 said:**
> i would recommend a clean install. The reason being that as i read the forums most people complaining about jaunty are people who have done an upgrade rather than a clean install. For whatever reason there seems to be a lot of problems with the upgrade process to jaunty.

+1 ... also, run a live session first to see how the distro reacts to your machine (wifi, sound, keypad, F keys, etc)

---

### Post by expelledboy on 2009-06-15
> **presence1960 said:**
> I would recommend a clean install. The reason being that as I read the forums most people complaining about Jaunty are people who have done an upgrade rather than a clean install. For whatever reason there seems to be a lot of problems with the upgrade process to Jaunty.

heh.. I wouldnt know. I always do a clean install. ;)

---

### Post by lotster on 2009-06-15
Thanks, everyone.  I will rather do a clean install then.  However, here I need some help again...

I'm dual-booting XP and Ubuntu (two different drives).  How do I go about doing the clean install?  Do I just boot to the disc and point it the partitioner to the correct drive?  Does it sort out all the GRUB-related things automatically?  Or will I be stuck with a non-working "Ubuntu 8.10" option in my boot menu?

---

### Post by presence1960 on 2009-06-15
> **lotster said:**
> Thanks, everyone.  I will rather do a clean install then.  However, here I need some help again...

I'm dual-booting XP and Ubuntu (two different drives).  How do I go about doing the clean install?  Do I just boot to the disc and point it the partitioner to the correct drive?  Does it sort out all the GRUB-related things automatically?  Or will I be stuck with a non-working "Ubuntu 8.10" option in my boot menu?

When you get to the Prepare disk space window of the partitioner choose "manual" option and highlight the disk/partition you want Ubuntu to install to. Then set all the parameters ( partition type, use as [filesystem] and mountpoint [/] for root). The only thing you may have to edit with GRUB is your windows entry, but that is a cinch.

---

### Post by lotster on 2009-06-15
Thank you all very much!  I think I'll be okay with it now...

---

