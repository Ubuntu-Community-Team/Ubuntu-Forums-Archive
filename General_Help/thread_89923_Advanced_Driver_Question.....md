---
title: "Advanced Driver Question...."
date: 2005-11-13
forum: General Help
---

### Post by TrueDego on 2005-11-13
Ok, Im wanting to install a RAID driver (Promise FastTrak 100 Controller) onto my work machine in Ubuntu.  The problem is that the only drivers for it are for Red Hat, SUSe, Turbo, and Open Linux.  Is there anyone I can recompile the drivers to be able to work in Ubuntu?  I couldnt find any source drivers.  I'll have some fellow employees check on this when im not here so try to noob your answers as much as possible.  Thanks.....

---

### Post by taurus on 2005-11-13
You can use "alien" to convert rpm to deb and then install it with dpkg...

---

### Post by TrueDego on 2005-11-13
Where would Alien be located/how would i run it after i install it?

---

### Post by taurus on 2005-11-13
If you don't have it on your system, then use apt-get to install it...  Then at the prompt, do

sudo apt-get install alien
sudo alien --to-deb <package name>.rpm
sudo dpkg -i <package name>.deb
-or-
man alien

p.s.  You may also want to install the "build-essential" as well...

---

### Post by xurizaemon on 2005-12-04
Hey guys, I have a Promise S150 SX4-M here. Belongs to a customer; same story.

Caveat #1: much of this is internet research and thus hearsay.
Caveat #2: I haven't got the card working to my satisfaction yet!

Here's what I've found over a few days of research:

[LIST]
[*] Promise drivers (even the partial source code version you can download from promise.com.tw) provide FRAID (fakeraid) functionality, but this does not necessarily equate to a boost in performance over Linux MD RAID. From what I've read, MD sounds preferable, probably why it's so hard to find good docs on how to do it "the Promise way".
[*] Promise partial drivers probably won't get updated down the track, because it's cheaper for them to piggy-back on existing MD implementation. [FT vs MD]("http://lists.centos.org/pipermail/centos/2005-May/006197.html")
[*] It seems like you can get this card etc to behave with stock kernel modules rather than doing the driver dance Promise suggest.
[*] But, to boot off such a RAID card you probably need to do some mkinitrd trickery. (Do you REALLY need to BOOT off the RAID card, though?)
[/list]

Here's how far I got ...

Ubuntu (for me) sees this card with the default kernel (I'm running 2.6.12-9-386 on Ubuntu 5.10). I believe it even autodetected the necessary modules, which for me are: **sata_sx4, sd_mod, scsi_mod, libata**

You can use mdadm to create a RAID array of your disks if they appear therein. For me to create a RAID5 array of disks /dev/sda, /dev/sdb, /dev/sdc I did the following steps.

[LIST=1]
[*] Partition the disks /dev/sda, /dev/sdb, /dev/sdc with a single partition of type 'fd'.
[*] Create the RAID5 array with mdadm:
```
sudo mdadm --create /dev/md0 --level=5 --raid-disks=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```
[*] Format the new disk /dev/md0 with my preferred partition etc.
[*] Mount /dev/md0 somewhere useful.
[/list]

This worked, but the resulting array is (1) far smaller than the 500Gb it ought to be - only 19Gb, and (2) trying to copy any large amount of data results in /dev/md0 going read-only after a short period.

Feels like I'm on the right track but not there yet. Anyway, hopefully these tidbits can help someone else who is facing the same challenge! Any more clues to share?

---

### Post by xurizaemon on 2005-12-04
[QUOTE=taurus]You can use "alien" to convert rpm to deb and then install it with dpkg...[/QUOTE]

The driver disks (at least the S150 drivers) are for the installation process and not just a 'normal' RPM. So this is a bit of a red (hat) herring, because there is no RPM to alien. There is a modules.cgz file, but alien doesn't eat those.

Not sure if I would suggest using alien to install an RPM of a kernel module anyway - do you think that would work, normally? Alien is great for software that's packaged for RH, but I'm unsure it's the right solution for kernel-level stuff.

I'm no alien expert though ...

---

### Post by xurizaemon on 2005-12-04
Some more references:

If you have mdadm installed, read this doc - [RootRaidHowto]("file:///usr/share/doc/mdadm/rootraiddoc.97.html"). If you don't have mdadm installed then you can obtain the same doc via [http://alioth.debian.org/projects/rootraiddoc](http://alioth.debian.org/projects/rootraiddoc)

[Serial ATA cards and support in Linux]("http://linuxmafia.com/faq/Hardware/sata.html") is useful information. Discussion of various hardware and current OS support. Some of the thoughts on Promise cards in this made me reconsider whether it was worthwhile expenditure of time making the Promise card go, versus doing 'plain' software RAID in Linux.

Read the [Software RAID HOWTO]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html").

Check out the [Promise S-150 SX4-M Downloads]("http://www.promise.com.tw/support/download/download2_eng.asp?productID=124&category=all&os=100").

Russian page with [some kernel compile settings]("http://www.linuxshare.ru/docs/hardware/fasttrak.html") (not much help unless you read russian or can make sense of the settings alone).

---

### Post by schdefan on 2005-12-08
I compiled a kernel module for SATA 300 TX4 from Promise.
I downloaded the sources from manufactors homepage 
[SATA 300 TX4 for kernel 2.6]("http://www.promise.com/support/download/download2_eng.asp?productID=139&category=all&os=100#")
Installed the kernel-sources, run make for a few seconds and then compiled the module. 
I got the module ulsata2 and copied to /lib/modules/$(uname -r)/kernel/drivers/scsi/
and add it to /etc/modules.

from the README file
> This driver should be used with all Promise SATAII150/300 Series adapter and onboard chipsets running under Linux operating system. 


Support List
============

The following Promise SATAII150/300 series adapters and Linux operating systems are
compatible with the drivers in this release:

Chipset         Adapter Name
--------        ------------
PDC40518        Promise SATAII150 TX4
PDC20575        Promise SATAII150 TX2plus
PDC20579        Promise SATAII150 579
PDC40718        Promise SATA300 TX4
PDC20775        Promise SATA300 TX2plus
PDC20779        Promise SATA300 779

OS              kernel version
--              --------------
Red Hat EL4 AS   kernel 2.6.9-5
SuSE Pro 9.2       kernel 2.6.8-24
N/A                   kernel 2.6.x    (kernel compiled by yourself)

schdefan

---

