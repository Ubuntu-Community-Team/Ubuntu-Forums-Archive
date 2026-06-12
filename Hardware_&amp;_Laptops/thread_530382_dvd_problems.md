---
title: "dvd problems"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by peterthewolf on 2007-08-20
Whenever I format or erase a dvd with Brasero it completes the job but ubuntu cannot mount the blank dvd.
If I mount via root then I get this
    mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg gives the following
      peter@peter-desktop:~$ dmesg | tail
[ 6033.232000] UDF-fs: No partition found (1)
[ 6033.644000] Unable to identify CD-ROM format.
[ 6090.436000] UDF-fs: No partition found (1)
[ 6090.844000] Unable to identify CD-ROM format.
[ 6688.480000] udf: bad mount option "0" or missing value
[ 6713.308000] udf: bad mount option "0" or missing value
[ 6740.180000] UDF-fs: No partition found (1)
[ 6740.500000] Unable to identify CD-ROM format.
[ 6791.436000] UDF-fs: No partition found (1)
[ 6791.768000] Unable to identify CD-ROM format.

---

### Post by Ux64 on 2007-11-26
Check this out...

[http://ubuntuforums.org/showthread.php?t=129093&highlight=udf+support](http://ubuntuforums.org/showthread.php?t=129093&highlight=udf+support)

Blank disk isn't formatted one. Even dvd+rw-format gives kind of impression of "formatting" disk.

---

