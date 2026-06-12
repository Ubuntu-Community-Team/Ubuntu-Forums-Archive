---
title: "[SOLVED] New SATA DVD Drive has wrong permissions and owner"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by pm124493 on 2007-11-28
I replaced my Plextor SA-712A SATA DVD drive with a new LG GSA-H62A SATA DVD drive. If I place a CD in the drive the system opens a window to display the contents, but then says I do not have permission to open the device. Now everything worked fine with the Plextor. I did notice that CDROM0 in the /media folder has the wrong group.

lrwxrwxrwx  1 root    root       6 2007-10-18 08:49 cdrom -> cdrom0
drwx------  3     400     401 2048 2005-10-07 01:28 cdrom0

cdrom0 should have root root as the owner. I can not fine a GROUP call 400 or 401.

I tried: "sudo chown root:root cdrom0 from the media directory, but it did not work. No error message and it did not change the ownership.

I took the Plextor SATA DVD drive an put it in my other system and it works fine. It replaced an older PATA DVDROM drive. It shows cdrom0 with root root.

The LG is in my UBUNTU 7.10_x64 system and the PLEXTOR went into my KUBUNTU 7.10_x64 system.

Can anyone help me get the ownership of the /media/cdrom0 corrected?

Thanks in advance.

---

### Post by crouton on 2007-11-29
Did you have anything in the drive (e.g. mounted CD/DVD) when you attempted the chown?  Try it without anything mounted.  Investigating what user '400' and group '401' are might help as well.  

For what it's worth, I have a BENQ IDE DW1620 and it shows (with DVD mounted):
 dr-xr-xr-x 1 root root 4096

---

### Post by pm124493 on 2007-11-29
Turns out the issue was with the CD I was trying to view. It was CD2 of COD2. Linux can't seem to view this CD. If I insert CD1 or another CD not part of COD2 it works.
My apologies. I have never seen this before. Thanks to everyone for their assistance.

---

