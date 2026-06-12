---
title: "[SOLVED] Think you can follow this???"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by buccaneere on 2007-12-06
Two new, empty laptops; Acer 5100/vista, and HP dv 9000/vista. All I need for this musical HDD's is music:guitar:

I pulled the HDD from the Acer, and set it aside. I took the *secondary* HDD from the HP (it has 2 HDD's), put it into the Acer, and loaded ubuntu, and made a hundred or so personal settings and hardware configurations.

I want now to transfer all settings to the original Acer HDD.

So I took the HP secondary out of the Acer, and put it in the PRIMARY bay of the HP, and put the original Acer into the SECONDARY bay of the HP. 

So now I can mirror the ubuntu settings onto the Acer original HDD, and then put it back into the Acer. Right?

Wrong. The HP won't boot the ubuntu-loaded HDD. It's cryin' about graphical interface not startin'.


So will this work:

Leave both HDD's as they are, and boot from ubuntu liveCD. Then, execute disk copy, from the primary disk, to the secondary disk.

Understand that? I don't either. I think it will go tho', huh?

---

### Post by Vadi on 2007-12-06
Wait, no. I think there's an easier way.

It's just that X is configured for the display on the other laptop, so when it's seeing a different one, it's going like "wth has happened?!". We can just reset X, and it should befriend the new monitor...

Do you / can you get to the console?

---

### Post by buccaneere on 2007-12-06
> **Vadi said:**
> Wait, no. I think there's an easier way.

It's just that X is configured for the display on the other laptop, so when it's seeing a different one, it's going like "wth has happened?!". We can just reset X, and it should befriend the new monitor...

Do you / can you get to the console?

Hi Vadi...

You must be pretty sharp to follow that story. 

Yeah, I'm with ya' on the display conflict. I can get into bios/setup; that's about it.

I have got the liveCD booted up, and fdisk returned both HDD's - the primary, partitioned,  with ubuntu, and the secondary, unpartitioned, and FAT32 format.

I think tgalati4 got me the right code for the copy execute...

[COLOR="Red"][I]Log into rescue mode.

[HTML]# cp /dev/sda /dev/sdb[/HTML]

This copies then entire device (sda) to another device (sdb). Partitions and everything copy over.

Edit your grub to point to sdb and boot and check around to make sure everything is in place.

This also works if the second drive is not partitioned/formatted. If partitioned, ...
[/I][/COLOR]

Exactly what is rescue mode tho'? Root user???

Thanks again there.................

---

### Post by chalewa on 2007-12-06
why not just run the command to reconfigure x?

---

### Post by buccaneere on 2007-12-06
> **chalewa said:**
> why not just run the command to reconfigure x?

Hi Chalewa...

Not sure how to do that. 

Would that still be easier than executing from live CD boot/load as above?

I haven't done anything yet; just logged in as root ...

---

### Post by PmDematagoda on 2007-12-06
Simply do:-
```

sudo dpkg-reconfigure xserver-xorg
```
in Recovery Mode and select the proper options that fit your PC.

After that is done do:-

```
startx
```
to start the GUI.

---

### Post by buccaneere on 2007-12-06
> **PmDematagoda said:**
> Simply do:-
```

sudo dpkg-reconfigure xserver-xorg
```
in Recovery Mode and select the proper options that fit your PC.

After that is done do:-

```
startx
```
to start the GUI.

Are you sure you understand what I'm tryin' to do? 

If I reconfigure the primary drive, the copied drive won't be configured to the Acer, will it?

---

### Post by chalewa on 2007-12-06
> **buccaneere said:**
> Two new, empty laptops; Acer 5100/vista, and HP dv 9000/vista. All I need for this musical HDD's is music:guitar:

I pulled the HDD from the Acer, and set it aside. I took the *secondary* HDD from the HP (it has 2 HDD's), put it into the Acer, and loaded ubuntu, and made a hundred or so personal settings and hardware configurations.

I want now to transfer all settings to the original Acer HDD.

So I took the HP secondary out of the Acer, and put it in the PRIMARY bay of the HP, and put the original Acer into the SECONDARY bay of the HP. 

So now I can mirror the ubuntu settings onto the Acer original HDD, and then put it back into the Acer. Right?

Wrong. The HP won't boot the ubuntu-loaded HDD. It's cryin' about graphical interface not startin'.


So will this work:

Leave both HDD's as they are, and boot from ubuntu liveCD. Then, execute disk copy, from the primary disk, to the secondary disk.

Understand that? I don't either. I think it will go tho', huh?


haha, I was gonna tell you to the same thing as the person above...but now lemme take a look at this again...


after reading that like three or four times, I think i got it.  the only thing that you did really was move a hard disc around right? you merely moved the secondary hd to the acer installed ubuntu on it, and then put it back in the primary slot on the HP right?

if that is the case, and you want to run ubuntu off it, but it is complaining about graphical errors, it is because when you installed ubuntu on that drive on the acer, the xserver was configured for the acer's graphics card and whatnot, not the HP's so to solve that problem you should just have to run 

```
sudo dpkg-reconfigure xserver-xorg
```

and then 

```
 startx
```

just like the man above said, if that is not the case...we can figure out a different solution

---

### Post by buccaneere on 2007-12-06
> **chalewa said:**
> haha, I was gonna tell you to the same thing as the person above...but now lemme take a look at this again...


after reading that like three or four times, I think i got it.  the only thing that you did really was move a hard disc around right? you merely moved the secondary hd to the acer installed ubuntu on it, and then put it back in the primary slot on the HP right?

if that is the case, and you want to run ubuntu off it, but it is complaining about graphical errors, it is because when you installed ubuntu on that drive on the acer, the xserver was configured for the acer's graphics card and whatnot, not the HP's so to solve that problem you should just have to run 

```
sudo dpkg-reconfigure xserver-xorg
```

and then 

```
 startx
```

just like the man above said, if that is not the case...we can figure out a different solution

No.

The objective is to copy the Acer setting onto the original Acer disk.

...and to do the copying ON THE HP, then remove and re-install the Acer HD.

Given that, is anything that you said for me to do correct?

EDIT: I just answered the question; you do NOT understand the task at hand. Thanks anyway.

---

### Post by buccaneere on 2007-12-07
I DID IT!!!

Leave both HDD's as they are, and boot from ubuntu liveCD. Then, execute disk copy, from the primary disk, to the secondary disk.

I think tgalati4 got me the right code for the copy execute...

Log into rescue mode.

HTML Code:

[HTML]cp /dev/sda /dev/sdb[/HTML]

Took about 50 minutes to execute, with no progress indicator... All of a sudden, a beep, I punched up fdisk -l, and VOILA! Replication.

Put it back into the Acer, and it's good to go!

---

