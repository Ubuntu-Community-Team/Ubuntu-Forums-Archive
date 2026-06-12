---
title: "Karmic on EEEPC 901?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by whitefort on 2009-11-02
Hi,

  Just curious to know if anyone has successfully got Karmic to run on an EEEPC 901 (specifically the one with the 15 and 4 gig drives)

Personally I've spent the weekend trying it, and have just given up.

Live CD is perfect.  Installation is a nightmare, frequently refusing to install on my drives, always showing a crash warning at some point during install.

Twice I DID manage to get it to install, but it ran too slowly to be usable (typically 2-4 minutes between login and the desktop appearing, and up to 30 seconds between selecting a menu item and the app actually running.

It also keeps telling me that my battery is broken.

If anyone has had more luck, I'd be REALLY grateful if you'd share the process, what options you selected, etc.

Personally, Karmic had me 98% certain that one of my 901's drives had failed, and it's only since reinstalling Jaunty that I've realised it's fine after all.

Any help would be appreciated, as I *quite* like Karmic, and it's running fine on all my other machines.

---

### Post by midnightflash on 2009-11-02
I installed 9.10-RC from a live-USB-flash made with unetbootin on my 901.
Quite plain... the interresting part:
# / was on /dev/sda5 during installation
UUID=1d0 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=802 /boot           ext2    defaults        0       2
# /home was on /dev/sdb1 during installation
UUID=ff9 /home           ext4    defaults        0       2

(shortened the UUID)

Had two issues: Yelling-fan and two-finger-tip-equals-right-click. (Both workarounded)

I'd say... just works.

ps: There is also an EFI-Partition for Boot-Boosting at the end of /dev/sda.

---

### Post by skotos on 2009-11-04
> **whitefort said:**
> Just curious to know if anyone has successfully got Karmic to run on an EEEPC 901 (specifically the one with the 15 and 4 gig drives)
 Worked flawlessly on mine with the 2 HDD.

> **whitefort said:**
> It also keeps telling me that my battery is broken.
Yes, it does this to me too. I thought it was because I never use it...

> **whitefort said:**
> If anyone has had more luck, I'd be REALLY grateful if you'd share the process, what options you selected, etc.
I was not able to run Karmic on the USB stick to make a clean install, but - instead - I went back to an old external USB CD drive that immediately worked.

Zapped away two big(?) Xandros partitions on the small drive and left the two 8 MB ones (I have to understand wtf they are there for).
I dedicated the last 512Mb to swap space and gave the rest to the / tree.
I used for the /home tree the 15 GB hdd as Xandros did and I did not even loose the Xandros *user*'s data.

Unfortunately 512Mb is not enough for hybernation, because you need at least the RAM size. I will resize the partitions accordingly, but I will take 1 GB from the 15 GB hdd, because the / partition is lacking necessary space (think of /tmp and downloaded packages).

HTH. Good luck!

---

### Post by skotos on 2009-11-04
One more thing: the UNR desktop does not work on the external LCD display if it is not mirrored.

An indipendent 1024x768 external display causes a mess in an unfortunately totally untested pre-release configuration!!

But!!!, **differently from the other i386 and 64bit Karmic releases, UNR works great with USB devices**. No problems at all!

---

### Post by whitefort on 2009-11-04
Thanks for the reply.

It turns out that my 901's hardware might have been having some problems.  One of karmic's (many) problems was that it couldn't see the 4Gig drive.

But that may have been because the drive was starting to fail, because now I've put Jaunty back on the machine, and the drive has just vanished, not even appearing when I check the devices in Gparted.  

I hate Karmic enough that I'm *almost* prepared to accuse it of breaking my drive... but not really - Karmic has its faults, but I don't think it's a computer trasher!

Anyway, I'm assuming that my 4 Gig drive has just died of old age, and now I'm wondering how long it will be before the 16 Gig drive follows.

---

### Post by skotos on 2009-11-06
I have now completed the partitions resizing:

/dev/sda (3.75 GiB)
```
/dev/sda1 3.74 GiB ext4 /
/dev/sda3 7.84 MiB unknown (untouched)
/dev/sda4 7.84 MiB unknown (untouched)
```/dev/sdb (15.03 GiB)
```
/dev/sdb1 14.03 GiB ext3 /home
/dev/sdb2 1.00 GiB linux-swap
```I resized everything after booting from the CD drive.
The /dev/sda1 resizing did not chaneg its uuid.
The new swap partition has, instead, a new uuid, thus this info had to be changed accordingly inside the /etc/fstab.

To read the new uuid:
```
sudo blkid
```
It took lots of time to *gparted* to successfully accomplish its tasks: more than an hour!

---

