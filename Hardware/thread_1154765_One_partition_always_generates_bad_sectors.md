---
title: "One partition always generates bad sectors"
date: 2009-05-10
forum: Hardware
---

### Post by fela on 2009-05-10
The first partition on my Samsung Spinpoint F1 750GB always generates errors when, time and time again, I reinstall Windows XP on it (or Vista, any version). I use Windows for Video editing and a few games, that's it.

I've tried formatting the 'partition of doom' as ext4, and I'm gonna see if it generates bad sectors. I might try installing another version of Linux on it and use it extensively, see if it crashes at all (will let you know if it does happen).

Right now it seems more like a software issue (read: windows) because on the very same harddisk, I have numerous other partitions used by Linux and they all have worked fine. But whenever I install Windows to the first partition (haven't tried the other partitions) it always starts blue screening when I copy my apps over and run them.

I know this could be a hardware problem and I've read lots of people have problems with this HDD, but it seems suspicious that only one partition is dud. Plus the HDD was pretty much brand new when it first started BSOD-ing.

Any help much appreciated

---

### Post by caljohnsmith on 2009-05-10
So I'm just wondering, but how do you know for sure your first partition has bad sectors just because Windows blue-screens when you copy programs over to that partition? If that's all that is happening, it sounds to me like you most likely have a Windows problem and not a problem with your HDD. And what do you mean by copying over your apps--are you installing your Windows apps using their respective installers, or are you trying to copy over their directories? 

John

---

### Post by fela on 2009-05-10
> **caljohnsmith said:**
> So I'm just wondering, but how do you know for sure your first partition has bad sectors just because Windows blue-screens when you copy programs over to that partition? If that's all that is happening, it sounds to me like you most likely have a Windows problem and not a problem with your HDD. And what do you mean by copying over your apps--are you installing your Windows apps using their respective installers, or are you trying to copy over their directories? 

John

Well basically I install my apps (the normal way) and then randomly certain apps either blue screen when they load, or just don't work (or freeze the computer). Also I think it's unlikely a Windows problem cause all three versions of windows I've tried on it have had similar results (BSODs related to HDD errors). The last install of Windows broke when I tried updating it (it froze when updating, very easily a harddisk error again). The difference with Linux is that if the harddisk breaks while the OS is running it won't kernel panic, you can even still use your running apps! Not like Windows which just falls through the floor if anything happens whatsoever.

But I'm not so fussed about it anymore. The truth is there's a whole lot more to computers than Games and Windows, and I don't think I'm gonna try to reinstall windows again - I don't need it if I don't need my games. I can use Flash in virtual box, I've yet to come across a Linux alternative to that app.

---

### Post by fela on 2009-05-17
Don't know if anyone still checks this thread, but I've started using this partition as my /home partition (no errors yet - Linux wouldn't crash even if the HDD disintegrated though - NOT joking ;)) - And I put winblows on the second (250GB) Maxtor HDD. It might be an error that's solved by a low level format, but I'm not worrying about it anymore (as windoze seems to be fine on the other HDD)

):P

---

