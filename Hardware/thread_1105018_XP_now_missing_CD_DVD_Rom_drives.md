---
title: "XP now missing CD DVD Rom drives"
date: 2009-03-24
forum: Hardware
---

### Post by viperxl2 on 2009-03-24
I've read the assortment of choices for where to post this and wasn't sure so move please if in the wrong place.  On to the problem I've been experiencing.

Just a few days ago when going into my XP side of my HDD I downloaded a program to remove the Ubuntu partion of my HDD.  After that I had an issue with the GRUB error 22 and removed it with the "FDISK /MBR" command under a MS-DOS disk.  After being able to log back into my XP side I notice that my DVD and CD Rom drives where missing.  I've checked my device manager and everything.  I've removed IDE drivers and reinstalled them and ran hardware scans.  Most didn't pick up my drives but one in particular said they were "DISABLED" which I thought was odd.  I've checked my BIOS settings of my PC and restored all of them to the factory defaults and still no go.  I've done almost everything I know possible to get these things back up and running.  Please help, any help would be fully appreciated.:popcorn:

---

### Post by KCG102282 on 2009-03-24
Just eneable them in the Device Manager.

---

### Post by viperxl2 on 2009-03-24
well I can't.  which is odd because they wont show up in either the BIOS nor the Device Manager.

---

### Post by viperxl2 on 2009-03-25
Ok I fixed it.  For some odd unapparent reason when I uninstalled Ubuntu it caused my CD/DVD drives to completely disappear.  I took them out the chassis and checked the pins for "Master" and "Slave" and incorrectly set them.  After that a no go.  So after doing that I just set them back the way the were before and everything just magically worked fine.  Not sure what went on but at least my problem no longer exist.

---

