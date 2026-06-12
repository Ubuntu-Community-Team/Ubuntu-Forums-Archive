---
title: "&quot;Insert disc Uu-Server 9.10 _KK_ in the drive '/cdrom/'&quot;"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by OctaneZ on 2009-11-10
I am trying to install Ubuntu Server 9.10 on a Dell Poweredge SC420. However when I configure LVM on the hard drives I end up in a loop with the following error:
```
[!!]Install the base system
Please insert the disc labeled: 'Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)' in the drive '/cdrom'/ and press enter.

Media change
```

I have tried umount'ing /cdrom and remounting at: /cdrom /mnt/cdrom /target/cdrom and /target/mnt/cdrom all with no luck, any ideas?

---

### Post by OctaneZ on 2009-11-10
I tried editing the sources.list file that was suggested here:
[http://ubuntuforums.org/archive/index.php/t-1000651.html](http://ubuntuforums.org/archive/index.php/t-1000651.html)
with no luck.

---

### Post by Mr_B on 2009-11-18
I had the same problem. I had an IDE CD/DVD drive and when I swithced to a SATA CD/DVD drive everything worked fine. I also read in the above link from OctanZ that some people have had success with a USB installation. The problem is with some IDE drives or drivers.

---

### Post by Raycho Raykov on 2009-12-11
I have the same problem with Ubuntu-Server 9.10 - AMD64. My IDE DVD was connected as "Cable Select". When I changed it to "Slave", the problem desapears.

Good luck!

---

### Post by skrittak on 2009-12-11
Do you mean the jumper settings on the IDE DVD Raycho?

---

### Post by Raycho Raykov on 2009-12-11
Yes, but it doesn't work every time. May be there is something else. I succeeded once but subsequent tries was unsuccessful. I'm still looking for solution.

---

### Post by skrittak on 2009-12-14
Yeah setting the cdrom to slave hasn't made any difference to me Raycho

---

### Post by Confusatron on 2009-12-26
I'm having the same issue with a clean install of 9.10 alternate amd64. CD ISO MD5 ok, verified burn, 'check disc for defects' also ok. Definitely seems to be a media or drive issue, I'm wondering if the installer changes how the drive is accessed?

Relevant info from /var/log/syslog:

> 
Dec 26 22:17:25 kernel: [    0.660412] ata1.01: ATAPI: _NEC DVD_RW ND-3520AW, 3.07, max UDMA/33
Dec 26 22:17:25 kernel: [    0.700316] ata1.01: configured for UDMA/33
Dec 26 22:17:25 kernel: [    0.704208] scsi 0:0:1:0: CD-ROM            _NEC     DVD_RW ND-3520AW 3.07 PQ: 0 ANSI: 5
Dec 26 22:17:25 kernel: [    0.706047] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Dec 26 22:17:25 kernel: [    0.706050] Uniform CD-ROM driver Revision: 3.20
Dec 26 22:17:25 kernel: [    0.706177] sr 0:0:1:0: Attached scsi CD-ROM sr0
Dec 26 22:17:25 kernel: [    0.706256] sr 0:0:1:0: Attached scsi generic sg0 type 5
-=SNIP=-
Dec 26 22:17:53 cdrom-detect: Searching for Ubuntu installation media...
Dec 26 22:17:53 kernel: [   30.966808] ISO 9660 Extensions: Microsoft Joliet Level 3
Dec 26 22:17:54 cdrom-detect: CD-ROM mount succeeded: device=/dev/sr0
Dec 26 22:17:54 kernel: [   31.050129] ISO 9660 Extensions: RRIP_1991A
Dec 26 22:17:54 cdrom-detect: Detected CD 'Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)'
Dec 26 22:17:54 cdrom-detect: Detected CD 'Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)'
Dec 26 22:18:13 cdrom-detect: Detected CD with 'karmic' (karmic) distribution
-=SNIP=-
Dec 26 22:24:40 debootstrap: Processing triggers for initramfs-tools ...
Dec 26 22:24:41 base-installer: Using CD-ROM mount point /cdrom/
Dec 26 22:24:41 base-installer: Identifying.. 
Dec 26 22:24:47 kernel: [  444.770347] sr 0:0:1:0: [sr0] Unhandled sense code
Dec 26 22:24:47 kernel: [  444.770353] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 26 22:24:47 kernel: [  444.770357] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
Dec 26 22:24:47 kernel: [  444.770364] Info fld=0x69
Dec 26 22:24:47 kernel: [  444.770367] sr 0:0:1:0: [sr0] Add. Sense: No seek complete
Dec 26 22:24:47 kernel: [  444.770372] end_request: I/O error, dev sr0, sector 420
Dec 26 22:24:47 kernel: [  444.770468] ISOFS: unable to read i-node block
Dec 26 22:24:53 kernel: [  450.798057] sr 0:0:1:0: [sr0] Unhandled sense code
Dec 26 22:24:53 kernel: [  450.798060] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 26 22:24:53 kernel: [  450.798064] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
Dec 26 22:24:53 kernel: [  450.798070] Info fld=0x62
Dec 26 22:24:53 kernel: [  450.798072] sr 0:0:1:0: [sr0] Add. Sense: No seek complete
Dec 26 22:24:53 kernel: [  450.798076] end_request: I/O error, dev sr0, sector 392
Dec 26 22:24:53 kernel: [  450.798175] ISOFS: unable to read i-node block
Dec 26 22:24:59 base-installer: [224d23dcf19dc56d5b2320a766bb8e14-2]
Dec 26 22:24:59 base-installer: Scanning disc for index files..
Dec 26 22:24:59 base-installer: Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Dec 26 22:24:59 base-installer: Found label 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)'
Dec 26 22:24:59 base-installer: This disc is called: 
Dec 26 22:24:59 base-installer: 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)'
Dec 26 22:24:59 base-installer: Copying package lists...
Dec 26 22:24:59 base-installer: gpgv: Signature made Tue Oct 27 17:17:23 2009 UTC using DSA key ID FBB75451
Dec 26 22:24:59 base-installer: gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Dec 26 22:25:00 base-installer: ^MReading Package Indexes... 0%^M^MReading Package Indexes... 1%^M
Dec 26 22:25:00 base-installer: ^MReading Package Indexes... Done^M
Dec 26 22:25:00 base-installer: Writing new source list
Dec 26 22:25:00 base-installer: Source list entries for this disc are:
Dec 26 22:25:00 base-installer: deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
Dec 26 22:25:00 base-installer: Repeat this process for the rest of the CDs in your set.
Dec 26 22:25:00 base-installer: W: Skipping non-exisiting file /cdrom/dists/karmic/main/binary-amd64/Packages
Dec 26 22:25:00 base-installer: W: Skipping non-exisiting file /cdrom/dists/karmic/main/debian-installer/binary-amd64/Packages
Dec 26 22:25:00 base-installer: W: Skipping non-exisiting file /cdrom/dists/karmic/restricted/binary-amd64/Packages
Dec 26 22:25:00 base-installer: W: Skipping non-exisiting file /cdrom/dists/karmic/restricted/debian-installer/binary-amd64/Packages
Dec 26 22:25:00 base-installer: Reading package lists...
Dec 26 22:25:00 base-installer: 
Dec 26 22:25:01 in-target: Reading package lists...
Dec 26 22:25:01 in-target: Building dependency tree...
Dec 26 22:25:01 in-target: 
Dec 26 22:25:01 in-target: locales is already the newest version.
Dec 26 22:25:01 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Dec 26 22:25:01 localechooser: Generating locales...
Dec 26 22:25:01 localechooser:   en_US.UTF-8... 
Dec 26 22:25:04 localechooser: done
Dec 26 22:25:04 localechooser: Generation complete.
Dec 26 22:25:04 localechooser: Generating locales...
Dec 26 22:25:04 localechooser:   en_US.UTF-8... 
Dec 26 22:25:04 localechooser: up-to-date
Dec 26 22:25:04 localechooser: Generation complete.
Dec 26 22:25:04 preseed: perl: warning: Setting locale failed.
Dec 26 22:25:04 preseed: perl: warning: Please check that your locale settings:
Dec 26 22:25:04 preseed: 	LANGUAGE = (unset),
Dec 26 22:25:04 preseed: 	LC_ALL = (unset),
Dec 26 22:25:04 preseed: 	LANG = "C.UTF-8"
Dec 26 22:25:04 preseed:     are supported and installed on your system.
Dec 26 22:25:04 preseed: perl: warning: Falling back to the standard locale ("C").
Dec 26 22:25:04 preseed: locale: Cannot set LC_CTYPE to default locale: No such file or directory
Dec 26 22:25:04 preseed: locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Dec 26 22:25:04 preseed: locale: Cannot set LC_ALL to default locale: No such file or directory
Dec 26 22:25:05 in-target: Reading package lists...
Dec 26 22:25:05 in-target: Building dependency tree...
Dec 26 22:25:05 in-target: Recommended packages:
Dec 26 22:25:05 in-target:   pciutils
Dec 26 22:25:05 in-target: The following NEW packages will be installed:
Dec 26 22:25:05 in-target:   installation-report
Dec 26 22:25:16 init: starting pid 377, tty '/dev/tty2': '-/bin/sh'



Sounds like the next step is to dig up a different CD/DVD drive, but that seems like a dumb solution, since this machine was able to install 8.10 alternate amd64... Also, the drive is really hard to remove ;-)

---

### Post by Confusatron on 2009-12-27
Well, a different CD-RW drive solved it for me. Still, seems like a bug that a known good DVD-RW drive that burned a good CD (since it worked fine on the other drive) can't install from it...

---

### Post by stieg on 2010-01-13
I just got past this by going into my BIOS and setting my SATA devices to use AHCI instead of ATA.  Now the Ubuntu 9.10 amd64 server disc gets past that point and continues like it should.

Did this on a Dell Precision T3400.  Hope that helps.

---

### Post by krosswindz on 2010-01-22
I am seeing the same error on a Dell Inspiron 530, I set my SATA mode to RAID (AHCI) still doesnt work. One thing I noticed was that the it is generating the apt/sources.list as _Karmic Koala_ while the cdrom-detect shows it as "Karmic Koala". I am wondering if this is the issue why it is failing there?

---

### Post by clenched_sphere on 2010-02-05
I managed to get this to work by following a few steps:

1. sudo vi /etc/apt/sources.list (use nano or vim or something if you dont use vi)
2. find the line:

deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted

add a hash (#) at the start to comment it out. Don't delete it incase you find yourself without a net connection and a need to install something from the cd repoisitory one day :D
The new line should read:

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted

save and quit.

3. Update aptitude - we've just changed it's conf file so need to get apt to update its sources. Type:
sudo apt-get update

4. Try and install your package - the one i was having an issue with was "whois". Even when I *removed* the cd drive it would ask for the disc. Got it installed after following these steps from online repositories.

Hope this helps anyone who had the same issue.

---

### Post by sligoman on 2010-04-22
After selecting guided use entire disk and continuing instead of writing I selected no and changed the ext4 to ext3 and had no probs from there on.

that's how I overcame the bootstrap warning on my Dell poweredge 600SC using Ubuntu server 9.10

All I know is that my machine did not like EXT4 but was happy with EXT3 so if someone can tell me if that is a good thing or not as I am a newbie to Linux

Regards

Sligoman

---

### Post by clenched_sphere on 2010-04-24
> 
All I know is that my machine did not like EXT4 but was happy with EXT3  so if someone can tell me if that is a good thing or not as I am a  newbie to Linux


as i understand it, there isn't really much difference from the user's perspective between Ext3 and Ext4. to explain the differences would require one more knowledgeable than I.

no real drawbacks anyway.:guitar:
is that meant to be toni iomi? ^^

---

