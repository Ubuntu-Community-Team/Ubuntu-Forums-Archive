---
title: "HHD Failing?"
date: 2010-11-23
forum: Hardware
---

### Post by joibjorn on 2010-11-23
Hi.
The HHD tool on Ubuntu tells me that my HHD ATA ST3500630AS is failing because of too many bad sectors. Gonna attach screen dump of the error message. (File-system is in Norwegian)

My questions is as follows: 
Is this HHD soon dead?
Is it any way to save it?

It's fully possible to read/write to this disk, i successfully manage to back up the drive, so if i have to buy myself a new one, it wont be a problem:)

---

### Post by sikander3786 on 2010-11-23
Hi.

There have been some false positive reports reported earlier on the fourms so if you don't see any problem with accessing/writing data, the first thing I would suggest is to download the diagnostic tools from manufacturer's website and scan your HDD by using them.

If they also report that you've got some (or more :-) ) bad sectors, you definitely need to backup your data as soon as possible.

But first make sure if the bad sectors really do exist.

---

### Post by warfacegod on 2010-11-23
False positives have been a bug with Palimpset since it was introduced in, I believe, 9.04. I generally use gsmartcontrol and get rid of Palimpset.

---

### Post by joibjorn on 2010-11-23
the diagnostic tools from manufacturer's website is only for Mac and Windows. Can i run it in Ubuntu using wine? [http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatools-win&vgnextoid=552bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatools-win&vgnextoid=552bd20cacdec010VgnVCM100000dd04090aRCRD)

But when i boot the computer a autodetectprogram (American megatrends) runs, and checks all the drives. Master 4 -ATA ST3500630AS Status: BAD, but all the other disk is OK. 
I got backup of all the data, but is it possible to save the drive? 500 GB is alot of space i would like to use.

---

### Post by sikander3786 on 2010-11-23
Go terminal and see the man page for badblocks and then use it to check your disks for bad sectors.

```
man badblocks
```

However if the Bios Utility is also telling that the hard disk has got bad sectors, you really need to worry. It might not just be a false positive report by palimpset.

And the bad sectors are something related to Hardware and not the software so that is not curable at all. The only way around is to mark them bad in an OS so that OS doesn't try to write to them. But you'll need to mark them again if you reinstall the OS.

And you need to keep an eye on them as they might keep on growing.

This web is also worth reading.

[http://www.fix-hdd-bad-sectors.com/](http://www.fix-hdd-bad-sectors.com/)

---

### Post by warfacegod on 2010-11-23
> **joibjorn said:**
> the diagnostic tools from manufacturer's website is only for Mac and Windows. Can i run it in Ubuntu using wine? [http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatools-win&vgnextoid=552bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=seatools-win&vgnextoid=552bd20cacdec010VgnVCM100000dd04090aRCRD)

But when i boot the computer a autodetectprogram (American megatrends) runs, and checks all the drives. Master 4 -ATA ST3500630AS Status: BAD, but all the other disk is OK. 
I got backup of all the data, but is it possible to save the drive? 500 GB is alot of space i would like to use.

Possibly could work with wine but I doubt it would work very well.

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

### Post by joibjorn on 2010-11-24
Thanks guys. The seagate software doenst work with wine, but i am gonna go with the easy solution. Just ordered a new HHD :D Thank you again for the responses :D

---

