---
title: "HELP - External HD is eating my CPU alive!"
date: 2008-08-22
forum: Hardware
---

### Post by Scavallo on 2008-08-22
I recently installed Hardy Heron on my Sony Vaio VGN-SZ280P laptop after messing around with Wubi (which is fantastic) for a good while. I am in no way, shape, or form an advanced or even an intermediate user however I've managed to configure my laptop fairly easily. Here's my sole problem:

After tweaking everything to my liking I decided to use a torrent program. I selected Deluge, installed it, set it up to write the downloaded files to one of my external HD's. I figured my Hardy Heron install was finally 100% complete.

So I mount my external HD, start up Deluge, and select a torrent. The speed was great (a big improvement over uTorrent in XP) and I thought everything was fine until I started to hear my fan pick up speed...and continue to pick up speed...until it was running as quickly as it could. I open up my system monitor (htop) and see that a process called

------>      /sbin/mount.ntfs-3g /dev/sdd1 /media/My Book -o rw,nosuid,nodev,uhelper=hal,locale=en_us.utf-8      <------

will consume upwards of** 80+% **of my CPU's capacity and sometimes **even higher**. 

Does anyone have any ideas on why this is consuming so much my CPU's resources.

Laptop-
Sony Vaio VGN-SZ280P
Hardy Heron 8.04
Kernal Linux 2.6.14-19-generic
GNOME 2.22.3
2gigs/memory
2x Intel T2500 @ 2gigs/each

HD- 
Western Digital 
My Book Essential Edition 500 GB
Reformatted from FAT32 to NTFS
(transferring data via USB 2.0)

My system runs right at 9% when running EVERY other program I use (Compiz, Screenlets, Firefox, etc.), but as soon as I start up Deluge and it begins transferring data I just run into a huge rut.

ANY help would be greatly appreciated. Since switching to Ubuntu full-on I have never thought about returning to XP, help me achieve total GNOME bliss...please:).

Thank you in advance,
Scavallo

P.S. I'm having minor surgery today, if anyone has any information requests I will reply as soon as possible to them.

---

### Post by Scavallo on 2008-08-22
Anyone...anyone...anyone?

---

### Post by cariboo on 2008-08-22
What command do you use to mount your external hdd. That process loks wrong some how it should look like:

```
mount ntfs-3g /dev/sdd1 /media/My Book -o rw,nosuid,nodev,uhelper=hal,locale=en_us.utf-8
```

That "." in there doesn't look right to me.

Jim

---

### Post by Scavallo on 2008-08-22
Jim,

Thank you for your reply.

I'm not currently using any command to mount the drive(s). I have the Western Digital 500 GB and a much newer Ex. HD, a Maxtor OneTouch 4 Plus 500 GB, each of which basically utilizes true plug-and-play connectivity (it's rather nice actually).  

In the screenshot attached here the WD HD is the program at the top. My computer has been running basically idle (except Deluge/WD HD) all day because of my surgery, and as you can see its just raping my CPU; the fan is still running at full throttle. I have a two cooling fans running underneath the computer constantly also, keeping it relatively chilly. Those Targus fans are the only reason I allow this madness to continue :). 

Also, out of curiosity I selected a torrent from one of my friends and changed the save location to my Maxtor drive to see what happened. Data can be saved to it completely fine (it does not even appear on my htop terminal).

The only difference between the two drives is the transfer method (WD=USB2, Maxtor=Firewire400/800). Any ideas?

I know the easy answer is just to stop saving torrent data to the WD and switch to the Maxtor, but the WD is old, nearly full, and very unorganized, and the Maxtor still has that new, "plasticy" smell :). I intended to keep the Maxtor as a backup HD which would stay extremely well organized and torrent-free. 

Thank you,

Scavallo

---

