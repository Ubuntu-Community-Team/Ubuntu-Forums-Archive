---
title: "CD and DVD not working after Lucid Upgrade"
date: 2010-07-09
forum: Hardware
---

### Post by Flyboy712 on 2010-07-09
Hi my CD and DVD drives have quit working after upgrading from Karmic to Lucid.  Both drives are being recognized but when I insert a CD or DVD into them they just spin up and do nothing.  They were both working when I had Karmic.


Thanks,
Mike

---

### Post by Flyboy712 on 2010-07-10
Anyone??

---

### Post by Flyboy712 on 2010-07-14
Bump.

---

### Post by Flyboy712 on 2010-07-20
Hello anyone???  Can anyone offer any help whatsoever??  I have seen multiple threads on this so I know it is not a mystery problem there has to be a solution somewhere??

---

### Post by Flyboy712 on 2010-09-17
Anyone out there?????????

Seriously its been several months and nothing??!!

Here is the output of lshw -c disk:

*-cdrom:0               
       description: DVD reader
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio dvd
       configuration: status=open
  *-cdrom:1
       description: DVD-RAM writer
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open


I'm guessing configuration: status=open is the issue.  Does anyone know how to fix this??


Thanks,
Mike

---

### Post by jonny90046 on 2010-09-19
HI Mike....after an system update last night, I'm having the same problem....the output of lshw is pretty similar, except my output provides the drives product name HL-DT-ST DVDRAMGT30N and the last line, configuration, includes ansiversion=5 and my status is either busy or nodisc.  It's been working fine...I started the update, it was downloading the files very slowly, so I cancelled it...started to burn a file to disc.....and then this... I thought it was one of the lasers failing, and it might be, but after researching it today (for hours) it might be a driver issue.  The update included a kernel update from 2.6.32-24 to -25.  I compared the dmesg output for both, but they look about the same, too.  I just wanted you to know your not alone with this....when/if I find a solution, will post it asap....please, do the same.  take care....jonny

---

### Post by Flyboy712 on 2010-09-19
Thanks Jonny will do!!

Its really frustrating not having a functioning disc drive.

---

### Post by uRock on 2010-09-19
> **Flyboy712 said:**
> Hello anyone???  Can anyone offer any help whatsoever??  I have seen multiple threads on this so I know it is not a mystery problem there has to be a solution somewhere??
Did any of those threads list a fix?

Is your hardware showing in the dmesg log at all?

---

### Post by Flyboy712 on 2010-09-19
uRock,

Yes they are showing up in my dmesg log file.  I attached a copy check it out let me know what you think.

Also I remember I had issues with Grub when I did my upgrade and had to manually install it from the live CD after I did the upgrade because my computer wouldn't progress past post.  Do you think that this might also have something to do with it??

Thanks,
Mike

---

### Post by Flyboy712 on 2010-09-23
bump

---

### Post by Flyboy712 on 2010-09-23
OK so a little update on my status I think I may have gotten the drives working.  Here is what I did:

my fstab file did read like this:
#/dev/sr0 /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sr1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

and I changed it to read this:
#/dev/scd0 /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

I replaced /dev/sr0 with dev/scd0 reboot the computer and wallah they are working.

Hopefully it will stay this way I check back in in a few days and let you all know whats going on.

---

### Post by Flyboy712 on 2010-09-24
Well never mind my previous post.  Worked until I ejected the discs and waited about an hour then tried the same discs and nothing so back to square one again.  

Mike

---

### Post by Flyboy712 on 2010-10-03
Well just did a complete system reinstall and the same issue persists kind of.    If I boot with a disc in the drive they are recognized upon OS startup. I can open the content and run for about 5 min and then its not recognized any longer.  I can start a movie get a couple min into it and then it just stops.  After that cant open or mount any of the drives.  If I go to disk utility and mount them from there they will mount and show that they stay mounted but after a few minutes the system can no longer find or access them again.  Its almost as if the driver for them quits working all of a sudden.  Both drives are good and work on other systems and I can boot from both of them on this system.  Definitely disappointing for such a great operating system to have such poor support for hardware and poor support period.  

If anyone has anything at all please let me know.  I am waiting until Maverick is released to see if that will fix it and if not I will have to go somewhere else.

Thanks,
Mike

---

### Post by Flyboy712 on 2010-10-04
Bump again!?

---

### Post by Flyboy712 on 2010-10-06
Hey I think I just found a fix.  i installed the Maverick kernel and so far everything is working great.  I'll keep you all posted on what happens.

---

