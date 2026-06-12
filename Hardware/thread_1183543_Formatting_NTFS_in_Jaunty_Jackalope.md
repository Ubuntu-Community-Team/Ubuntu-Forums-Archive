---
title: "Formatting NTFS in Jaunty Jackalope"
date: 2009-06-10
forum: Hardware
---

### Post by nengracia on 2009-06-10
I have a new external hard drive. I currently use Ubuntu 9.04 Jaunty on my desktop, and Vista on my laptop. I need to have access on this external drive on both OS.

When I was using Intrepid, Gparted "allows" formatting hard drives with the NTFS system. With Jaunty, this capability seems to be "grayed out".

Can somebody show me how I could format drives with the NTFS system?

---

### Post by Moop on 2009-06-10
Have you tried booting from a live cd and using gparted from there? I ran into the same problem but don't remember if I used a Ubuntu live cd or a gparted live cd.

---

### Post by nengracia on 2009-06-10
Done it - during installation, live Ubuntu CD, live Gparted CD; NTFS formatting option is not present or disabled (grayed out).

---

### Post by boof1988 on 2009-06-10
> **nengracia said:**
> Done it - during installation, live Ubuntu CD, live Gparted CD; NTFS formatting option is not present or disabled (grayed out).

Not sure... but maybe [GPartEd](http://gparted.sourceforge.net/) needs some extra file-system tool.

[ntfs-3g](https://help.ubuntu.com/community/MountingWindowsPartitions#For NTFS Partitions) (only provides read/write support) and is probably already installed.

When I looked at [GPartEd features](http://gparted.sourceforge.net/features.php), it seems you may need [*ntfsprogs*](http://en.wikipedia.org/wiki/Ntfsprogs), which can be installed...

1. Using [Synaptic-Package-Manager](http://en.wikipedia.org/wiki/Synaptic_package_manager).
2. Using [apt-get](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html) (in a terminal)...
```
sudo apt-get install ntfsprogs
```
3. Using any other favorite package installer.

Another option is...

1. Download the GPartEd CD-image (or other) at [Live CD/USB/PXE/HD](http://gparted.sourceforge.net/livecd.php).
2. Check the GPartEd Live CD [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and compare to the sums listed at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).
3. Burn the CD image to a disk and then boot to it.

---

### Post by nengracia on 2009-06-10
Hi boof1998,

Thanks for the info. Have downloaded ntfsprogs and it worked.

Thanks a lot.

---

### Post by boof1988 on 2009-06-10
> **nengracia said:**
> Hi boof1998,

Thanks for the info. Have downloaded ntfsprogs and it worked.

Thanks a lot.

Glad it worked for you :)

---

### Post by hxcjohn on 2009-06-20
Thanks! This helped me as well!

---

### Post by caue.rego on 2009-06-22
> **boof1988 said:**
> Not sure... but maybe [GPartEd](http://gparted.sourceforge.net/) needs some extra file-system tool.

[ntfs-3g](https://help.ubuntu.com/community/MountingWindowsPartitions#For NTFS Partitions) (only provides read/write support) and is probably already installed.

When I looked at [GPartEd features](http://gparted.sourceforge.net/features.php), it seems you may need [*ntfsprogs*](http://en.wikipedia.org/wiki/Ntfsprogs), which can be installed...

1. Using [Synaptic-Package-Manager](http://en.wikipedia.org/wiki/Synaptic_package_manager).
2. Using [apt-get](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html) (in a terminal)...
```
sudo apt-get install ntfsprogs
```
3. Using any other favorite package installer.

Another option is...

1. Download the GPartEd CD-image (or other) at [Live CD/USB/PXE/HD](http://gparted.sourceforge.net/livecd.php).
2. Check the GPartEd Live CD [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and compare to the sums listed at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).
3. Burn the CD image to a disk and then boot to it.

Jaunty liveCD itself already comes with gparted and ntfsprogs. It's just not installed by default, for some reason.

---

