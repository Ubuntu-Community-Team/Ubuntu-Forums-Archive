---
title: "Wanted to know how to make fan run all the time?"
date: 2010-04-07
forum: Hardware
---

### Post by keithg67 on 2010-04-07
I have been looking around for a answer and havnt found one yet on how to make the fan in my netbook run at full speed all the time. I know the fan is controled through the bios but in my old dell I was able to do this with a program I installed.

Acer aspire one
model# 532h - 2789
Ubuntu 9.10

any other info needed please let me know.

I am getting a cooling pad soon to help with the issue but I would really like to get the internal fan to run full speed all the time. the laptop is brand new and the fan and heat zink are clean. I heard about a program for the netbooks I think it was called (nhc) netbook hardware control that could do this for me but cannot find it. 

Thank you for any advice in advance,
Keith

---

### Post by User Name 6 on 2010-04-07
> **keithg67 said:**
> I have been looking around for a answer and havnt found one yet on how to make the fan in my netbook run at full speed all the time. I know the fan is controled through the bios but in my old dell I was able to do this with a program I installed.
 
Acer aspire one
model# 532h - 2789
Ubuntu 9.10
 
any other info needed please let me know.
 
I am getting a cooling pad soon to help with the issue but I would really like to get the internal fan to run full speed all the time. the laptop is brand new and the fan and heat zink are clean. I heard about a program for the netbooks I think it was called (nhc) netbook hardware control that could do this for me but cannot find it. 
 
Thank you for any advice in advance,
Keith
 
There are a number of free fan programs. Try this one I believe it enables you to set your fans speed up either manually or automatically.
 
[http://www.makeuseof.com/tag/monitor-your-computer-fans-with-speedfan/](http://www.makeuseof.com/tag/monitor-your-computer-fans-with-speedfan/)
 
The download is free:
 
[http://www.almico.com/speedfan.php](http://www.almico.com/speedfan.php)

---

### Post by keithg67 on 2010-04-07
> **User Name 6 said:**
> There are a number of free fan programs. Try this one I believe it enables you to set your fans speed up either manually or automatically.
 
[http://www.makeuseof.com/tag/monitor-your-computer-fans-with-speedfan/](http://www.makeuseof.com/tag/monitor-your-computer-fans-with-speedfan/)
 
The download is free:
 
[http://www.almico.com/speedfan.php](http://www.almico.com/speedfan.php)

The speed fan program is for windows I assume I can use wine to install and run this program and it should work? I'm Still new to linux for the most part.

---

### Post by Linuxforall on 2010-04-07
If you turn off Speed Step in BIOS for Intel CPU, the fan would go on constantly, in case of AMD, you have to turn off Power Now in BIOS.

---

### Post by User Name 6 on 2010-04-07
> **keithg67 said:**
> The speed fan program is for windows I assume I can use wine to install and run this program and it should work? I'm Still new to linux for the most part.

I don't see why the Linux operating system should be affected by this program. But hell install it and see if it doesn't work then I'd be surprised.

As opposed to using OS functions or even BIOS functions, this should enable you to set the fans operation and monitor it, I'd always use a utility over fiddling with BIOS, especially if you're not sure what you are doing, it's hard to do any serious damage even in  BIOS which is at least fairly safety conscious, but anyone can make a CPU melt. :D

[http://www.makeuseof.com/service/linux](http://www.makeuseof.com/service/linux)

There's an area dedicated to Linux on the site.

---

### Post by keithg67 on 2010-04-08
I tried speed fan both with and without wine with wine it would start but saw none of the hardware without it did not work it again did not see any of the hardware.

I went into the bios and did not see any thing named that. I may be doing it wrong and that would not suprise me lol if you could maybe post how to do it I would be very greatful.

Ty both for the info.

---

### Post by User Name 6 on 2010-04-08
> **keithg67 said:**
> I tried speed fan both with and without wine with wine it would start but saw none of the hardware without it did not work it again did not see any of the hardware.

I went into the bios and did not see any thing named that. I may be doing it wrong and that would not suprise me lol if you could maybe post how to do it I would be very greatful.

Ty both for the info.

Difficult to tell you without seeing your bios. 

Obviously press whatever f key takes you into the BIOS from start up and then, tell us what it allows you to do from there, you could prt screen and copy it to paint and show us perhaps? There should be an option to control temperature and or fans under a subheading. 

I have an acer aspire AX1301 I'll see how its done on mine, probably be the same.

EDIT:

My BIOS is idiot proof as well and wont allow you to change fan settings.

All I can tell you is that on my computer speedfan runs fine, but then on this particular system (my gaming computer) I am running windows 7.0. so that's no use whatsoever. I can set the fan speed of any fan to 0 using that programme. If you can't find a utility like speedfan that works on Linux then I think you're screwed. I just set my fan speed to 99% using configure/speed/ select 99%. The temperature went up by 1 degree so I'm sure it worked. For what its worth.

Notebooks are different from desktops in every way, it's possible that your computer itself is not compatible with speed fan, or you may need a laptop specific version. No idea.

EDIT 2:

[http://www.techsupportforum.com/hardware-support/laptop-support/145853-question-about-speedfan-my-laptop.html](http://www.techsupportforum.com/hardware-support/laptop-support/145853-question-about-speedfan-my-laptop.html)

This forum has some good advice. Apparently some notebooks are controlled either through the BIOS or if not by manufacturer specific utilities and wont work with speed fan generally. You might want to mess about with your processor speed if the fan option is not doable.

> 
**[How to cool off an Overheating Laptop]("http://www.pctipsbox.com/how-to-cool-off-an-overheating-laptop/")**


**2)  SPEED FAN**
Speed Fan is a tool written by Alfredo Milani Comparetti.  It&#8217;s a [freeware program]("http://www.almico.com/speedfan.php#") that  monitors voltages, fan speeds and temperatures in computers with  hardware monitor chips. SpeedFan can even access S.M.A.R.T. info for  those hard disks that support this feature and show hard disk  temperatures too, if supported.  It works on Windows 2000, XP, and Vista  &#8211; both 32 & 64-bit.

Folks &#8211; this is a pretty wicked program.  When minimized, it sits in  your System Tray and shows you the temperature in either Fahrenheit or  Celcius.  But how does it help you keep your machine cool? 
 
 The key feature of Speed Fan is the ability to *modulate the fan  speed* manually or on the basis of temperatures on the sensors in  your machine.  You can crank up the fan to its maximum speed all day,  everyday.  For example, I have laptops that are always on and always  connected to AC power&#8230; and I use Speed Fan to keep the fan on all the  time.  So what do I care if the fan is always on keeping the machine  cool?[http://www.pctipsbox.com/how-to-cool-off-an-overheating-laptop/](http://www.pctipsbox.com/how-to-cool-off-an-overheating-laptop/)


Apaprently speedfan is not compatable with Linux either.

---

### Post by cascade9 on 2010-04-08
Shouldnt be that hard to do. Look at this- 

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

You will have to edit /etc/modprobe.d/options though, no GUI.

---

