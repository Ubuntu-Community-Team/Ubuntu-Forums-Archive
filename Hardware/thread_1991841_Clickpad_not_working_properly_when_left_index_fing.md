---
title: "Clickpad not working properly when left index finger is resting on it"
date: 2012-05-31
forum: Hardware
---

### Post by rcano on 2012-05-31
CONFIGURATION

Ubuntu 12.04 with the latest updates (up to the 26th of May)
Asus Zenbook UX31 with Elantech touchpad updated with the latest BIOS

PROBLEM

Trying to use the touchpad with my right index finger while resting my left index finger on the lower part of the touchpad (left button area) is not working. The pointer is not moving or sometimes it is detected as if I was trying to do two-fingers scrolling.


DETAILS

I’ve checked the [**very big thread**]("http://ubuntuforums.org/showthread.php?t=1865577") at the forums and also the great [**compilation**]("https://help.ubuntu.com/community/AsusZenbook") at Ubuntu site. After applying most of the tips and fixes there, I came into this [**patch**]("http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html") from Chase Douglas, and activated left click and right click support.

Finally I came into [**Synaptics manpage**]("http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html") explaining the Synaptics configuration to try to understand if some setting was missing. I tried the AreaBottomEdge setting to try to disable the lower part of the touchpad and although it is working (no movement detected at that area and no clicks) my problem still remains as I guess the problem is two-fingers being detected on the touchpad. Maybe a solution is to disable two-fingers scroll, but I would like to have the same functionality as in Windows.

Does anyone know what am I doing wrong? I really want to have this functionality and I don’t know if this is something usual. I don’t mind getting my hands “dirty” if I have to dig into low level stuff (developer here!), but I still think that I’m doing something wrong.

Could someone please help me? It is much appreciated!

Thanks,
Roberto Sosa

---

### Post by roelforg on 2012-05-31
I always disable tap-click (and scroll if the system has a phys. scrollwheel) as one of the first things i do on an OS.
The settings you're looking for are in system settings->mouse/touchpad->touchpad

---

### Post by rodpott on 2012-05-31
Got the same problem and no solution. It is like driving a car with automatic transmission --> Put the left hand away. My problem is that i use the left thumb to klick the touchpad buttons since years. I also think i am much faster do it like this.
So i am happy for any suggestions, too. 

> **rcano said:**
> CONFIGURATION

Ubuntu 12.04 with the latest updates (up to the 26th of May)
Asus Zenbook UX31 with Elantech touchpad updated with the latest BIOS

PROBLEM

Trying to use the touchpad with my right index finger while resting my left index finger on the lower part of the touchpad (left button area) is not working. The pointer is not moving or sometimes it is detected as if I was trying to do two-fingers scrolling.


DETAILS

I’ve checked the [**very big thread**]("http://ubuntuforums.org/showthread.php?t=1865577") at the forums and also the great [**compilation**]("https://help.ubuntu.com/community/AsusZenbook") at Ubuntu site. After applying most of the tips and fixes there, I came into this [**patch**]("http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html") from Chase Douglas, and activated left click and right click support.

Finally I came into [**Synaptics manpage**]("http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html") explaining the Synaptics configuration to try to understand if some setting was missing. I tried the AreaBottomEdge setting to try to disable the lower part of the touchpad and although it is working (no movement detected at that area and no clicks) my problem still remains as I guess the problem is two-fingers being detected on the touchpad. Maybe a solution is to disable two-fingers scroll, but I would like to have the same functionality as in Windows.

Does anyone know what am I doing wrong? I really want to have this functionality and I don’t know if this is something usual. I don’t mind getting my hands “dirty” if I have to dig into low level stuff (developer here!), but I still think that I’m doing something wrong.

Could someone please help me? It is much appreciated!

Thanks,
Roberto Sosa

---

### Post by lucastsa on 2012-10-22
Has anyone fixed this problem?

---

### Post by moserino on 2012-10-28
No news about this subject?
I have an unibody macbook pro 8,2 and everything works pretty well. 
The only problem i have is this. I always leave my thumb resting on the bottom of the touchpad. in os x nothing happens, but with 12.04, it just blocks every action. I have tried everything, but nothign seems to work!
i would be more than greatful if someone would help me out! this is the only thing stoping me from using linux as my main os.

greets

---

### Post by blk_jack on 2013-01-21
Also affected by this annoyance.  Anybody have any luck?

---

### Post by rcano on 2013-01-21
Hi all,

Finally I changed my laptop for a Mac Book Air. No problems at all, including Ubuntu. I hope you guys can find a solution to this soon!

Kind regards,
Roberto

---

### Post by blk_jack on 2013-01-21
> **rcano said:**
> Hi all,

Finally I changed my laptop for a Mac Book Air. No problems at all, including Ubuntu. I hope you guys can find a solution to this soon!

Kind regards,
Roberto

Do you mind posting which Input driver you're using (synaptics, multitouch, mtrack, etc) and if possible any Options?  Even if they're the defaults?  I'm actually using a Samsung Chromebook (ARM) and in Chrome OS the trackpad works prefectly, but in Ubuntu I get the issues outlined earlier in the thread.

Thanks!

---

### Post by lazarusx on 2013-05-08
Im assuming no one found a solution to this? :( Im relatively new to ubuntu..

I just picked up an Asus s200 and i'm having this issue with ubuntu 12.04. I tried adjusting the value of AreaBottomEdge but as mentioned in the original post the problem still remains that it detects two fingers on on clickpad and the cursor doesn't move, disabling/enabling two finger scrolls doesnt seem to help either.

---

### Post by zgold550 on 2013-06-21
Just throwing my Hat into this ring as well (and subscribing to updates).  Everything is great with the world if I keep my finger OFF the click-area, but old habits die hard.  Also tried the AreaBottomEdge and BottomEdge synclient configs -- resting a finger there seems to activate 'multitouch' state.  Would be wonderful if AreaBottomEdge ignored *all* input beyond the specified ranges.

---

### Post by zgold550 on 2013-06-21
Also, a possibly relevant bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046)

---

