---
title: "Ghosting?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by ikehack on 2008-12-02
Is it possible to make a "ghost" image of my Ubuntu installation? That is, can I take my current installation of Ubuntu (themes, programs, documents and all) and move it to a new machine?

---

### Post by lemming465 on 2008-12-03
Yes, there are several ways to accomplish this.

* Norton Ghost can do ext2/3 partitions if you own a copy of that

* If you can temporarily get old and new disks into the same machine, there are partition copying tools you can use, either free ones such as GNU "parted" or commercial ones such as "partition magic".

* If the two machines are connected by a network, you can do a minimal install on the new one, use "dpkg --get-selections" on the old one to generate a list of the installed .deb files, use "dpgk --set-selections" followed by "apt-get upgrade" on the new host to install them all.  Then use "rsync" over "ssh" to copy data files, home directories, etc.

* boot a live CD on each host, start "nc -l -p 1234 | tar -xf -" on the new machine, do "tar cf - / | nc new.machine 1234" on the old one, and finish up with "chroot /mnt/whereever" and "grub-install /dev/sda"

Does anyone want to recommend still more scenarios?  If there is one you like but don't fully understand, ask for more details about it.

---

### Post by caljohnsmith on 2008-12-04
You could also check out Partimage in the Ubuntu repositories, or many people particularly like using [Clonezilla]("http://www.clonezilla.org"). Another option is to use Ubuntu's partition editor "gparted" (System > Admin > Partition Editor) from the Live CD to simply copy the entire Ubuntu partition from the source drive to the destination drive. As lemming465 alluded to though, you will have to install Grub to the MBR (Master Boot Record) of the destination drive if you simply copy/clone the Ubuntu partition, because copying/cloning the partition doesn't include the MBR. If you need specific help with any of that, let me know. Otherwise let us know how it goes. :)

---

### Post by arjay27529 on 2009-01-06
caljohnsmith

have just finished nearly a year of hardware and software problems - mostly related to windows.  now have a working machine with ubuntu/linux and have found a home.  concerned about hardware failures - specifically harddrives.  

so - after ghosting a drive - how do you copy grub to the mbr?
and - which is better to ghost to another drive or a cd?  or is there any difference?

---

### Post by caljohnsmith on 2009-01-06
> **arjay27529 said:**
> caljohnsmith

have just finished nearly a year of hardware and software problems - mostly related to windows.  now have a working machine with ubuntu/linux and have found a home.  concerned about hardware failures - specifically harddrives.  

so - after ghosting a drive - how do you copy grub to the mbr?
and - which is better to ghost to another drive or a cd?  or is there any difference?
You don't actually need to copy over Grub, you can install Grub to the MBR in a few short steps using this tutorial:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And about ghosting to a CD or drive, either should be OK, but if you do it to a CD you will have to split up your partition, assuming the partition is more than 700 MB.

---

