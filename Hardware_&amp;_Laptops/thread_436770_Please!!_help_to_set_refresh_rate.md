---
title: "Please!! help to set refresh rate"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by riscbroker on 2007-05-08
OK, this is desperation stakes. I'm reasonably computer literate but also reasonably new to Linux. I've installed, and used DSL, Kubuntu, Mepis, Knoppix and now Ubuntu 7.04, but never had so much trouble sorting out the screen. I've been thru all the forums and followed the howtos, borked the system three times to the extent that I have to reload the OS, and still the screen flickers. To the extent that I either have to buy a new screen or abandon Ubuntu on this machine. 

The screen I use is a 17 inch TVM AS6S, manufactured June 2001. The TVM website reports specs:
Scan Frequency: 30-70KHz horizontal, 50-120Hz vertical.
I am trying to establish screen resolution of 1024x768, refresh rate 85 on Ubuntu 7.04.
This machine dual boots XP and this resolution and refresh rate is fine on XP so obviously the monitor supports it.

When I install Ubuntu, the screen defaults to 1280x 1024, refresh rate 60Hz, no alternative refresh rate available. The screen flickers very badly.  I can select 1024x768, however the only available refresh rate is 61Hz, which still leaves the screen flickering badly.

I have followed the various howtos, when I restart X the preference settings indicate that I have specified 1024x768 at 85Hz, the resolution is correct but the screen still flickers. The flicker is such that I cannot use the OS.

Is this one of those cases where Linux is unable to support this hardware config or is there a workaround? 

Help please!

---

### Post by jjordan on 2007-05-08
I don't mean this as an insult but his is a pretty low end monitor.  My honest recoomendations is to updgrade or at least update.  That being said, it does not answer your question so here goes.

I believe you have a bandwidth problem, your monitor cannot handle all of the data you are throwing at it.  The only way I have foubd to force a specific refresh rate is to actually put it on the mod line in the xorg.conf file.  I am at work right now so I can't give you a good example even though I am using one on my HTPC system.  

The first thing I would try in your case is reducing the color depth to 16 that will reduce the data headed into the monitor.  

-j

---

### Post by riscbroker on 2007-05-08
Hi jjordan

Probably is a cheapo monitor, but it's a work PC so I have to make do or dig in my pocket.

I don't know enough to argue the premise of there being too much data for the screen to handle - why is it able to handle the resolution and refresh rate in Windows but not in Linux? I appreciate that they are totally different in structure, does this mean Windows is more efficient?Isn't Linux generally a better bet for lower end/older hardware?

That said, I'm more than willing to try your recommendations on the colour depth, is this a mission or can you give me a swift howto?

Thanks

---

### Post by DagMan on 2007-05-08
I guess that you've tried putting those values into /etc/X11/xorg.conf
for example my laptop looks like this:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	[COLOR="Red"]HorizSync[/COLOR]	28-64
	[COLOR="Red"]VertRefresh	[/COLOR]43-60
EndSection

---

### Post by jjordan on 2007-05-08
riscbroker,

I doubt that Windows is actually operating at 24bit color depth.  Windows video drivers are sometimes more efficient than Linux drivers because the video card manufacturers put most of their efforts where they have the most sales. Some hardware mfrs release video drivers for Linux but not all. As Linux becomes more popular and hardware manufacturers recognize that Linux presents a great hardware market they will come around.   There are lots of configurations that work great right out of the box but sometimes getting things going takes a little work.

Here are a couple of links that show how to force a refresh rate:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

[http://ubuntuforums.org/showthread.php?t=292152&page=3](http://ubuntuforums.org/showthread.php?t=292152&page=3)

-j

---

### Post by riscbroker on 2007-05-09
jjordan, I really do appreciate the time you've given this.

I've tried the links you posted, checked the forums again, still nothing works.

At least I know now how to recover my X config without having to reload the OS........

But seriously, is this a dead-end or can you recommend any other course of action? Will it help if I post my X config file? Perhaps there is something fundamental that I'm missing?

I've tried altering the colour depth to 16, no difference, at 8 I got some pretty psychaedelic effects and at 15 I got garbage.....

---

### Post by riscbroker on 2007-05-09
@DagMan - yes, I have tried editing my /etc/X11/xorg.conf, when I restart X the resolution preference tab tells me that the screen is set to 1024x768 at 85Hz but I still have that deadly flicker......

---

### Post by jjordan on 2007-05-09
How about this:

Open a terminal and type
**xrandr -r 85**

That should set the refresh rate to 85Hz.
If that does not work try 80, 75, 70 to see if you can stop the flicker.

If this works we should be able to change your xorg.conf to give you the rate you want.  Xwindows genrally defaults to the lowest rate allowed in the xorg.conf.  This is a holdover from the old days when and excessive rate could damage your monitor.

We will need to look at your xorg.conf file to help with that.

If you need help posting it let me know.

- j

---

### Post by jjordan on 2007-05-09
You may have to install xrandr, it in in the repos.  

-j

---

### Post by riscbroker on 2007-05-10
Thanks jjordan, installed xrandr, it doesn't do much except tell me what it thinks the screen is set to -currently 1024x768 85Hz. The resolution is correct but the refresh rate obviously not since the screen still flickers - badly.

I have run xrandr -r 85 from the terminal, got some arb reply that I cannot remember and cannot check now since I have reverted to Windows again. I tried altering values to 80, then 75, then 70 etc but no difference, still the same response from the terminal.

I guess this is why Linux doesn't make much headway against Windows - for me to make a 'free' OS work I must shell out for a new screen, which ain't gonna happen since the thing works perfectly with Windows.....

Thanks again for your help

---

### Post by ukripper on 2007-05-18
> **riscbroker said:**
> OK, this is desperation stakes. I'm reasonably computer literate but also reasonably new to Linux. I've installed, and used DSL, Kubuntu, Mepis, Knoppix and now Ubuntu 7.04, but never had so much trouble sorting out the screen. I've been thru all the forums and followed the howtos, borked the system three times to the extent that I have to reload the OS, and still the screen flickers. To the extent that I either have to buy a new screen or abandon Ubuntu on this machine. 

The screen I use is a 17 inch TVM AS6S, manufactured June 2001. The TVM website reports specs:
Scan Frequency: 30-70KHz horizontal, 50-120Hz vertical.
I am trying to establish screen resolution of 1024x768, refresh rate 85 on Ubuntu 7.04.
This machine dual boots XP and this resolution and refresh rate is fine on XP so obviously the monitor supports it.

When I install Ubuntu, the screen defaults to 1280x 1024, refresh rate 60Hz, no alternative refresh rate available. The screen flickers very badly.  I can select 1024x768, however the only available refresh rate is 61Hz, which still leaves the screen flickering badly.

I have followed the various howtos, when I restart X the preference settings indicate that I have specified 1024x768 at 85Hz, the resolution is correct but the screen still flickers. The flicker is such that I cannot use the OS.

Is this one of those cases where Linux is unable to support this hardware config or is there a workaround? 

Help please!

I had the same problem just sorted it  by reconfiguring xserver xorg and selecting my correct driver which is SIS instead of VESA and setting Horrizontal to 32-100 and vertical 55-110 hope that helps for u too. And checked in screen resolution which is giving me 85 hz now with other modes too.

In your case Select to appropriate graphics card driver when reconfiguring xorg and then setting Horizontal and vertical  as I have specified above.
__________________

---

