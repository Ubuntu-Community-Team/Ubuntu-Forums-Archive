---
title: "Trying to Connect Panasonic GH3, Not Going Well"
date: 2016-06-29
forum: Hardware
---

### Post by ChrisC098 on 2016-06-29
Hello.  I am running Ubuntu 15.10 and have a Panasonic GH3 DSLR that I would like to connect to my computer. At first I was giving me an issue about not read Exfat file system. Googled and found this page([http://askubuntu.com/questions/667475/cant-read-sd-card-in-digital-camera-but-can-read-the-card-in-cardreader](http://askubuntu.com/questions/667475/cant-read-sd-card-in-digital-camera-but-can-read-the-card-in-cardreader)) I tried both and it didn't work. I couldn't do the first one as chmod 777 gave me a operation not permitted. It has changed the error to:

Error mounting /dev/sdb1 at /media/chris/1548-F934: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/chris/1548-F934"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.1.0
'
stderr: `ERROR: file system is larger than underlying device: 64071139328 > 64071138816.
'

Any help would be greatly appreciated. Thank you.

Edit: Also, how sketchy is this site? [http://ubuntuapk.com/APK_Panasonic-Lumix-GH3-QuickPro_Ubuntu.html](http://ubuntuapk.com/APK_Panasonic-Lumix-GH3-QuickPro_Ubuntu.html)

---

