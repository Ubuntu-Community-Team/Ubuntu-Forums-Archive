---
title: "can't start system after adding usb hard drive"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by gowild00 on 2008-02-27
added a usb hard drive last night - went OK as was able to read and write fine - shut system down normally - this morning system won't boot properly - am told "home directory is /home/bob but that does not appear to exist - only changed fstab file last night to accommodate new hdd - not sure what to do as am still something of a newbie at this - any help appreciated needless to say!!

---

### Post by gowild00 on 2008-02-27
also, message says $HOME/.dmrc file is being ignored - it should be owned by user and have 644 permissions. USERS's home directory must be owned by user and not writable by other users

---

### Post by gowild00 on 2008-02-27
I figured out that the drive where /home resides hadn't been mounted and I'm not sure why - here is my /etc/fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=963c6213-ce64-4bbd-a679-52bb019a46e8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb1 :
/dev/sdb1   /home            ext3   defaults   0   2
# Entry for /dev/sda5 :
UUID=facc017e-6fc4-47d3-af21-8a8b6a347262 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
# Entry for USB drive
/dev/sdc1   /media/storage   ext3   defaults   0   1


any ideas on what to fix to automatically mount  /home as it was doing before I added the new drive (that drive is the last line)

---

