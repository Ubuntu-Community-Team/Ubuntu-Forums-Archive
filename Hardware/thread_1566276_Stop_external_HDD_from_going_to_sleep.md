---
title: "Stop external HDD from going to sleep"
date: 2010-09-02
forum: Hardware
---

### Post by Ghost_Mazal on 2010-09-02
Lo guys ,
 
I have an external USB 1.5TB Seagate Freeagent hard drive where all my media is stores. But the drive keep on going to sleep and shuts down if there is no activity on it.
Everytime I want to access it I have to wait for it to start spinning up first before I can use it. Is there a way to stop it from going to sleep , shutting down ?
 
Thanx

---

### Post by scottku on 2010-10-24
I'm also wondering if there is a way to do this.  hdparm doesn't work with external USB drives.  I also tried changing the USB autosuspend settings in /sys and still didn't stop the drive from spinning down.  sg_start seems to let me set the disk to idle (or spin up), but it still seems to always spin down after being idle for a while.

I'm not sure how long the disk needs to be idle before it spins down, but it seems to be some amount of time less than 15 minutes.

Anybody have any ideas?

---

### Post by Ghost_Mazal on 2010-10-25
> **scottku said:**
> I'm also wondering if there is a way to do this.  hdparm doesn't work with external USB drives.  I also tried changing the USB autosuspend settings in /sys and still didn't stop the drive from spinning down.  sg_start seems to let me set the disk to idle (or spin up), but it still seems to always spin down after being idle for a while.

I'm not sure how long the disk needs to be idle before it spins down, but it seems to be some amount of time less than 15 minutes.

Anybody have any ideas?

This all worked hundred percent with my external :

"   	 	 	 	p { margin-bottom: 0.21cm; }  [COLOR=#000000][SIZE=2]**Re: Seatgate external USB HD goes to sleep**[/SIZE][/COLOR][COLOR=#000000][SIZE=2] [/SIZE][/COLOR] 
 

 [COLOR=#000000][SIZE=2]There's a lot of info out there about Seagate not playing nice with Linux because of this. What worked for me is to make sure the [/SIZE][/COLOR][COLOR=#ff0000][SIZE=2]**HDD**[/SIZE][/COLOR][COLOR=#000000][SIZE=2] is installed and awake. Then in a terminal type (this only works if you have sdparm installed. if not then go get it from the package manager or using apt-get):[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Code:[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=2]$ sudo fdisk -l[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Note the name of your external [/SIZE][/COLOR][COLOR=#ff0000][SIZE=2]**HDD**[/SIZE][/COLOR][COLOR=#000000][SIZE=2]. It should be something similar to "/dev/sdb"[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Code:[/SIZE][/COLOR]
  [COLOR=#000000][SIZE=2]$ sudo sdparm --clear STANDBY -6 /dev/sdb[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Where /dev/sdb is the appropriate name of your drive."[/SIZE][/COLOR]


[COLOR=#000000][SIZE=2]So in my case sdparm does work with externals
[/SIZE][/COLOR]

---

