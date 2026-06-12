---
title: "openMosix 2.6 setup"
date: 2005-11-30
forum: General Help
---

### Post by Kosvarnin on 2005-11-30
I am in the process of setting up a cluster using Kubuntu 5.10

I have the Master setup with the KDE 3.5 GUI and the 2 Slaves are setup with the basic server install. They all can talk to each other and out through the Master for updates. My problem is getting openMosix installed and setup. I have seen some posts about openMosix but they were about 2.4 not 2.6. Furthermore, I need it broken down as I am still in the novice level of this. One post suggested adding the unstable lines to the sources.list, but I cannot find where those lines are. So does anyone out there know how to set this up. I have read the 4 posts found via a search "openMosix". Thanks for the help in advance.

---

### Post by flandercan on 2005-11-30
Did you ever get it working ? Do you have a how to I could follow ?


Paul

---

### Post by Kosvarnin on 2005-12-01
Nah, still trying to get it up. Wish I could get some help with this!

---

### Post by Kosvarnin on 2006-01-17
Okay, I have gotten to a point where I have patched the kernel and compiled it, but my problem is the install of the DEB package. I get the following error below:
-------------------Start of Error----------------------
(Reading database ... 22770 files and directories currently installed.)
Preparing to replace kernel-image-2.6.12 m01 (using kernel-image-2.6.12_m01_i386.deb) ...
D000001: process_archive oldversionstatus=broken due to postinst failure
Unpacking replacement kernel-image-2.6.12 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/vmlinuz-2.6.12
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

D000001: process_archive updating info directory
Setting up kernel-image-2.6.12 (m01) ...
D000001: deferred_configure updating conffiles
Cannot find /lib/modules/2.6.12
Failed to create initrd image.
dpkg: error processing kernel-image-2.6.12 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kernel-image-2.6.12

----------------------End of error-----------------------------

Note I can get more length error info if the need arises. I only did the install with Debug=1 which is just the general info.

---

### Post by joebaker on 2007-02-13
Can we get OpenMosix into Feisty 7.04?  It is an amazing way to do SMP processing across many computers.  If there is a kernel patch it would be great if it would be an installable module to the main Ubuntu kernel.

-Joe Baker
Burlington, Wisconsin; USA

---

### Post by tutomlin on 2007-04-05
I was put off of OpenMosix because of their website that says that 2.6 support is in alpha and I've really only been using linux consistently for about 4 months.  Is this something that's doable for someone with fairly low level skills? (I'm comfortable with the command line and have played around with a gentoo install but sadly my knowledge of kernel compilation really only extends to the tutorials I can find)

Also: My understanding was that openMosix wasn't true SMP in the sense that a SMP enabled program couldn't run spread across the network, even though individual programs could migrate happily from one system to another (which is pretty cool anyway).

if OpenMosix does do this I'll have to get off my lazy fanny and get to it.  :)

Cheers  :)

---

