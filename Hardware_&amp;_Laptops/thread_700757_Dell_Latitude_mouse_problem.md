---
title: "Dell Latitude mouse problem"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by GregRC on 2008-02-18
I just wanted to share a fix with everybody that took me all night to find.

I recently installed Ubuntu 7.10 on my Dell Latitude laptop. The laptop has both the nipple mouse pointer thingy and a touchpad. At random, the cursor would just go crazy, moving off screen and clicking random things. I spent a lot of time searching various forums to find a fix, but nothing worked. I made changes to my xorg.conf file and installed the gsyanptics package to configure the touchpad. I disabled the touchpad, but couldn't disable the nipple pointer and the problem persisted. It turns out it's a hardware problem with the nub pointer. Some users bought a new keyboard, others just used a USB mouse. I didn't want to spend money or use a USB mouse. I ended up opening the case and cutting the connection to the nub pointer. I can still use the touchpad and it works perfect now.  

1) Remove the hard drive/battery  
2) Remove 5 screws labeled "K"   
3) Open the laptop and pop off the strip with the power button
4) Pop up the keyboard  
5) Cut the ribbon connection to the pointer thingy

---

### Post by schnuser on 2008-02-23
I have a similar problem but i have a usb- mouse. sometimes the mouse curser does what it should but then suddenly it goes mad and then the curser goes to the right upper corner of the desktop. In this situation I cannot control the curser with the mouse. I already tried to  switch of the touch pad but that didn't help.
Any idea wht to do to fix this issue?
regards

---

### Post by konungursvia on 2008-02-24
You actually did a nipple vascectomy?

---

### Post by schnuser on 2008-02-25
> **konungursvia said:**
> You actually did a nipple vascectomy?

What does that mean?

---

### Post by impishgeek72 on 2008-03-07
I have a problem similar to that of schnuser except that my mouse, instead of going crazy, just stops. I unplug the mouse from it's port and plug it back in. All I get from the mouse is a couple of flashes then it just dies. Anyone have any ideas?

---

### Post by V2.Perry on 2008-07-06
I think I'm having a problem with my nub(nipple mouse), but im not quite sure. It seems whenever I type certain keys my pointer goes crazy, and goes off in a single direction for about half a minute. I have reinstalled hardy and it works fine untill it seems I eather knock my nub or just plain out of the blue typing.

I have looked around for awhile to fix this problem, I tried installing Qsynaptics and turning off the touch pad I tryed exiting the Xorg.conf. But to no avail, please help; its making me consider going back to Windows...

I was going to make a thread just for this problem but couldn't, sorry for the thread necromancy.

---

