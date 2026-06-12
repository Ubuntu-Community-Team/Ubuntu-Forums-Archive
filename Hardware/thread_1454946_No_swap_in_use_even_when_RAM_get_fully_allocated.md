---
title: "No swap in use even when RAM get fully allocated"
date: 2010-04-15
forum: Hardware
---

### Post by Azyx on 2010-04-15
Hi.
I have system-monitor applet and kan follow CPU acyivity, RAM use, network, system load, swap and disj.

I have 1,7GB RAM to system, (0,3 to the grafic-card) and I have 2GB disk to awap,
When i run the flash-game FarmVille a lot of RAM get filled up, and if I run a long time and work much, my RAM get totally used by application (not only as cache and the desktop freeze, totally, so I have to ctrl+alt+F1 to open a terminal and start top and kill mozilla and then go back and open mozilla again.

What I now notice is that the swap don't at all are in use!!! and I think that can be the reason to why the desktop freeze.

I don't remember If I sometime turned of the swap or so...but I have no idea where I maybe turn it of.

I running Ubuntu 8.04 LTS

Thanks for any help 

/Cheers

---

### Post by louieb on 2010-04-15
1st make sure swap is allocated and ready for use. Post the output of 
```
free -m 
```

---

### Post by Azyx on 2010-04-15
> **louieb said:**
> 1st make sure swap is allocated and ready for use. Post the output of 
```
free -m 
```

Fist: when I run :
Azyx@intel:~$ swapon -s there is no outcome

and the outcome from free -m is:

             total       used       free     shared    buffers     cached
Mem:          1772       1202        570          0         16        265
-/+ buffers/cache:        920        851
Swap:            0          0          0

So the swap is tuned of. (can also have happen when i downgrade from 8.10 cos hardare problems..

I have an swap-partition when I look in Gparted.

---

### Post by Azyx on 2010-04-15
> **louieb said:**
> 1st make sure swap is allocated and ready for use. Post the output of 
```
free -m 
```

I saw a swapon thing in Gparted (It was off) and activated the swap there. And now I get the outcome:

 free -m
             total       used       free     shared    buffers     cached
Mem:          1772       1222        549          0         17        266
-/+ buffers/cache:        938        834
Swap:         2047          0       2047

PS. How do i wrap CODE?

---

### Post by louieb on 2010-04-15
Swap is not being turn on automatically. That is controlled  by file **/etc/fstab **

Need 3 things : 

```
sudo fdisk -l
sudo blkid -c /dev/null

```and a listing of file /etc/fstab

Code tags are created by pressing the #  (make sure your Ubuntu forums profile is set to use the advanced editor).

---

### Post by Azyx on 2010-04-15
It's little desturbing...
I don't have any swap in fstab. I don't know why..Can it be cos I have during installation maked a primary partition and not an logical? I don't find any mount-point ether in Gparted.

When I look at fstab on another computer I found something like his:

# swap was on /dev/sda5 during installation
UUID=76733465-aeb3-40dc-ba16-5526979e86c0 none            swap    sw              0       0

Can I use /dev/sda5 instead of UUID=76733465-aeb3-40dc-ba16-5526979e86c0 in fstab, or how do I find that long partition UUID for my partition? (I his computer It's sda1 but i take this as an example)

PS. I still not manage to aktivate Bold (B), Italic (I)  or CODE (#) in this forum.Nothing happent when I maked the text and click on symbols up when I reply,

---

### Post by louieb on 2010-04-15
you find the UUID with the blkid command.

and yes you can use /dev/sda5 or what ever your swap partition is. 

I've used both - the UUID is better if you ever want to add another hdd. 

You are correct - select the text you want to bold or put in a code block before pressing the button - don't know why it not working for you.

---

### Post by Azyx on 2010-04-15
> **louieb said:**
> you find the UUID with the blkid command.

and yes you can use /dev/sda5 or what ever your swap partition is. 

I've used both - the UUID is better if you ever want to add another hdd. 

You are correct - select the text you want to bold or put in a code block before pressing the button - don't know why it not working for you.

So UUID is not only there to complicate things ;)

Now I get this:

```
Azyx@intel:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda1                               partition    2096440    0    -1
Azyx@intel:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1772        976        796          0         24        452
-/+ buffers/cache:        498       1273
Swap:         2047          0       2047
```

On the page: [HTML]http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space[/HTML]

They say that fstab shuold look like this:

```
/swapfile none swap sw 0 0
```

but on Ubuntu 9,04 fstab looks like this:

```
UUID=76733465-aeb3-40dc-ba16-5526979e86c0 none            swap    sw              0       0
```

The row don't beguinn with /swap

Will see how it should be on Ubuntu 8.04. I have not still manage to fill up the RAM becourse I reboot.

Cheers and thank for all help :)

PS. It seems like a problem with mozilla cos it work with Chrome with code and stuff. I run mozilla 3.6 on Ubuntu 8.04.. maybe the backporting don't fully work?

---

### Post by Azyx on 2010-04-15
It worked :)
When I came up to above 90% RAM-use the swap-space begin to be used :)

Thanx again. I'm  little unused to trix with terminal and so cos Ubuntu almost always just work :) I have not have need for more virtual memory until I begin to play that f*ckn FarmVille ;) that really eat memory..

---

### Post by m0nstersnatch on 2011-02-04
Hello, 

I think I have a similar problem. I have 4GB RAM but the system performs poorly and now that I have read your post I think it has something to do with the swap.

> /etc/fstab
# / was on /dev/sda1 during installation
UUID=2ac2d1b6-6b1c-44e1-ae8f-44a5616217d1  /                ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda2 during installation
UUID=2b145d3d-df5f-4779-bab0-2e033dc0c604  none             swap         sw                          0  0  
/mnt/512Mb.swap                            none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0   auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda3                                  /media/MRBIG     ext4         users,user                  0  2> sudo blkid -c /dev/null
/dev/sda1: UUID="2ac2d1b6-6b1c-44e1-ae8f-44a5616217d1" TYPE="ext4" 
/dev/sda2: UUID="2b145d3d-df5f-4779-bab0-2e033dc0c604" TYPE="swap" 
/dev/sda3: LABEL="MRBIG" UUID="0586fac1-aa46-4b26-a19e-436b577521f0" TYPE="ext4"> sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2745    22049181   83  Linux
/dev/sda2            2746        3060     2530237+  82  Linux swap / Solaris
/dev/sda3            3061       38913   287989222+  83  Linux> free -l
             total       used       free     shared    buffers     cached
Mem:       3614012    1796944    1817068          0      28668    1239988
Low:        853876     147476     706400
High:      2760136    1649468    1110668
-/+ buffers/cache:     528288    3085724
Swap:      3054508          0    3054508As you can see the swap is not beeing used, but there is a /mnt/512Mb.swap which I cannot recall making. What is this all about ?

Thanks !

---

### Post by Azyx on 2011-02-04
> **m0nstersnatch said:**
> Hello, 

I think I have a similar problem. I have 4GB RAM but the system performs poorly and now that I have read your post I think it has something to do with the swap.

As you can see the swap is not beeing used, but there is a /mnt/512Mb.swap which I cannot recall making. What is this all about ?

Thanks !


```
free -l
             total       used [COLOR=Red]      free[/COLOR]     shared    buffers     cached
Mem:       3614012    [COLOR=Black]1796944[/COLOR]    [COLOR=Red]1817068[/COLOR]          0      28668    1239988
```

Seems that you have [COLOR=Red]1817068[/COLOR] byte free in RAM, so there are no need to start use the slower  swap-memory i think? Open up a lot of web-pages so you use up all RAM and see if the swap start to be used. 
/Cheers

---

### Post by grahammechanical on 2011-02-04
Hi m0stersnatch

Regarding this comment of yours

>  but there is a /mnt/512Mb.swap which I cannot recall making. What is this all about ?

The installation process created this swap partition. The size can be changed but you are not given the choice of doing without one.

Regards.

---

