---
title: "Touchpad Issues"
date: 2011-08-01
forum: Hardware
---

### Post by cbennett926 on 2011-08-01
Hello, I have a HP Dv6 Laptop and I the touchpad did not correctly work upon installation and I found some code to fix that and it basically told my computer that I have a P/S2 Touch pad or something like that. I can currently tap-to-click, left click, right click, and click and drag. Is there anyway I can get it to to scroll? Also when I go to mouse preferences I have absolutely no options for my touch pad. I posted a screen shot of what it looks like.

---

### Post by cbennett926 on 2011-08-01
Ok, I have figured out scroll, although I wish it were edge scrolling. Currently I can set my scroll to the mouse 1 button (left click, tap) and I can scroll that way. It is my understanding that no one has come up with mutltouch which I am fine with, beggers can't be choosers after all.

---

### Post by cbennett926 on 2011-08-02
Bump

---

### Post by Andrethe7th on 2011-08-03
I'm looking at a similar problem, and it appears the p/s2 configuration treats it as a mouse and not an actual touchpad, so those settings won't be available.  More info here:
[http://ubuntuforums.org/showthread.php?t=1753920](http://ubuntuforums.org/showthread.php?t=1753920)
I hope that helps.

---

### Post by cbennett926 on 2011-08-03
Is there any other configuration?

---

### Post by tjhans on 2011-08-03
Do you know if there is anyone working on a multi-touch support for ubuntu, and where to follow the progress on that?  It would be sweet to have 3 fingers change work spaces like it does on the new OSX Lion (my brother is a mac user and nearly wet himself when he got that feature).

---

### Post by cbennett926 on 2011-08-03
I have no idea, I just really wish I could configure my touchpad.

---

### Post by dog-soldier on 2011-08-03
what version are you using?
im using 11.04 on my tablet pc and my touch pad works great along with edge scrolling and two finger scrolling.


edit to add photo

---

### Post by cbennett926 on 2011-08-03
LUCKY!! I am using 11.04 on a HP Dv6, when I first installed Ubuntu I believe I could configure it, but couldn't right click. I did some googling and found some code that would enable me to right click as well as click and drag so of course I used the code. Now I can't configure my touchpad at all, my computer recognizes it as a mouse :/

---

### Post by tjhans on 2011-08-03
I'm on a Samsung RV511 laptop.  I don't have a touch pad tab in my mouse options...did you have to do anything to make that appear?  I have a 11.04 install, still pretty fresh from the box.  Just installed it along side windows last weekend.  I think ubuntu is really cool, I'm just a fish out of water with it.

---

### Post by cbennett926 on 2011-08-03
When I fresh installed it was just an option already. Then I installed a different code and I could no longer configure my touchpad

---

### Post by 3602 on 2011-08-03
I have a dv7 and I also have a bunch of touchpad problems, including not being able to right-click.
A Synaptics driver is indeed loaded but it might not be a proper one. Both OpenSUSE and Fedora load correct ones that actually lets you disable the touchpad by tapping the little light.
Other than that, try installing *gpointing-device-settings* from Synaptic Packager. It got so unusable to me that I just disabled it entirely and am relying on a (Microsoft) mouse.

---

### Post by cbennett926 on 2011-08-03
Well, if you want to be able to right click and click and drag here's the coding I used.


To get the trackpad working correctly you need to use the terminal and  enter in the below commands. Make sure you press enter after each  command:

     	Code:
 	sudo su 
     	Code:
 	echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 
     	Code:
 	reboot 

Once the computer reboots your trackpad will be able to do left click and drag and right clicking.

---

### Post by 3602 on 2011-08-03
And thus disabling the Synaptics driver.
Every time you do any modprobing you will see the warning WARNING: All modules need config file, or something similar to that.
That is unacceptable. 
However if you can live with that, then do it. That's what I did when I first installed Maverick too and found meself not being able to accept that.

Word of advise. Don't sudo su.

---

### Post by cbennett926 on 2011-08-03
Oh darn, I'm assuming there is no way of un-doing that?

---

### Post by 3602 on 2011-08-03
Delete the psmouse.modprobe file and reboot.

Instead of *sudo su*, do *sudo -i. *The proper enviro params will be set up with the -i flag.

---

### Post by cbennett926 on 2011-08-03
Where would the modprobe file be located?

---

### Post by 3602 on 2011-08-03
Alright,
*sudo rm -rf * [I]/etc/modprobe.d/psmouse.modprobe
[/I]Done.

---

### Post by cbennett926 on 2011-08-03
YES! I can manage my touchpad!! YOU ARE A SAINT!! Ok, now I can still right click, although not easy, I have to tap the very very right corner of my touchpad. Is there a way to edit the "tap zones" on the touchpad?

---

### Post by 3602 on 2011-08-03
This I don't know, which I why I opted to disable it entirely...

---

### Post by cbennett926 on 2011-08-03
Oh well! I can manage and I'll google around! Thank you so much!

---

### Post by 3602 on 2011-08-03
No problem man, always GLaD to help out a fellow Ubuntu user.

---

### Post by cbennett926 on 2011-08-03
Hey, kinda off topic, how is Canada? I've always been curious what it's like compared to the US.

---

### Post by 3602 on 2011-08-03
I'm in Quebec and definitely cannot speak for Canada.
People of Quebec (City): Six years of being here (immigrant), they may be cold and hostile at first. There is a strong self-preservation thing going on here as Quebec speaks French and is surrounded by English speakers. Once you speak French and kinda meld-in and talk their topics (mostly hockey, beer and poutine), they can be really warm, caring and you can certainly develop a camaraderie with them. I work in a lab and we bunch of lab guys just kid around and whatnot.
Also winters are cold. Very. And snowy. Very.

---

