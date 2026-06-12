---
title: "Lenovo ThinkPad T400s + Multitouch Touchpad"
date: 2009-09-11
forum: Hardware
---

### Post by undoIT on 2009-09-11
I'm curious if the multitouch synaptics touchpad works with Ubuntu. Does anyone with a T400s know if all the multitouch features are working?

---

### Post by damien.corpataux on 2009-10-09
Hi, I couldn't get it to work neither. I have a Lenovo IdeaPad S12.

Have you tried this [http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html) ?

---

### Post by undoIT on 2009-10-09
> **damien.corpataux said:**
> Hi, I couldn't get it to work neither. I have a Lenovo IdeaPad S12.

Have you tried this [http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html) ?

I've tried that on some other laptops that don't have a multi-touch Synaptics touchpad, and I found that it didn't work very well. The scrolling wasn't very smooth and the two-finger right click was hard to engage. I think I might try it again with Karmic stable.

---

### Post by djst on 2009-11-03
I have a T400s and I couldn't get two-finger scrolling to work in Ubuntu either. :(

Such a shame, as this was the main reason why I went for this computer (Thinkpads were supposed to have strong linux compatibility, and this particular model has two-finger scrolling)...

---

### Post by undoIT on 2009-11-03
> **djst said:**
> I have a T400s and I couldn't get two-finger scrolling to work in Ubuntu either. :(

Such a shame, as this was the main reason why I went for this computer (Thinkpads were supposed to have strong linux compatibility, and this particular model has two-finger scrolling)...

Have you tried Karmic 9.10? I've got it installed on my Macbook and was able to easily activate the two-finger scrolling in Preferences > Mouse > Touchpad

---

### Post by casboy99 on 2009-11-03
I tried Ubuntu Karmic 9.10 Std live CD on my eeePC 1000h, both 2 and 3 fingers work, just activate in Preferences > Mouse > Touchpad

---

### Post by undoIT on 2009-11-03
> **casboy99 said:**
> I tried Ubuntu Karmic 9.10 Std live CD on my eeePC 1000h, both 2 and 3 fingers work, just activate in Preferences > Mouse > Touchpad

What kind of functionality do you get with 3 finger gestures?

---

### Post by Xzenome on 2009-11-05
Has anyone found a fix for this yet? I'm experiencing the described problem on a Thinkpad S12 using Karmic.

There don't seem to be any related notes of dmesg.

---

### Post by warrenkb on 2009-11-27
I had it working ootb on my T61p which is essentially a t400 without camera and finger print reader, since upgrading to 9.10 I no longer am able to use two finger scrolling. Very frustrating.

---

### Post by IgnasM on 2009-12-12
Same problem here. I have the new sl410, using ubuntu 9.10 64bit version ant multitouch isn't working. Any ideas on this issue?

Thanks!

---

### Post by tmcnulty1982 on 2010-01-10
I have a ThinkPad T400s (64 bit) and a ThinkPad T60 (32 bit).  Two finger scrolling works great on the T60 but not on the T400s.  When I run synclient -m I never see a '2' in the 'f' column.

---

### Post by undoIT on 2010-04-17
I have tested Ubuntu and Kubuntu 10.04 Lucid on my new Lenovo T410s and I have not been able to get the multi-touch working. Tried several of the usual hacks, no luck. Has anyone figured this out yet, or is this a driver issue that requires the Synaptic driver to be updated?

---

### Post by COW-tz on 2010-09-23
> **tmcnulty1982 said:**
> I have a ThinkPad T400s (64 bit) and a ThinkPad T60 (32 bit).  Two finger scrolling works great on the T60 but not on the T400s.  When I run synclient -m I never see a '2' in the 'f' column.

I experience exactly the same problem. I spent hours searching for a solution, but I couldn't find anything useful.

Still doesn't work with 10.10, unfortunately...

---

### Post by MeanderingCode on 2010-10-03
I was getting ready to give up, too, and wish it was more well supported here (via the usual channels) so I could use the beautiful synaptiks KDE Systems Settings plugin, but alas.

Anyway, I found this thread: [http://ubuntuforums.org/showthread.php?t=1419833]("http://ubuntuforums.org/showthread.php?t=1419833")

Works for me on my 410s :)

EDIT: Okay, this is *simulating* multi-finger action via wide pressure area.  Well, I guess i'll have to deal or dig further and see if i can manually get updated drivers.

---

