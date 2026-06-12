---
title: "HP Mini 210 and a few minior issues with 10.04"
date: 2010-04-17
forum: Hardware
---

### Post by indarios on 2010-04-17
After installing and playing around with Ubuntu on my netbook I found pretty much everything works on it perfectly out of the box. The system is fully updated as well.

I am having a few annoying issues with it though. First I have a multimedia mute key with a LED light one it. The LED is always on, but it shouldn't be. the LED should only turn on when my system is muted. Is there a fix for this? Because I cant find one on Google.

The other issue I'm having is disk access. Every few seconds data is written. I'm pretty sure its something in Gnome because when I either log into xterm via GDM or just not log in, the hard drive will spin down.

Anyone have any ideas on these?

---

### Post by indarios on 2010-04-18
After playing with the find command I found what was making so many writes to my disk. Network manager and the indicator applet are to blame. 

Network manager is constantly writing data to .xml files in the ".gconf/system/networking/connections/1/" directory. Indicator likes to write to the ".cache/indicator-applet.log" file. Whenever I use my multimedia key to change my volume it logs it. I also get some other entry that it likes to spam.

I ended up creating a symbolic link for "indicator-applet.log" into "/dev/null" and adding the ".gconf" directory to the "/var/log/indarios/" directory to be kept in a ramdisk. This hack seems to work until I can find a better solution.

---

### Post by KdotJ on 2010-04-20
Any luck with the mute button LED? Mine is still on all the time.

Also, how is your mousepad? Can you right click ok?

---

### Post by indarios on 2010-05-02
> **KdotJ said:**
> Any luck with the mute button LED? Mine is still on all the time.

Also, how is your mousepad? Can you right click ok?

No luck at all. The mute button's LED is still always on and the touch pad is annoying to use to say the least. The hardware buttons work but only work in a small area at the corners it seems. Plus multi touch does not work, so if you have to be careful not to touch the touch pad with two fingers. I'm sure you have this same problem. I'm trying to find out if there is any work towards supporting this touch pad.

---

### Post by ElectroDruid on 2010-05-03
> **indarios said:**
> Plus multi touch does not work, so if you have to be careful not to touch the touch pad with two fingers. I'm sure you have this same problem. I'm trying to find out if there is any work towards supporting this touch pad.

Here's a post for getting the touchpad to work better: [http://www.backports.ubuntuforums.org/showpost.php?p=9158330&postcount=30](http://www.backports.ubuntuforums.org/showpost.php?p=9158330&postcount=30)

However, I think it still doesn't support multi-touch? I never used it so I am not sure what I'm missing ;)

---

### Post by indarios on 2010-05-10
> **ElectroDruid said:**
> Here's a post for getting the touchpad to work better: [http://www.backports.ubuntuforums.org/showpost.php?p=9158330&postcount=30](http://www.backports.ubuntuforums.org/showpost.php?p=9158330&postcount=30)

However, I think it still doesn't support multi-touch? I never used it so I am not sure what I'm missing ;)

This seems to not do anything new on my system. Does anyone else have the annoying problem when using the physical buttons you have to click them at the very bottom of the trackpad? Trying to click in the middle or top part of it does nothing. Is there a way to change that?

---

### Post by ljrmorgan on 2010-08-06
Has anyone had any progress with the Mute key? It's really annoying me!

I'm considering installing Jolicloud - it claims to support the Mini 210 out the box - if the mute key light works properly on that then it might be possible to figure out what it does differently and get it working in Ubuntu.

---

### Post by imaginaryboy on 2010-08-06
I think I was able to switch it off in the HP quickweb linux, and that it stayed off in UNR, until the next boot.  So maybe looking into what's going on there could help.

It would also be nice to get the LED on the trackpad working, to light when the trackpad is disabled; then it should be simple to configure clicking on that corner to turn off the trackpad.

---

### Post by ljrmorgan on 2010-09-06
I've just upgraded to Maverick - the mute key now works as it should - the light comes on when muted, and is off otherwise.

Yay! Finally!

Now I just need to figure out why I can't right click anymore...!

---

### Post by tim183 on 2010-09-13
how are you finding meerkat?

---

