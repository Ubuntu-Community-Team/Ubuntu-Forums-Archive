---
title: "Permission Denied to new internal hard drive"
date: 2009-01-07
forum: Hardware
---

### Post by wadhurstdaisy on 2009-01-07
Firstly, I am total new at Ubuntu so please be gentle with me !

Have installed 8.04 onto an old PC with the intention of using it as a headless networked music server. I am the only user.

All appeared to function well so I added an additional 400gb internal hard drive.

Formatted new 400gb using GParted 0.3.5 Partition editor into 2 drives of 262gb and 98gb both of which are FAT32 to allow older windows access.  These are identified as sdb1 and sdb2.

Then used Storage Device Manager to automatically mount sdb1 & sdb2 at boot-up.

At boot-up both sdb1 and sdb2 appear on 'desktop'.

Then attempted to transfer music files from external hard drive (connected via firewire) to sdb1 however error message of 'permission denied' appears.  This also happens with sdb2.

I have established that it is possible to transfer files from external drive to 'desktop' but error message of permission denied appears if I try to transfer from 'desktop' to sdb1 or sdb2.

Having searched this forum tried using Nautilus via terminal command 'gksudo nautilus' and this allows me to transfer files onto sdb1 and sdb2 however this is surely a fudge and that drag & drop should work.

Any help in gaining direct access to new internal hard drive will be much appreciated. Thanks.

---

### Post by logos34 on 2009-01-07
gksudo gedit /etc/fstab

try commenting (#) the entries made by psydm and replacing them:

> /dev/sdb1 /media/wherever vfat [COLOR="Red"]users,rw,owner,umask=000 0 0[/COLOR]

or 

> /dev/sdb1 /media/wherever vfat [COLOR="Red"]defaults,umask=0000 0 0[/COLOR]

or

> /dev/sdba1 /media/wherever vfat user,fmask=0111,dmask=0000 0 0

---

### Post by wadhurstdaisy on 2009-01-08
> **logos34 said:**
> gksudo gedit /etc/fstab

try commenting (#) the entries made by psydm and replacing them:



or 



or

Many thanks for the reply.  Have just tried it ( 1st option incidentally) and it worked :KS Thanks also for explaining what 'commenting' means.

If I understand correctly, the alteration you suggested amends the privilege rights for the specified volumes.

Having just looked at Storage Device Manager, I can see that the entries under 'options' have altered from default and that the 'mounting' sub-menu is likewise modified.

Could these amendments have been made directly into 'Storage Device Manager' and that you simply had a preference for terminal code?

Sorry for the question but, being a novice, I'm generally someone who operates using nice gui's rather than direct code so I'm just trying to understand why a particular method was used.

---

### Post by logos34 on 2009-01-08
yes, I suppose you could have simply edited the options line in the Storage manager but I wanted to be sure it was done right so I had you manually enter them using gedit.  So by all means use the gui if you prefer.

To 'comment' (out) a line simply means to put single or double hash marks (#) in front, which tells the program not to read it

good luck and mark thread as 'Solved' (->thread tools)

---

### Post by wadhurstdaisy on 2009-01-14
> **logos34 said:**
> yes, I suppose you could have simply edited the options line in the Storage manager but I wanted to be sure it was done right so I had you manually enter them using gedit.  So by all means use the gui if you prefer.

To 'comment' (out) a line simply means to put single or double hash marks (#) in front, which tells the program not to read it

good luck and mark thread as 'Solved' (->thread tools)
Many thanks ... thread tools doesn't provide an option of 'Solved', in fact none of the drop-downs do; is there any other way of closing the thread ?

---

### Post by logos34 on 2009-01-14
> **wadhurstdaisy said:**
> Many thanks ... thread tools doesn't provide an option of 'Solved', in fact none of the drop-downs do; is there any other way of closing the thread ?

last time I looked it was under thread tools...I'm not sure what's going on, the servers have been down, can't login properly when they're up...things are a mess!

---

