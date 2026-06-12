---
title: "[SOLVED] Problem with wubo"
date: 2008-10-22
forum: General Help
---

### Post by Fr33z0n3 on 2008-10-22
Wubi seems very interesting, so I decided to try it out. But what happened - it downloaded the installation, restarted and nothing... Windows started but the installation didn't continue... I reinstalled it but again - nothing... I'm with windows XP SP2. 

I'm sure I've done something wrong but I don't know what :(
Please help I really want ubuntu.

Sorry for the typo in the title - I meant 'Wubi'

(sorry about my bad language - English isn't my native)

---

### Post by Orlsend on 2008-10-22
In windows are you the admin user?

---

### Post by Fr33z0n3 on 2008-10-22
Of course I'm the computer's administrator! I'm not so stupid ;)

---

### Post by Orlsend on 2008-10-22
do you have any Ubuntu files or folders in you hardrive? if so copuld you post them here?

---

### Post by Fr33z0n3 on 2008-10-22
I've never tried ubuntu before, but I've found that I've downloaded before an .ISO file of ubuntu 8.04.1
And there are the ubuntu files downloaded by wubi located in C:\ubuntu (Its size is 8.20Gb). The folders inside are 'disks', 'docs', 'install', 'winboot'. I think you know what is inside them. 

If ubuntu was installed properly there, why I can't select to boot up ubuntu - in the bootup menu I can choose only Windows Xp ...

---

### Post by ago on 2008-10-23
Check that you have an ubuntu entry in c:\boot.ini

---

### Post by Fr33z0n3 on 2008-10-23
Huh I haven't noticed that I don't have this file! (I turned of hiding windows system files but still I can find it)
Every time I turn on my computer it says 'invalid c:\boot.ini' but always windows starts...(I don't know how but it does) and I thought it was 'normal'...

This must be the problem so can somebody tell me how to fix it :confused:

---

### Post by ago on 2008-10-23
> **Fr33z0n3 said:**
> Huh I haven't noticed that I don't have this file! (I turned of hiding windows system files but still I can find it)
Every time I turn on my computer it says 'invalid c:\boot.ini' but always windows starts...(I don't know how but it does) and I thought it was 'normal'...

This must be the problem so can somebody tell me how to fix it :confused:

Yes that is the reason. You have to create a new one, it's just a text file. Note also that boot.ini might be hidden.

```

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect
c:\wubildr.mbr="Ubuntu"

```

The 0 and 1 might change according to the disk/partition where you have installed windows.

---

### Post by Fr33z0n3 on 2008-10-23
Thank you! Everything s working just perfect!

---

