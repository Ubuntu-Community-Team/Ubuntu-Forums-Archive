---
title: "Getting ATI Radeon Mobility 7500 to work on Karmic 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by mlissner on 2009-11-06
Hello, I just installed Karmic on an old Thinkpad R40 laptop, and it's giving me nothing but trouble.

I have never had to deal with an ATI card before, but this one freezes the system a few seconds after I log into the system, usually when I do something that involves graphics work.

I've tried pretty much everything I can find, but nothing seems to make the thing work. Either the login screen doesn't come up at all, or shortly after I log in, it freezes. 

I've noticed that the computer doesn't have an xorg.conf file, but I've tried putting some values in there. I've tried a PPA that was recommended somewhere, and I've tried a few other things.

I'm really not sure how to proceed to get this thing to work. Does anybody have any suggestions as to how to get this computer functioning. It's really driving me crazy.

---

### Post by disneyfriedhistory on 2009-11-06
I'm having the same problem with my t30.  It has the radeon 7500 as well.  So far I've been able to disable visual effects and get decent results.  I also created an xorg.conf file like the following:

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"ati"
	BusID		"PCI:1:0:0"
	Option		"AccelMethod"	"XAA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AIGLX"		"true"
EndSection

This config file at least reduced a lot of the residual bugs that seemed to be floating around. But still no luck with compiz / visual effects.

Hope this helps.

---

### Post by Astinsan on 2009-11-07
The t30's video unit has only 16mb of ram. Switch to a color depth of 16 instead of 24. It should work after that. Also check this thread for some hints. [http://ubuntuforums.org/archive/index.php/t-32015.html](http://ubuntuforums.org/archive/index.php/t-32015.html)

Hope that helps

---

### Post by apirec on 2009-11-10
If I switch to a color depth of 16 instead of 24, all the videos become unwatchable slow and glxgears output is totally broken. When I tell mplayer to use another output driver, it works, but I can't tell firefox that for playing youtube, etc...

---

### Post by disneyfriedhistory on 2009-11-14
This used to be my solution in earlier versions of ubuntu.  But I was definitely using a color depth of 24 with the last two.  So I don't think this is the problem.

---

### Post by disneyfriedhistory on 2009-11-14
Okay, this has worked for me: Downgrade to the old jaunty mesa and glx drivers.  Then tweak your xorg.conf with what I suggested above.  This first link is the discussion: [http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg32591.html](http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg32591.html)
And this second link has a very easy to follow "how to":
[http://www.ode2.com/?p=44](http://www.ode2.com/?p=44)

Good luck!  Report back any problems so we can keep people informed.  If you get things working, also let us know at ThinkWiki.   
[http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500)

---

### Post by handy on 2009-11-14
If you don't need 3D, go to the open-source drivers, as they are vastly superior to the Catalyst drivers in 2D.

---

### Post by Nevermore on 2009-11-17
I have alot of problems with ATI radeon mobility 7000 on my panasonic Cf73.
I added xorg edgers repository and now i can use compiz, and i have accelerated video, but the sistem freezes randomly...
I really hope this will be fixed soon, i really like AWN and i wont like to switch back to normal gnome menues....

---

### Post by disneyfriedhistory on 2009-11-17
I'm not really sure about the 7000.  I believe it is like the 7500, but with less power.  I don't find that AWN plays well with my 7500.  I usually even keep compiz down to the minimal desktop effects that are both useful and pretty.  (Use the compiz settings manager to better tune your compiz effects.  I always found wobbly windows annoying anyways.)  But AWN on top of that always seemed slow, so I never used it.

So the question is: Were you successfully using AWN before?  And, all things being equal, is it less effective with karmic?  If that's the case, have you tried the suggestion above about downgrading your mesa and glx drivers?

---

### Post by aextance on 2010-01-03
> **handy said:**
> If you don't need 3D, go to the open-source drivers, as they are vastly superior to the Catalyst drivers in 2D.

Given that the advice at the link below advocates using Xorg.conf, is this the correct way to go for Karmic, which is supposed to make this file obsolete?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by aextance on 2010-01-03
I sorted my ATI Mobility 7500 problems by putting the following in my xorg.conf file:

Section "Device"
Identifier "ATI 7500"
Driver "ati"
BusID "PCI:1:0:0"
Option "AccelMethod" "XAA"
Option "RenderAccel" "off"
EndSection

It's the "RenderAccel" "off" option that's key. Accordingly changing the acceleration method from XAA to EXA does something similar at the cost of lower performance.

The same bug is detailed at the following links:

[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001)

[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/426582](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/426582)

[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/429295](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/429295)

Hope this helps!

---

### Post by opteron123 on 2010-01-08
> **aextance said:**
>  
Hope this helps!
 
 
Mate, that's exactly the info I needed, thankyou!!!
 
My compaq N1000C did not config the ATI mobility 7500 properly and there was no xorg.conf.
 
Adding the adapter info to a fresh xorg.conf has fixed it.
 
Now onto getting TV out to play nice.

---

### Post by Natealt on 2010-01-30
Hi [aextance]("http://ubuntuforums.org/member.php?u=672465"),

thanks for the info I had the same problem and from doing that code in the xorg.conf file I am now able to view my system monitor. But I also have this other problem, When I watch videos on youtube for instance, I can only watch them in the small screen, if I enlarge the screen the video is very slow. Also when I try to use google earth this message comes up saying

"You are currently running google earth in 'OpenGL' with software emulation. If you want to run google earth more quickly we suggest you upgrade your graphics card driver."

The odd thing about this is, I used to be able to run the same google earth version just fine under the last Ubuntu version "Jaunty"

If you or someone else could help that would be very appreciated, and by the way I'm using a IBM Thinkpad 2004 model with ATI Radeon Mobility 7500. Thanks

---

### Post by untitledtv on 2010-04-04
Sweet!  Thanks for the revised xorg.conf file settings...

Strange, another post actually said to do EXA, so playing around, but this setting seems to work best so far...still testing....no way to use normal displays under Apperance those...

---

### Post by threepenpals on 2010-04-18
> **aextance said:**
> Hope this helps!

Thank you so much for synthesizing all that!  Your fix solved pretty much all the issues I was having with this card--videos now play smoothly, osd-notifications work, and I can get semi-transparent windows.

---

