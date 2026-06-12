---
title: "Wireless setup without connection"
date: 2010-09-28
forum: Hardware
---

### Post by OldManRiver on 2010-09-28
All,

Have 9.10 installed on Dell Inspiron 6000, but ran from CD and have no connection except wireless, and the wireless drivers did not download onto CD, therefore having issues.

Found the URL for download of the .deb file, the system wanted, some Broadcom driver, but a package inside this install asked for, via "wget" commands, two more files each from two seperate repositories on openWRT.

So I got these files.  Realizing that the install would not finish, but always error, I used copy and paste to rip the contents of the install script, in the download script file, creating my own bash script where I could point to the /home/files dir where I stored the files.

This script executed and said finished, but I still have no wireless connection, and since I do not have any connectability other than wireless, I'm at a loss of what to do next to get my laptop working.

Having to post this from another Win machine, where I do have connection.

Oh Yes the 3 files are:

[http://us.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1_i386.deb)
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Thanks!

OMR

---

### Post by OldManRiver on 2010-09-30
All,

Could use some help here.

OMR

---

### Post by OldManRiver on 2010-10-16
All,

At least respond with command line string I need to find the right hardware so I can determine if I got the right drivers or not.

Thanks!

OMR

---

### Post by OldManRiver on 2010-10-16
All,

Never mind it just came up.

Thanks!

OMR

---

