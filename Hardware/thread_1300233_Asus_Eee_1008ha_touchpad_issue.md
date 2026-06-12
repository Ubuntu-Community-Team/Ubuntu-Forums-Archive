---
title: "Asus Eee 1008ha touchpad issue"
date: 2009-10-24
forum: Hardware
---

### Post by NullHead on 2009-10-24
The touchpad works just fine, but the multi-touch "feature" doesn't seem to be working on Ubuntu 9.10 RC. For example, in mouse options, there is a setting for two finger scrolling, but when I have that option enabled, I loose scrolling abilities completely. If I change the setting back to edge scrolling, it works fine; like any other touchpad would. 

It's not really a big deal, but I'd like this to work.

---

### Post by NullHead on 2009-10-25
bump

---

### Post by tehMalone on 2009-11-03
I'm following this :D

---

### Post by thebloggu on 2009-11-03
The same on 1101HA

---

### Post by starwed on 2009-11-08
I have this issue too; I just replaced a stolen 901 with a 1008, and it's aggravating not having the multitouch features.

Is it known for sure that the hardware is capable of multitouch?  I couldn't see anything about it one way or the other on the eeeuser forums.

---

### Post by tehMalone on 2009-11-08
@ Starwed: It is confirmed that it has, it is actually a sales argument for Asus, that you can zoom internet, pictures and documents the 'iPhone way'. And I know you can, as I dualboot ubuntu NBR and Win7,

---

### Post by starwed on 2009-11-09
I think I read somewhere that even on the default windows install, only the zooming motions, not two-finger scroll, was working.

*edit - * Ah, regardless of whether it works by default, I found someone who [claims](http://forum.eeeuser.com/viewtopic.php?pid=604077#p604077) they got it working on linux with the right drivers.

---

### Post by NullHead on 2009-11-09
> **starwed said:**
> I think I read somewhere that even on the default windows install, only the zooming motions, not two-finger scroll, was working.

*edit - * Ah, regardless of whether it works by default, I found someone who [claims](http://forum.eeeuser.com/viewtopic.php?pid=604077#p604077) they got it working on linux with the right drivers.

I've got it working in windows XP and 7 at least ... all I needed to do is update the synaptics driver to the latest offered by Asus and away it goes. Two finger scrolling and all that awesomeness works great in XP (my 1008ha is older and came with XP :()

---

### Post by starwed on 2010-01-02
Just took another crack at figuring this out.  Running synclient, it only ever detects 1 finger on the touchpad at a time.

I'm very confused on whether the touchpad really supports multitouch.  I didn't have any problems with my older ASUS, so could it just be a matter of the touchpad being more recent hardware?  If there are more recent drivers than included in 9.10, where could I go about finding them?

---

### Post by starwed on 2010-01-02
Found that this issue is covered in [Bug 308191](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191).  

According to Alberto Milone in the comments, true multitouch is not implemented by this hardware! :(  This contradicts ASUS's product info, though.  So perhaps it is some sort of driver problem.  It would be nice to know if those who say they have it working on windows really have true multitouch or are just using the emulation program.

---

### Post by NullHead on 2010-01-03
I've used my windows xp restore disk a couple of times before, and this "multi touch" has always worked quite nicely. I can't tell you if it's emulated or legitimate, but it works.

---

### Post by beefstu on 2010-01-04
try this: [http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

I found this whilst trying to sort my laptop touchpad out - didn't work for me but its not the same laptop, just hoped i'd be able to use it too!

It seems that theres alot of problems in Karmic with touchpads.

---

### Post by starwed on 2010-01-04
> **beefstu said:**
> try this: [http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

I found this whilst trying to sort my laptop touchpad out - didn't work for me but its not the same laptop, just hoped i'd be able to use it too!

It seems that theres alot of problems in Karmic with touchpads.

Those instructions are to enable emulation; I'd really prefer to first understand whether that's truly necessary or not.  At this point I'm wondering whether *some* 1005/1008 units support multitouch and others don't.

---

