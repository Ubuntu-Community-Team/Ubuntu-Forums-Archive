---
title: "No Partitions During Install"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by epic1856 on 2009-09-13
Yes I am a n00b at this. First time installing any type of ubuntu. Downloaded .iso from xubuntu site and burned image onto a cd. 

Have:
Sony Vaio
1.5 GHz Pentium 4
512 mb ram
640 GB HD

I am not getting any info in step 4 "Prepare Partition". I can't continue because its asks for a "root file system".  Any idea how I can fix this partition issue? 

The hard drive is new with no OS on it. This is a fresh install of Xubuntu.

---

### Post by Bartender on 2009-09-13
I read an interesting article recently that measured RAM usage between Ubuntu, Xubuntu, and Lubuntu.
[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

From his results, Xubuntu actually took more resources than Ubuntu!  I've seen this no root file problem with Xubuntu, then Ubuntu would install just fine.

So, one option might be to try an Ubuntu install CD.  

Another option might be to download latest stable version of GParted LiveCD (link below) and make an image from the download.  Boot from GParted LiveCD.  It _should_ let you format the HDD as ext3 or ext4.  Then you could try the Xubuntu CD again.

---

### Post by raymondh on 2009-09-13
> **bartender said:**
> 

so, one option might be to try an ubuntu install cd.  


+1 ....

---

### Post by epic1856 on 2009-09-13
> **Bartender said:**
> 
So, one option might be to try an Ubuntu install CD.  


I'll give it a shot. I'm trying to do this [http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/) I noticed in ubuntu there is the desktop version and server version. Should I get the server version?Also using the ubuntu instead of xubuntu, will there be any differences from the instructions?

Thanks for the replies.

---

### Post by katakaio on 2009-09-13
Two things that might help: first, have you verified the MD5 checksum after downloading the Xubuntu ISO? That might tell you if the image was corrupted in any way.

The second thing is that I would highly recommend using the Ubuntu server disc for a server installation. You can always install a GUI after the server is set up. I personally like using [Fluxbox]("http://www.fluxbox.org/") for servers that require a GUI, but you can use whatever GUI you like - including XFCE, which is the Xubuntu interface.

Have fun! If you have any server questions, feel free to consult the [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html") or hop on IRC with the Ubuntu Server Team. Good luck!

---

### Post by epic1856 on 2009-09-14
](*,) 

Figured out its not the software thats the problem.  Looks like its either the new hard drive or the IDE to SATA adapter that is not working. 

Guess I'm heading back to Fry's. 

Hardware I bought:
[http://www.cooldrives.com/sata-drive-to-ide-converter-mini.html](http://www.cooldrives.com/sata-drive-to-ide-converter-mini.html)

[http://www.frys.com/product/5947264?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/5947264?site=sr:SEARCH:MAIN_RSLT_PG)

---

