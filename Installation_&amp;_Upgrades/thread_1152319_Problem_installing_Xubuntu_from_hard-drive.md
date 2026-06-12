---
title: "Problem installing Xubuntu from hard-drive"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by AlFrugal on 2009-05-07
I'm trying to install Xubuntu 9.04 from my hard drive (as opposed to installing from a CD). I'm using the "Live CD" procedure from: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

After I answer all of the installler questions, the installer proceeds and shortly thereafter issues the message:

===============================================================================================================

Failed to unmount partitions

The installer needs to commit changes to partition tables, but cannot do so becasue partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

==============================================================================================================

I've restarted the PC and even power-cycled it. The same problem happens.


/dev/sda2 is mounted on /cdrom. If I try to manually unmount it, umount fails, saying the device is busy.

The ISO was downloaded to sda2. The "mount -o" (loopback) mount from the "Live CD" procedure was also to sda2. The files from the ISO were extracted into sda2. My entry in /boot/grub/menu.lst for the Xubuntu install (as described in the "Live CD" procedure) has root (sd0,1), i.e. it points to sda2. I've selected /dev/sda5 as root partition (where Xubuntu should be installed).

This procedure is making sda2 look like a CD-ROM.

I've used this procedure before on another PC to install Ubuntu 7.10 from a hard drive. There were no problems. (I used a different set of partitions in that case).


Why is this install from hard-drive not working?

---

### Post by logos34 on 2009-05-07
unless this

root (sd0,1)

is a typo it should be (**[COLOR="Red"]h[/COLOR]**d0,1)

---

### Post by AlFrugal on 2009-05-07
> **logos34 said:**
> unless this

root (sd0,1)

is a typo it should be (**[COLOR="Red"]h[/COLOR]**d0,1)

It's a typo. At boot, the GRUB menu was displayed. I selected the (temporary) Xubuntu entry (which was the extracted ISO on sda2) and it booted fine. However, the install of a permanent copy of Xubuntu onto sda5 fails, as described above..

(I'm posting messages in this thread from my primary PC. Xubuntu is on my secondary PC, which has been powered off during both of my posts to this thread. I wasn't viewing menu.lst when I composed the post).

---

### Post by logos34 on 2009-05-07
[edit]

Just noticed the ["Note" (below step 4)]("https://help.ubuntu.com/community/Installation/FromLinux"):

> Note: if you unpacked the livecd on the same disk where you want to install Ubuntu, chances are you'll run into LP#288675, and be unable to select a partition. The workaround by Nick Spencer ("sudo umount -l -r -f /dev/sda3 ([COLOR="Red"]where sda3 was the device mounted as cdrom[/COLOR])") is a rather terrible hack, but usable as a workaround.

so maybe try it with /dev/sda2 in your case

---

### Post by AlFrugal on 2009-05-08
> **logos34 said:**
> [edit]

Just noticed the ["Note" (below step 4)]("https://help.ubuntu.com/community/Installation/FromLinux"):



so maybe try it with /dev/sda2 in your case

That did the trick. Thanks *very* much for your help.

I did not originally see the "Note" below step 4. I was using a local copy of that document that I had downloaded in February 2008 (when I did an install from hard-drive of Ubuntu 7.10 on my main PC). The document at that time did not have the "Note" included with step 4.

---

### Post by AlFrugal on 2009-05-08
Update: The install ran to completion, taking about an hour, and appeared to go smoothly. The installer built a new GRUB menu, but it only contains an entry for memtest. /boot on SDA5 does not contain a vmlinuz for kernel 2.6.28 (the kernel level of Xubuntu 9.04 live CD). /boot does contain several of the other files for 2.6.28.

I've run the install several times. Initially not reformatting SDA5 (which previously contained a dysfunctional copy of Ubuntu 8.04), and then reformatting it. The result was the same for all trials.

/etc/fstab for the Xubuntu Live-CD (i.e the extracted ISO) does not contain an entry for sda2.

---

### Post by logos34 on 2009-05-08
> **AlFrugal said:**
> Update: The install ran to completion, taking about an hour, and appeared to go smoothly. The installer built a new GRUB menu, but it only contains an entry for memtest. /boot on SDA5 does not contain a vmlinuz for kernel 2.6.28 (the kernel level of Xubuntu 9.04 live CD). /boot does contain several of the other files for 2.6.28.

I've run the install several times. Initially not reformatting SDA5 (which previously contained a dysfunctional copy of Ubuntu 8.04), and then reformatting it. The result was the same for all trials.


Huh?  It didn't install the kernel??? what about initrd-img?

The fact that it's making a grub dir with menu,lst (empty though it is) at least indicates it knows the /boot is there, and not a separate partition.

---

### Post by AlFrugal on 2009-05-09
Following are the contents of /boot on sda5 following the most recent install attempt (where the installer reformatted sda5):

GRUB (folder)
abi-2.6.28-11-generic
config-2.6.28-11-generic
initrd.img-2.6.28-11-generic
memtest86+.bin
Systemmap-2.6.28-11-generic
vmcoreinfo-2.6.28-11-generic

I checked the md5sum of the downloaded ISO on sda2. It is OK.

Afterthought:

I did a Google search on: vmlinuz missing. I found a "Ubiquity" bug where the installer doesn't copy vmlinuz from casper if it detects a pre-existing install.

In all of the cases where I ran the install, there were remnants of a previous Ubuntu install. The first time, there were remnants of Ubuntu 8.04. In all subsequent trials, there were remnants of a failed Xubuntu 9.04 install.

So, perhaps I should reformat sda5 (via Knoppix LiveCD -> Qtparted) to erase all remnants of Ubuntu and then rerun the Xubuntu install. GRUB is set up to look for /boot in sda5. If I have Knoppix reformat sda5, then I won't be able to boot my Xubuntu LiveCD extracted ISO in sda2. I would have to reinstall GRUB and have it look for /boot in sda2.

---

### Post by logos34 on 2009-05-09
interesting bug...i'll have to bookmark this

real catch-22 with grub, sda5, format...um, maybe copy everything in /boot to a small, [dedicated grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")...then you can delete sda5 and still boot.  Or make a [grub boot floppy.]("https://help.ubuntu.com/community/GrubHowto/BootFloppy")

or make a grub boot [CD]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html")

---

### Post by AlFrugal on 2009-05-10
Problem (apparently) solved.

Using Knoppix, I manually copied vmlinuz from sda2 /casper to sda5 /boot and I then renamed it to vmlinuz-2.6.28-11-generic. Also in Knoppix I updated sda5 /boot/grub/menu.lst to include an entry for Xubuntu.

Xubuntu now boots and I was able to log in to my user account. Time will tell if I have a clean install.

So it looks like there is a bug in the installer when installing into a partition that previously contained Ubuntu. (The installer does not copy vmlinuz from casper).

---

