---
title: "Disk cloning"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by PhilWig on 2009-10-21
I've installed Mythbuntu 9.04 on a 40GB drive which has 3 partitions holding  / (ext3), swap and /var/lib (xfs).

It's working fine after a lot of tuning (and grief for this Linux novice!) but I'd now like to transfer it to a 500GB SATA drive and take the 40G out of service, preferably without having to customisation myth again.

I'd like to change the layout to have partitions holding /boot (I'm told this will make dual booting and future upgrades easier - is that so?), a bigger swap, / and /var/lib/mythtv and some spare.  That will separate my media content in /var/lib/mythtv from system and configuration stuff in the rest of /var/lib to make backups more sensible.  The existing media content can be zapped before the move to save overflowing partitions.

I have set up a non-configured Mythbuntu on the 500G in order to partition the drive this way, write the MBR, and to set up /boot.  I've taken a copy of /etc/fstab to a usb stick to push back in later if necessary but would appreciate a few hints.

I'm thinking I now need to use a live distro to copy whole trees across, move the /var/lib stuff to the right place then replace the /etc/fstab.

Does what I'm saying make sense, and what tools would you now use to copy across and what needs copying? 

Phil

---

### Post by raprap30 on 2009-10-21
Using Linux, dd can be used to copy files, disks and partitions. It can output directly onto another disc or as an image (like an iso). To copy a hard disk, use this command when you are root, or sudo or sudo su before doing this:

dd if=/dev/hdx of=/dev/hdy

hdx is the input hard disk (to be copied) and hdy is the output hard disk (where it is to be copied to).

Use gParted to find out your drive&#8217;s paths. Good Luck.

---

### Post by linux-hack on 2009-10-21
or you can use CLONEZILLA

---

### Post by raprap30 on 2009-10-21
Yes [http://clonezilla.org/](http://clonezilla.org/). It has a cool GUI too. I would reccomend this if you are a newbie.

---

### Post by Shazaam on 2009-10-21
A Clonezilla livecd worked extremly well for me. I had an 80gig WinXP drive doing the "click of death" dance. Cloned it to a 160gig drive. Worked like a champ; booted XP without a hitch. I did not have to do any mbr repairs or grub/fstab/fdisk editing. I then used the gparted livecd to resize the 80gig partition to fill the 160gig drive. After cloning it would be wise to run a chkdsk/scandisk on a cloned Windows drive.
Clonezilla...
[http://clonezilla.org/](http://clonezilla.org/)
Go to the left side of the page; choose "Live CD/USB/PXE" then "How to use Clonezilla live" then click "step by step examples". Scroll down to "Disk to disk clone" and click "Description: clone small disk to larger disk" for instructions.

---

### Post by PhilWig on 2009-10-21
thanks all - will try clonezilla - I have that on a pmagic cd.
Phil

---

