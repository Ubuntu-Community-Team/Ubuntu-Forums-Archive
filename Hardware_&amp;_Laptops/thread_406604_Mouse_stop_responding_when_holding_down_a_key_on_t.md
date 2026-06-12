---
title: "Mouse stop responding when holding down a key on the keyboard."
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by BlueSkyDefender on 2007-04-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/105389](https://bugs.launchpad.net/ubuntu/+bug/105389) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have Installed Feisty Fawn 7.04 on to my MacBook Pro and every thing seems to work fin till I Connected a external Mouse. I am only able to use the mouse, when I am not using the keyboard. The Dose not happen to my other PCs running Ubuntu.

This dose not seem problematic until I attempt to use STEAM to play FPS or every other game I have. The strange thing is that I am able to use the touch pad and the keyboard at the same time since the touch pad dose not lock up like the external usb mouse.

I have also have tried other mouse and keyboards but no luck. I think it has to do with the built in keyboard and touch pad on the MacBook Pro.

So the bottom line is external mouse stops working when i use the internal keyboard and external usb keyboard. Then come back to life when I stop using the keyboards.

Is there any way I can fix this problem?

Is there more information I can post here to help?

---

### Post by dan171717 on 2007-04-11
try dissableing the touchpad an how did u get steam 2 work i want 2 play half-life 2 and gmod:popcorn:

---

### Post by BlueSkyDefender on 2007-04-11
Cool I will try to Disable it.  I got steam working with Wine. you get that at [http://www.winehq.com/](http://www.winehq.com/) Wine easy to install as well.

Here is more information about steam on wine. [http://appdb.winehq.org/appview.php?iAppId=1163](http://appdb.winehq.org/appview.php?iAppId=1163)

Only if I know how to do it with out messing up my system lol.

---

### Post by BlueSkyDefender on 2007-04-11
I was able to disable it bit it didn't resolve the problem. I think it may just be a conflict with the usb or something so I am going to buy a Bluetooth mouse and hope that works. :(

 The Bluetooth mouse suffers from the same problem. So I wanted to see if the problem shows up on the live CD. Well it did not show up on the live CD.  So now I think it has to do with the ATI driver I installed. I am reinstalling the old version of linux to see if it shows up there. This problem is annoying the hell out of me.

---

### Post by dan171717 on 2007-04-16
errm the might be something in mouse properties or if you can dissable it in the bios

---

### Post by andybotting on 2007-04-18
I've also got a Macbook Pro and am experiencing the same problem. I noticed it while trying to plat RTCW.

It seems that if I hold down any key on the keyboard (except Shift, Alt, Ctrl, etc) then the mouse slows down, or even stops while that key is pressed. The interesting thing is that the trackpad is not affected at all. 

I'm wondering if this might be a USB issue or a Macbook Pro USB issue.

---

### Post by andybotting on 2007-04-18
Just to update.. this does not happen if I boot into my Gentoo install. Must be something Ubuntu related.

---

### Post by andybotting on 2007-04-19
I think i found the culprit. A package called mouseemu.

apt-get remove mouseemu

---

### Post by BlueSkyDefender on 2007-04-21
> **andybotting said:**
> I think i found the culprit. A package called mouseemu.

apt-get remove mouseemu

Now i am upgrading again :D.... hope this works :p....

But ya ;-; how did you find out thats the problem. ^_^ I am still getting used to Linux. So far I love it now.

---

### Post by amitofu on 2007-06-16
I just posted the following to the bug listed above. Thanks andybotting for tracing the problem to mouseemu:

I had the same problem on my MacBook. mouseemu is definitely the culprit. Instead of removing it though,
edit /etc/default/mouseemu and uncomment and change the last line to:

TYPING_BLOCK="-typing-block 0"

It appears mouseemu has a feature to disable the trackpad while typing. It seems to be mistaking an external mouse
for the trackpad because the mouse gets disabled but NOT the trackpad. Perhaps this is a usb device naming issue.

This completely fixed the problem for me.

**Edit:** Don't forget to run:

sudo /etc/init.d/mouseemu restart

for the changes to take effect.

---

### Post by willskills on 2008-05-20
Thanks for this guys, I have a Logitech g11 gaming keyboard, and it seems this behaves similarly for me when having a usb mouse plugged in!

---

