---
title: "dvd burner not reading"
date: 2008-10-30
forum: Hardware
---

### Post by nolimit974 on 2008-10-30
It seems that my cdrom doesn't read any disk nor can i burn anything.  When i try to burn something it doesn't detect a blank disk.  I can't manually mount the drive either.  I know it is in the software because I can boot from the cdrom but after I load ubuntu nothing is able to access it or read from it.

---

### Post by JMorg on 2008-10-30
If i'm not mistaken, much like how the windows operating system has an "uppers and lowers" filter located in its registry, I think that Linux does as well. The way to correct the issue within windows is to basically reset the filters, but locating them in linux can be a different beast. I will try and see what I can figure out for ya.

---

### Post by 080829k on 2008-10-30
.&#23545;&#20110;&#65292;&#20854;&#20182;&#20844;&#21496;&#30340;&#22823;&#23567;&#38050;&#32467;&#26500;&#20214;&#25110;&#20572;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#36710;&#35774;&#22791;&#20135;&#21697;&#65292;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#25105;&#20844;&#21496;&#21487;&#20195;&#20026;&#29983;&#20135;&#12289;&#21046;&#36896;&#12289;&#23433;&#35013;&#12289;&#32500;&#20462;&#12290;&#21319;&#38477;&#27178;&#31227;&#31867;&#30340;&#20572;&#36710;&#35774;&#22791;&#65292;[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#25105;&#20844;&#21496;&#24050;&#23558;&#35813;&#20135;&#21697;&#26631;&#20934;&#21270;&#65292;&#27169;&#22359;&#21270;&#65292;&#23454;&#26045;&#22823;&#37327;&#29983;&#20135;&#65292;[&#31435;&#20307;&#36710;&#24211;](http://www.bjbcl.com/neiye.htm)&#20197;&#19968;&#27969;&#30340;&#36136;&#37327;&#26631;&#20934;&#65292;&#21512;&#29702;&#30340;&#20379;&#36135;&#20215;&#20301;**&#65292;**[**&#31435;&#20307;&#36710;&#24211;**](http://www.bjbcl.com/neiye.htm)&#25552;&#20379;&#32473;&#25152;&#26377;&#31435;&#20307;&#20572;&#36710;&#35774;&#22791;&#20844;&#21496;&#12290;

---

### Post by kevomeister11 on 2008-10-31
I encountered the same problem :mad:

upgraded to 8.10 from 8.04 lts on my compaq presarion v2000

searched and searched for a solution, but nothing came up.:confused:

I downloaded the 8.10 iso, burned it to a dvd and just ran a fresh install 

It works perfect now!!:)

so i would suggest backing up any data you don't want to lose and just run a fresh install of whatever release you are using.

---

### Post by Firestone on 2008-10-31
I seem to have the same problem after upgrading to 8.10. My second device, 1st is blu-ray player, isn't being detected.
My fstab is unchanged after the update:
```

# CD/DVD-drives
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

But only one blockdevice is detected:
```

~$ ls /dev/scd*
/dev/scd0

```

dmesg only gives the blu-ray(right?):
```

[   22.099337] scsi 3:0:0:0: CD-ROM            BDROM    4X12X32X         CA32 PQ: 0 ANSI: 5
[   22.585209] sr0: scsi3-mmc drive: 1x/1x cd/rw xa/form2 cdda tray
[   22.585213] Uniform CD-ROM driver Revision: 3.20
[   22.585286] sr 3:0:0:0: Attached scsi CD-ROM sr0

```

Anyone have an idea besides a clean install?

---

### Post by nolimit974 on 2008-10-31
well i guess i can just back up my data and upgrade to 8.04 then.

---

### Post by forceflow307 on 2008-10-31
I'm having the same issue with the 8.10 release. I installed from CD earlier today, and it hasn't worked since the install. The drive is not being detected by the system, doesn't show up in Computer, doesn't appear in any hardware information tools, and dmesg doesn't have anything about it. Very odd. There is however an fstab entry for a non-existant /dev/sdc0 though, so I'm pretty sure it saw the drive at some point, probably during the install.:P Any ideas on this? Not quite sure what to try next

This is the model of drive I have: LITE-ON 20X DVD±R DVD Burner Black IDE Model DH-20A4P-04

---

### Post by forceflow307 on 2008-10-31
My bad, figured out what was wrong. My DVD drive was set as a slave, which had been working under 8.04. I decided on a hunch to try switching it to master and voila, problem solved. Probably isn't what was causing your guys' problems but it fixed mine.

---

### Post by nolimit974 on 2008-11-01
maybe I should try that on my master ide i have my main hard drive set to master and my dvd burner to slave.  I think i will put my cdrom on secondary ide as master and my storage drive as slave.

---

### Post by nolimit974 on 2008-11-02
Well I have upgraded to 8.10 and now everything seems to work fine.

---

