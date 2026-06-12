---
title: "How to Download Garmin GPS Maps"
date: 2010-04-20
forum: Hardware
---

### Post by treeclimber on 2010-04-20
My husband has a Gamin nuvi GPS he bought last year, when he still had Windows XP.  We now have both of our computers running on Ubuntu 9,10,  He recently got on the Garmin website to update his maps.  But to download the maps, he has to install a Garmin Communicator Plugin.  Unfortunately, they don't make this for Firefox on Ubuntu.  I tried to install IE using Wine, but it doesn't seem to be working correctly.  Any ideas?  It really gripes me that these darn companies can't get it through their thick skulls that not everybody uses Window!!

---

### Post by tegwilym on 2010-05-07
Add me to the list!
I just got a Garmin eTrex Venture HC that I'm trying to get working with Openstreetmaps and Ubunutu.  I can get the maps with Ubuntu fine and convert them to .img, but then I have to boot up Windows to see the Garmin on the GPS to upload them to the unit.  
Getting closer.....but like you I'm annoyed when I just see Windows/Mac options.  I do like Mac, but I have Linux at home.

---

### Post by IcarusR on 2010-05-08
I had the same issue with the plugin. Ended up installing Firefox windows version under wine, the installing the Garmin 'communicator' plugin. 
Couldn't get it to work with IE either.

I have a line in my /etc/fstab for my Garmin 2820

```
/dev/sdb    /mnt    vfat    rw,user,noauto  0   0
```

I attach garmin & mount from terminal to mount

```
mount /mnt
```

& to unmount

```
umount /mnt
```

Original idea came from here

[http://bradthemad.org/tech/notes/garmin_streetpilot.php]("http://bradthemad.org/tech/notes/garmin_streetpilot.php")

Admittedly I have not tried updating mapping this way. I can update speed camera database & update firmware using Garmins windows programs with wine (POIloader & Webupdate). 
Mapsource also works. Unit shows up as 'J drive'

I can also upload data from my Oregon 300 to the Garmin Connect website using FF & wine.

I hope this helps.

---

### Post by flyfishingphil on 2010-05-09
You might want to check the Ubuntu Software Center for a couple of possibilities. Just go in and type in Garmin in the Search bar. Several, multi-gps usable, program packages are offered. See if one of these helps out.

I haven't done much with my Mag Explorist yet so can't offer much more but did notice that it was immediately offered in "Places" as a 2GB Filesystem and, when I looked at what was in there, it gave text format listings on my POI's. Haven't looked into the maps yet, for my computer, but I already have what I need in the Explorist.

---

### Post by tegwilym on 2010-05-10
I'm still having problems getting the GPS/Computer to talk to each other.  It works fine in Windows, but I don't want to go that way.

I forget what I did, but I did the the GPS to beep when I did something on the computer side, so it's seeing it, but just not transferring easily.   I'll give the Firefox thing a try mentioned above a try, but still think I need a good transfer to work first. 

I'm not seeing anything that really looks like the GPS listed in the /dev folder though.  My unit is a Garmin eTrex Venture HC.

Tom

---

