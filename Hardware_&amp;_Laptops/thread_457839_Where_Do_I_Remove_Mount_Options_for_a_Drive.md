---
title: "Where Do I Remove Mount Options for a Drive?"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by patrick728 on 2007-05-29
I added "rw" to the mount options of my external FireWire drive by right-clicking on the drive on the desktop, going to the Volume tab, and expanding the Settings section. I restarted my computer for the changes to take effect and got an error that the mount options were invalid. Now the volume doesn't show up on the desktop so I can't right-click on it to remove the "rw" I typed in. I can manually mount the volume in terminal and access files there, but can't get it on the desktop.

Any suggestions as to where that setting got saved so I can remove it and get my drive back on the desktop?

---

### Post by blackened on 2007-05-29
Have you looked in /etc/fstab?

---

### Post by patrick728 on 2007-05-29
Hello,

That particular drive is not listed in the fstab file. Everything else is, of course.

--Patrick

---

### Post by dogskull on 2007-06-03
Same problem with a SD card drive.  Changed the options and cannot remount the drive.  Help would be appreciated.  It is not listed in fstab.

---

### Post by blackened on 2007-06-03
OP: How are you remounting the drive? If you are able to mount it via the commandline, then mount it as a subdirectory of /media and it will show up on the desktop. You should be able to change the read/write settings there.

---

### Post by dogskull on 2007-06-03
When I reinsert the card it automatically tries and fails to mount.  What should I do at that point to remount it?  Sorry, Linux noob.

---

### Post by grengren on 2008-05-02
hi. i've had the same problem.
try to use Storage Device Manager to configure mounting options. somehow it disables bad parameters in drive properties.

---

