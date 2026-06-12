---
title: "is there a problem with 9.10 and having several HDs?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by northwestuntu on 2009-11-12
ive read a couple places saying 9.10 can't handle multiple hard drives? im still thinking of upgrading but that would be a big problem since i have 3 hard drives.

anyone have problems with this?

---

### Post by MG37221 on 2009-11-12
> **northwestuntu said:**
> ive read a couple places saying 9.10 can't handle multiple hard drives? im still thinking of upgrading but that would be a big problem since i have 3 hard drives.

anyone have problems with this?

I'm using two hard drives.  They're both SATA and my /home partition is on one while my / is on the other smaller drive.  I don't think multiple drives are a problem but yes, there are problems with 9.10.  Several users have been experiencing random lockups.  Mine have been averaging about one a day though today has been so bad that I am seriously considering going back to 9.04, which really worked like a charm.  This has been a frustrating experience for me.

---

### Post by northwestuntu on 2009-11-12
thanks for the info. ill have to rethink the upgrade.

---

### Post by MG37221 on 2009-11-12
This is my experience.  Hopefully others will contribute theirs.  Been with Ubuntu since 7.04 (SuSE before that) and this has been my first difficulty - always done a clean install.

---

### Post by Ginsu543 on 2009-11-12
I too initially had difficulty installing Karmic because I have multiple (4) SATA drives in my system. In my case, the Karmic installer had trouble recognizing my SATA drives that had been used previously in a RAID array (something wrong with dmraid). After a week of troubleshooting, I've finally got everything working. I understand your frustration and desire to go back to Jaunty (I actually dual-boot Jaunty because it's been great for me and didn't want to get rid of it), but Karmic is a very nice OS once you get it to work.

---

### Post by GmAz on 2009-11-12
> **Ginsu543 said:**
> I too initially had difficulty installing Karmic because I have multiple (4) SATA drives in my system. In my case, the Karmic installer had trouble recognizing my SATA drives that had been used previously in a RAID array (something wrong with dmraid). After a week of troubleshooting, I've finally got everything working. I understand your frustration and desire to go back to Jaunty (I actually dual-boot Jaunty because it's been great for me and didn't want to get rid of it), but Karmic is a very nice OS once you get it to work.

Glad you got past your raid array issue.  I never got past mine.  Even with dmraid disabled at the install, though it would recognize the four drives, it wouldn't let me choose one of them to install too.  Since this was at work and only used for a FOG server, i just went back to 9.04.

---

### Post by audiomick on 2009-11-12
Hi.
I've upgraded to 9.10 with no disc related problem. The only thing I have is to do with synching the phone via usb / obex / syncml
I also have a smaller disc with a / partition and a larger with a /home. There is also another install in there that grub isn't offering at the moment, but I can't say if that has to do with 9.10 or not, because I haven't booted it for about 8 months.
On the other hand, I had a lot of trouble when the computer was new. The discs are Samsung, i.e. cheap, and they, along with a DVD player, a MP3 player and they discs in my NAS have convinced me to NEVER EVER EVER EVER buy anything with "samsung" written on it again.
The solution with the boot problems with the computer was to turn off all the "fast boot" options in BIOS and fiddle with the cables in the computer to make sure that the connectors are not under [U]ANY[U] mechanical strain. The SATA plugs are mechanically really dickey, wobbly and no locking. Mine were in, but because of the way the cables were lying, they were under a bi of lateral stress. I "relaxed" the cables, and, as I said, slowed down the boot, and have had no problems since.

---

### Post by MG37221 on 2009-11-12
> **GmAz said:**
> Even with dmraid disabled at the install, though it would recognize the four drives, it wouldn't let me choose one of them to install too.  

Something special about your setup?  I had to redefine my partitions manually but had no [drive] problems installing on the partition of the exact drive I wanted it on.  Other problems?  Oh yes, but none with the partitioner.

---

### Post by Ginsu543 on 2009-11-12
> **GmAz said:**
> Glad you got past your raid array issue.  I never got past mine.  Even with dmraid disabled at the install, though it would recognize the four drives, it wouldn't let me choose one of them to install too.  Since this was at work and only used for a FOG server, i just went back to 9.04.
Sorry to hear that you continued to have problems with your raid array issue. This may be moot at this point, but did you ever try disconnecting all the other drives except for the one you were trying to install to? I was only able to install after I removed all but the the one drive and ran "sudo apt-get remove dmraid" before launching the installer.

---

