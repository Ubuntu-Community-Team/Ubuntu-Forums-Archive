---
title: "ATI R128 driver and Rage Mobility M4"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by sigmason on 2006-07-07
Got a Dell Latitude C800 laptop with ATI Rage Mobility M4.

To install, I used safe mode and the VESA driver.
That let me use 640x480, 800x600 and 1024x768.
All was well.

Then used 'dpkg-reconfigure xserver-xorg' to get the ati driver and the subdriver r128.

I got the 1400x1050 resolution and the 1280x1024 resolution and a quicker display.

Only one little issue....and it's the same in Dapper & Breezy...
I can't get the R128 driver to display correctly in any resolution below 1280x1024...
It sees them, the LCD can handle them.
Xorg.0.log checks out fine.

However, if you select say the 1024x768 mode...you get a scrambled screen with a bar down the middle...same with 800x600 and 640x480.

I tried ALOT of modelists...and nothing fixed it.
I even used the actual modelist for the VESA mode 118 and that mode absolutely does work in VESA (I used to write assembly video drivers...I'm very sure it works...I even queried the card registers to check.)

Anyone else having this hangup?
If you are, were you able to fix it...well either then using VESA for 640x480, 800x600 and 1024x768 and then switching (restarting X) for 1280x1024 or 1400x1050.  Personally that's a problem for me as the VESA driver isn't exactly accelerated either.

Note I've also tried turning off the acceleration 'option "NoAccel"' and 'option "NoDDC"' (that isn't even a real switch) and I even tried turning down the DAC.

sigmason

---

### Post by melotron on 2006-07-07
Woa! Finally someone with the same problem! I have a Dell C600 with a Rage 128 Mobility M3 video card and a 14.1" TFT SVGA screen. I have tried the ATI and the r128 drivers as suggested in some threads (one in the launchpad i recall) and have not been succesfull so far. I still have not tried the vesa driver. As you say, I can correctly see 1400x1200 and 1280x1024 but can't do anything below that without the screen going bananas. The desktop area is well delimited, but it seems it can't figure out correctly the middle part.

I've seen some other posts in which most people can't see anything higher than 800x600 or so, but had never seen anyone who could not see below 1280x1024 as is my case.

There are some suggestions that you try the following (which I'm sure you must have done already). Yype in a terminal

sudo dpkg-reconfigure xserver-xorg

(I might be wrong on the exact module, but it is the xserver configuration). Perhaps this might help.

Currently I have not been able to solve my problem and it's really a little bothering cause I prefer to see things a little bigger. If you find any solution, please let me know, I would appreciate it a lot!

---

### Post by sigmason on 2006-07-07
Adding to this:

Of course the proprietary ATI driver is no help (I tried just for the heck of it.)

I also discovered that the Display utility in KDE actually can insert the modelines in xorg.conf allegedy specifically for this display panel...guess what...that gets the exact same results.

I'm pretty sure at this point, given that the VESA driver works and now I'm sitting here with a set of 'tested' modelines specifically for this laptop LCD that also seem to work in VESA that there's an incompatibility (or bug) in at least the R128 portion of that Xorg driver...I might be wrong...but it sure seems that way.  Specifically with regard to it not getting the modes below 1280x1024 correct on this display and laptop combination of course since I don't have anything else with this exact configuration (say a desktop) it's tought to tell.

Later I'll hook up a CRT to the SVGA port and see if I can see that right (my refresh is the very conservative 60Hz so I'm not likely to hurt the CRT.)  If I can see the correct image...then maybe the panel controller is acting odd.  If I can't, and I get this same issue, I can be assured that something is not right between r128 and my video chipset.  I'm also going to see if I can find out with the ATI drivers from Windows 2k Pro and putting in the CRTC register...just to see if modeline will ever make this right.

Will post later if I get anywhere.
sigmason

---

### Post by melotron on 2006-07-07
I just reread your original post and recalled you had already done sudo dpkg-reconfigure xserver-xorg. Late advice!

It seems the problem is with the native resolution the screen can do. I did some research and it seems the LCD panels can't do any refresh rate that's not say 60 Hz. Said that, some resolutions need the refresh rate to go above or below 60.

Tying this information to something I found on modelines and after reading the xorg.o.log I tend to believe (although am not completely sure of) that the refresh rate for a 1024x768 or lower resolution goes out of range for the flat panel. Hence, it cannot support it correctly.

I tried adding some modelines on the /etc/X11/xorg.conf file but they did not solve the problem.

I also run a win2000 second boot on this box, but curiously, I can display as low as 600-400 on the screen. As well, DELL did write and posted a patch for the win driver for the screen which corrected the screen size problem (it used to shrink so as not to extend across the whole screen, but rather used a smaller portion with thick black bands on the border.

I have looked on the dell website for some patch for linux and haven't been able to find any. I also searched within the ATI website for a linux driver but they have one that works under fedora and I'm not sure that it might work on ubuntu.

Finally, I just bumped into the following thread [http://www.ubuntuforums.org/showthread.php?t=191319&highlight=dell+screen+resolution+dapper](http://www.ubuntuforums.org/showthread.php?t=191319&highlight=dell+screen+resolution+dapper)
which gives another possible solution to a similar problem.

Hope this can help you somehow...

EDIT: just found this post that includes a solution I had seen before. I tried it with the dapper live CD but to no avail. Perhaps it might give you some clues.
[http://www.ubuntuforums.org/showthread.php?t=199306&highlight=dell+screen+resolution+dapper](http://www.ubuntuforums.org/showthread.php?t=199306&highlight=dell+screen+resolution+dapper)

---

### Post by sigmason on 2006-07-07
ugh I just got logged out after typing a great big long SOLUTION to this.....AAAHHAHAHAH!](*,)

---

### Post by sigmason on 2006-07-07
Ok, well I guess I had time :mrgreen: 

Anyway, guess what...if you hook up the external monitor (a Dell Flat Screen CRT Modem M782) to the SVGA port...then switch modes...LOL...IT WORKS THEN!.  Kind of.

After you change resolution with the Screen Resolution tool in GNOME both screens go blank (the backlight on the LCD is on).  After playing with it, I realized that I had to hit the Fn & F8 combo a few times... the first time makes the LCD backlight turn off (I guess it turns off the local laptop LCD in favor of the monitor normally...I don't usually do this enough to notice)...the second time makes the LCD display come up...CORRECTLY...regardless of the resolution selected (it can be 640x480, 800x600, 1024x768, 1280x1024, 1400x1050, or even higher (the display will scroll)) however, the monitor is off (makes sense right...you are toggling the display options.)   Finally if you hit that combo for the third time you get both the display and monitor.

Now this is interesting to me for a few reasons.
One because there's a switch for Options in the Device section that's not in the man for the ati driver call MetaMode (try it if you doubt it...it won't be listed as rejected or accepted in the Xorg.0.log)  This switch is targeted for support of the dual head  display cards...IE this card.  The purpose of MetaMode is to let the user put the screens at 2 different resolutions (like the Windows ATI driver can do.)  However, I had put this in for "1024x768" for both screens.  Me thinks that since the Xorg ati driver likes to pick the highest screen resolution it can, it's ignoring me in xorg.conf.  (Incidently, MetaMode is also an option on some NVidia drivers...though I've never used it.)

Also, I do get an error, which appeared to be unrelated in the Xorg.0.log file that states that when the laptop is NOT connected to an SVGA monitor, the VESA VBE DDC read *failed*, however, if you connect it to the analog monitor the VESA VBE DDC read is *successful*.

So from this I conclude that this is not a bug or problem in the Xorg ati driver at all.  It is a problem with the Dell C800 laptop's LCD panel failing to complete a DDC request (DDC is how the video card HARDWARE knows what the monitor can do...if DDC is messed up I've seen even the venerable ATI Rage IIc PCI go crazy...it's something funny ATI did in that case, and I'm betting the same in this case.  So since hooking up the external monitor gets the silly video card something useful from the DDC request the silly ATI card does what it's supposed to do then (and only then.)  Sadly, once you disconnect the monitor and then change the resolution again or restart X (or the computer for that matter), you are right back  in the same boat.

So I guess I am answering my own question:

1. Yes it's a bug and it appears to be in the hardware, not the software.
2. I don't think it's a Dell bug...I've seen this DDC problem with ATI Rage IIc chipsets in Windows NT 4.0 so I'm betting it's from the ATI hardware chipset & firmware.  (LOL, and I spent days finding a fix for that too.)
3. It's not a problem if you only change video modes with an external CRT connected and keep the CRT connected below 1280x1024, since no analog input CRT I know of does 1400x1050.
4. No modeline entry will fix this...it is unrelated to that.  I have the Xorg.0.log that shows the DDC request succeed and it proves the modeline I have are correct because the modeline it ended up using correctly are exactly the same.  So no love here for a solution.
5. I've seen someone use an Option in the Driver section called NoDDC...but the current Xorg ati driver, doesn't seem to note responding to it in the Xorg.0.log, it just keeps trying DDC anyway, but oddly it doesn't puke like it does if you leave the word "true" in there...and "true" used to work (not in the current build though.)
6. I'm betting the problem is deep in the heart of the ATI proprietary hardware chipset and firmware because if the VESA driver works, clearly ATI did SOMETHING in the video card firmware to make that happen.  Probably doesn't happen in Windows because they either dump their driver into the VESA mode in a different manner then the XOrg ati driver or they made a workaround.
7. It's not likely the acceleration is causing this because the Xorg ati Option NoAccel is noted in the Xorg.0.log as recognized.

So I guess, if I want my lower res. modes I either dump the accelerated  Xorg ati driver in favor of the standard XOrg VESA driver or keep a monitor handy (in case I reboot or change video modes) or I start digging and see if I can get either the maintainer at Xorg to patch this (like ATI somehow did) or MAYBE find a Option string that works around it.

sigmason ](*,)

---

### Post by sigmason on 2006-07-07
> **melotron said:**
> I just reread your original post and recalled you had already done sudo dpkg-reconfigure xserver-xorg. Late advice!

It seems the problem is with the native resolution the screen can do. I did some research and it seems the LCD panels can't do any refresh rate that's not say 60 Hz. Said that, some resolutions need the refresh rate to go above or below 60.

Tying this information to something I found on modelines and after reading the xorg.o.log I tend to believe (although am not completely sure of) that the refresh rate for a 1024x768 or lower resolution goes out of range for the flat panel. Hence, it cannot support it correctly.

I tried adding some modelines on the /etc/X11/xorg.conf file but they did not solve the problem.

I also run a win2000 second boot on this box, but curiously, I can display as low as 600-400 on the screen. As well, DELL did write and posted a patch for the win driver for the screen which corrected the screen size problem (it used to shrink so as not to extend across the whole screen, but rather used a smaller portion with thick black bands on the border.

I have looked on the dell website for some patch for linux and haven't been able to find any. I also searched within the ATI website for a linux driver but they have one that works under fedora and I'm not sure that it might work on ubuntu.

Finally, I just bumped into the following thread [http://www.ubuntuforums.org/showthread.php?t=191319&highlight=dell+screen+resolution+dapper](http://www.ubuntuforums.org/showthread.php?t=191319&highlight=dell+screen+resolution+dapper)
which gives another possible solution to a similar problem.

Hope this can help you somehow...

EDIT: just found this post that includes a solution I had seen before. I tried it with the dapper live CD but to no avail. Perhaps it might give you some clues.
[http://www.ubuntuforums.org/showthread.php?t=199306&highlight=dell+screen+resolution+dapper](http://www.ubuntuforums.org/showthread.php?t=199306&highlight=dell+screen+resolution+dapper)


See I'm not crazy...okay...I am...but not this time :rolleyes: 

Thanks for responding.
As I've worked out above this is not a refresh issue at all...at least not in the sense that a modeline will fix it ever.

See there's a utility that installs with Gnome called gtf, it lets you play around with different resolutions and refresh rates, it will even let you get a -v (verbose) output of how it gets the modeline it gives you to type into xorg.conf.  All it does is perform a simple...well simple for an electronic engineer...calculation based on the parameters that go into the CRTC register of the video card.  If you wanna try some realistic settings try here, start with a 60Hz refresh, then try 43Hz, then 70Hz, then 75Hz, the 108Hz...keep trying...trust me I have 87 modelines alone for 1024x768.  All of my modeline have been tried and I know Xorg's ati driver tried them because they show with the *Mode syntax in the Xorg.0.log file in /var/log.

Now the real problem is:

You are right, in a very real sense...the video display is being driven at the wrong refresh, it's just not the modeline parameters fault, it's something the video card seems to be doing either because of a bug in the firmware or some hardware dependency on DDC (that SHOULD NOT be there.)

Anyway, do me a favor please, can you look in your Xorg.0.log and see what it says directly below this:

>SNIP from Xorg.0.log in /var/log<
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2 # **** It MIGHT say none here!!!! ****
(II) R128(0): VESA DDC transfer in appr. 2 sec.
>SNIP End<

Do you have a message that it failed when no external CRT is connected.  I bet you do.

Now connect an external CRT or LCD panel with analog in and try it, I bet it works then right?

Please let me know, I'm going to bring this to the attention of the maintainer at Xorg to see if they can address it.  I know I've seen a similiar bug listed with them, only MetaMode seemed to address it (it doesn't work for me yet...then again...only now do I understand the mechanics of the problem.)

Also, try using dpkg-reconfigure xserver-xorg and change to the VESA driver.  Now see if you can get to 640x480, 800x600 and 1024x768 (I'll bet they become available as defaults when you do the monitor autodetection.)  Just please note that there is really NO acceleration in the VESA drivers...acceleration is proprietary so you need something hardware specific.

Also, if for some reason you can't go down in resolution (in the Screen Resolution applet) make sure you have the lower resolutions with a * next to them when you do the dpkg-reconfigure xserver-xorg with the XOrg ati driver selected...otherwise...I've seen the silly monitor autodetection detect ONLY the 1400x1050 mode because (hey guess what in retrospect) THE DDC fails!

sigmason

---

### Post by melotron on 2006-07-07
Thanks for the response as well.

Currently I'm not in front of the C600 box and won't be before tonight. When I get home I'll try what you say (the VESA driver) and check as well on the xorg.0.log for what you mention.

However, I did try the MetaMode way, and guess what, nothing happened (but I didn't change from the ATI to the r128 or the VESA drivers, so perhaps that might do something. But then, if just simply switching to the VESA driver allows lower resolutions, then the question is if the MetaMode line will allow higher resolutions as well).

Unfortunately I don't have a CRT monitor at home, nor an LCD external monitor to try. What I can say is that you are right when pressing the Fn F8 keys, they change from LCD flat panel, to external monitor to both, in that sequence. I use it a lot when doing presentations with a projector.

One thing though, when trying to switch resolutions through the gnome screen resolution app, I can see as low as 640x480, but they don't work. I mean, they are options in the list, as well as a fixed 60 hz refresh rate appears as an "option" :), but they don't work. One time, trying to fix this thing, I ended up with only the 1600x1200 option and the 1280x1024 options, none else. Funny isn´t it? But then, after doing something (might have been the dpkg-reconfigure xserver-xorg configuration) things went back to "normal".

I hope you have some success with the xorg maintainer. Perhaps he can look on the win driver for this card (yours and mine). If you can't find it in the Dell website, let me know and I'll send it to you. There must be a way around to having the full range of resolutions available, not just some of either side with a different driver. If they did it in windows, they must be able to do it in Linux. Have you tried the ATI Linux driver posted in their website. It says for Fedora 3, so as I'm not sure it'll work on ubuntu I have not tried it yet.

I'll post again tonight with the other stuff.

One last idea. Can this be a Gnome problem? I mean, may it work differently in KDE? Logic and gathering what I know of X and what you just said says it should not make any difference. But perhaps it might be worth the try...

Thanks once more for the response.

---

### Post by sigmason on 2006-07-07
[http://www.redhat.com/archives/xfree86-list/2003-September/msg00014.html](http://www.redhat.com/archives/xfree86-list/2003-September/msg00014.html)

Nope not crazy I am :rolleyes:

---

### Post by sigmason on 2006-07-07
> **melotron said:**
> Thanks for the response as well.

Currently I'm not in front of the C600 box and won't be before tonight. When I get home I'll try what you say (the VESA driver) and check as well on the xorg.0.log for what you mention.

However, I did try the MetaMode way, and guess what, nothing happened (but I didn't change from the ATI to the r128 or the VESA drivers, so perhaps that might do something. But then, if just simply switching to the VESA driver allows lower resolutions, then the question is if the MetaMode line will allow higher resolutions as well).

Unfortunately I don't have a CRT monitor at home, nor an LCD external monitor to try. What I can say is that you are right when pressing the Fn F8 keys, they change from LCD flat panel, to external monitor to both, in that sequence. I use it a lot when doing presentations with a projector.

One thing though, when trying to switch resolutions through the gnome screen resolution app, I can see as low as 640x480, but they don't work. I mean, they are options in the list, as well as a fixed 60 hz refresh rate appears as an "option" :), but they don't work. One time, trying to fix this thing, I ended up with only the 1600x1200 option and the 1280x1024 options, none else. Funny isn´t it? But then, after doing something (might have been the dpkg-reconfigure xserver-xorg configuration) things went back to "normal".

I hope you have some success with the xorg maintainer. Perhaps he can look on the win driver for this card (yours and mine). If you can't find it in the Dell website, let me know and I'll send it to you. There must be a way around to having the full range of resolutions available, not just some of either side with a different driver. If they did it in windows, they must be able to do it in Linux. Have you tried the ATI Linux driver posted in their website. It says for Fedora 3, so as I'm not sure it'll work on ubuntu I have not tried it yet.

I'll post again tonight with the other stuff.

One last idea. Can this be a Gnome problem? I mean, may it work differently in KDE? Logic and gathering what I know of X and what you just said says it should not make any difference. But perhaps it might be worth the try...

Thanks once more for the response.


If you load the 'ati' driver and you have a Mobility M3, look at your logs and you'll see the r128 subdriver pop.  ati is actually a wrapper so that you don't have to guess which one, they do that for you.

I've tried the ATI proprietary driver on my Dell 8200 with a Radeon 9000, it works okay there, but that driver won't work at all on this Rage Mobility chipset, unfortunately, I actually tried it just in case.

In a sense this is somewhat of a Gnome problem as well, but not directly related.  Se Gnome works kind og old school, it doesn't really come sporting the experience of it's elders.  KDE on the other hand in the Display section under System Settings, actually has a Hardware option specifically for the Dell 1400x1050 Laptop LCD (it's even called that) complete with recommended modeline it drops in xorg.conf.  It also has a HUGE number of ther CRTs and LCDs in there, so you spend less time playing the guess and calculate the modeline game.  In a sense I guess the way Gnome works is the reason why gtf is installed by default...cause you are probably going to need it.  However, KDE has the exact same issues and so does XFce.  If you disconnect the monitor you are done for just the same.  The ONLY advantage I see...and it's a big on is that KDE has the modelines that have worked for others, and it DOES support configuring BOTH the SVGA port and the LCD to work as mirrors or as desktop extensions with 2 seperate resolutions...I have (k/x)ubuntu all installed so I just change sessions and it all works.  Even if you configure for multi-head output in KDE, Gnome can read that same xorg.conf....just the Screen Resolution Applet in Gnome will pop an error on open (it doesn't support that...but the Rage chipset can still mirror with the Fn & F8 key combo.)

I want to add to this, that if you change modes, you'll need to use the key combo again in each mode and it appears to need it even when you dump to the VESA mode when you exit...once you do this key combo to get it working...you need to repeat it when you stop with the buggy output...somewhere somebody didn't dot their Is and cross their Ts.


I did notice 2 more things as well.

1. I was wrong about MetaMode...the XOrg ATI driver DOES say it's ignoring it as it is "not applicable" because my line is for the lower resolution (I didn't see it before)...but that's not revelation, at least I know the driver now accepts MetaMode as a command for sure instead of it acting mute.

2. The KDE multi-head support DOES NOT use MetaMode...that's interesting...but perhaps not valuable to the issue.

sigmason

---

### Post by sigmason on 2006-07-07
Oh joy! ](*,)

So if you use KDE and you do the dual monitor, and you reboot with the laptop screen's resolution set below 1280x1024, LOL, you get a scrambled screen (like we are all trying to fix) on startup and if you do the key combo on it you loose the desktop extension assuming you use the other CRT that way, instead the attached monitor becomes a mirror.  The key combo does get you the laptop LCD back though, but since you did that you lost your control over the attacted monitor.  Also, if you read Xorg.0.log, it shows that it has 2 (count them 2) identical monitors attached to the DDC channels and those monitors happen to be the analog CRT I have attached BUT with a slightly different screen size (which is further proof it's dependent somehow on DDC.)  Also, I've noticed with the shrunk screen size on the laptop display the desktop becomes virtual sized to 1400x1050 WITHOUT the command in the xorg.conf to do so, in all the GUIs.  Moreover, in KDE if you detach with the lower resolution and reattach, because DDC is broken, it thinks there's a THIRD monitor...and your back to square one.  Oh and don't detach the external monitor while still in KDE...you'll crash the KDE Display Settings Applet when you try to refresh it or switch to administrator mode.

Okay now let's try Xubunutu itself some more..:-k

Xubuntu with the KDE generated xorg.conf won't change the Display Settings either with the applet but will let you change the gamma settings.  It also doesn't support the multi-head feature KDE pulled off.  Whoops...yes it does when you find the right applet :D

---

### Post by melotron on 2006-07-07
> **sigmason said:**
> [http://www.redhat.com/archives/xfree86-list/2003-September/msg00014.html](http://www.redhat.com/archives/xfree86-list/2003-September/msg00014.html)

Nope not crazy I am :rolleyes:

No you're not, but in a sense you might be ;) I have tried Red Hat 7 on this same laptop, as well as Mandrake 10 a couple of years ago and as far as I recall, I didn't have this problem. Perhaps i did not fidget much with the resolution as I was just starting to familiarize myself with linux and was searching for a nice distro that would actually work with the hardware in my box (mainly the combo nic modem/ethernet card the C600 brings which Dell brilliantly decided to put in the box and intel shortly after discontinued and unsupported).

---

### Post by sigmason on 2006-07-07
> **melotron said:**
> No you're not, but in a sense you might be ;) I have tried Red Hat 7 on this same laptop, as well as Mandrake 10 a couple of years ago and as far as I recall, I didn't have this problem. Perhaps i did not fidget much with the resolution as I was just starting to familiarize myself with linux and was searching for a nice distro that would actually work with the hardware in my box (mainly the combo nic modem/ethernet card the C600 brings which Dell brilliantly decided to put in the box and intel shortly after discontinued and unsupported).

[https://launchpad.net/distros/ubuntu/warty/+source/xorg/+bug/29970](https://launchpad.net/distros/ubuntu/warty/+source/xorg/+bug/29970)

Nope I'm crazy....we are all alone :) 

Anyway, I've just noticed that if I hit the Fn & F7 combo it fixes the display without even having the external monitor!  However, only after it shrinks the LCD back to it's native resolution image (really small for a 1400x1050 screen.  Unfortunately, when you go back to the text screen you are out of luck.  So DDC is not right with dualhead, the laptop LCD isn't producing DDC results (other brands have that too) and I'll bet there's something about that screen stretching thing that is related to this!

sigmason

---

### Post by melotron on 2006-07-07
> **sigmason said:**
> [https://launchpad.net/distros/ubuntu/warty/+source/xorg/+bug/29970](https://launchpad.net/distros/ubuntu/warty/+source/xorg/+bug/29970)

Nope I'm crazy....we are all alone :) 



This was precisely the "MetaModes" option I mentioned I had tried, and it did not worked for me [-( 

I'll keep looking.

EDIT: BTW, I'd love to see the "Fix Released" solution they mention...

---

### Post by sigmason on 2006-07-07
Hmmm, I just found something else 'interesting' ](*,) 

You CAN'T change modes with the VESA driver from inside KDE/Gnome or X.  If you do, you'll get logged out and when you log back in, it won't be changed.  Until now, I've simply changed the resolutions using xorg.conf.  This ONLY happens with the VESA driver.  Oddly, while it doesn't let you change the modes in the GUI, it DOES work in all the modes it can allow (640x480, 800x600 and 1024x768.)

For a minute I thought I nailed my install and was going to reinstall, but I just took my Desktop Ubuntu CD to another computer, one with a PCI NVidia card...and surprise it does it there too!  So as far as VESA is concerned, check the different modes by changing the display section in xorg.conf.  All you have to do is make the highest or only resolution listed the one you want to test.  Other than this the VESA driver works great.

I could have sworn though, I was able to change that from the GUI at one point, but that test with the NVidia card indicates otherwise.

sigmason

---

### Post by sigmason on 2006-07-07
LOL, :-k (k/x)ubuntu are not the only Linux folks having issues with these video cards and the r128 driver.

I just downloaded a LiveCD based Mandrake 9.2: pclinuxos distro.
Guess what, if you boot it, like knoppix, you get a blank screen with the r128 driver.  Hit Fn & F7 and there you go...it's ready to go!  I looked at the Xorg.0.log and the xorg.conf, all the same issues all the same stuff.

So this is not a (k/x)ubuntu issue, or a debian issue there's something incompatible with our particular model of the Rage chipset or the firmware it's using and the setup of the r128 subdriver.

I also checked the settings I've been using in the modeline against the ATI settings in Windows (with PowerStrip) and I was right on the money, so modeline won't help us.

Guess what, the VESA driver even forces a kick out (Fatal Server error:) just like (k/x)ubuntu....LOL....](*,) It's so touching to know we are all on the same page.

sigmason

---

### Post by melotron on 2006-07-07
Ok. Finally back home. Nice to know you're still trying to find a fix for the problem.


I have done some testing as per your suggestions. First thing was configure the VESA card through the xserver-xorg way. Then i decided to check all the screen resolutions I wanted to be able to be seen. At the end, there is a menu that asks wether you want to give a simple, medium or advanced info input for the Xserver to detect some last info (Hzync and Vzync among others i recall) from the monitor. It says about CRTs, but then I figured that at the time of writing LCDs might not be so common (perhaps I'm utterly wrong!).

The thing is that, first I used the advanced option, and simply hit enter when the refresh rates were shown. After logging out and restarting GDM THE ONLY available resolution was 680x420. Quite annoying.

I decided to redo the xserver-xorg conf and finally got 1024x768, 800x600 and 680x420. However, I also decided to play a little bit more and selected in the screen resolutions menu 1280x1024, 1024x768, 800x600 and 680x420. Then in the last section, went for the medium option, and selected the 1024x768 at 60Hz option as my default resolution for the screen. I got that when restarting GDM. Once again went and changed the default resolution in the last menu (through the medium option) to 1280x1024 at 60Hz, and guess what... I am know seeing 1280x1024. However in the Gnome applet I can see the other lower resolution options, but when I select any one of them and hit Apply, the screen goes bananas and after some seconds, it loggs me out and throws me back to the login screen of GDM at the 1280x1024 resolution.

So in the end, I can use the VESA driver with 1280x1024, but cannot go further down. As well, I can use the same VESA driver with 1024x768 and lower resolutions, but can't go any higher.

I also checked at the xorg.0.log as you said and did find that script which I know copy:

(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read failed

so your ideas are somewhat more confirmed know.

I'll try seeing if addind the MetaModes line does something to allow me to see 1280x1024 as well as 1024x768 with the VESA driver. If that does the trick, well then I guess its allright for me.

melotron

---

### Post by melotron on 2006-07-07
> **sigmason said:**
> LOL, :-k (k/x)ubuntu are not the only Linux folks having issues with these video cards and the r128 driver.

I just downloaded a LiveCD based Mandrake 9.2: pclinuxos distro.
Guess what, if you boot it, like knoppix, you get a blank screen with the r128 driver.  Hit Fn & F7 and there you go...it's ready to go!  I looked at the Xorg.0.log and the xorg.conf, all the same issues all the same stuff.

So this is not a (k/x)ubuntu issue, or a debian issue there's something incompatible with our particular model of the Rage chipset or the firmware it's using and the setup of the r128 subdriver.

I also checked the settings I've been using in the modeline against the ATI settings in Windows (with PowerStrip) and I was right on the money, so modeline won't help us.

Guess what, the VESA driver even forces a kick out (Fatal Server error:) just like (k/x)ubuntu....LOL....](*,) It's so touching to know we are all on the same page.

sigmason


As i still have my Mandrake 10 live and install CDs I went for the Live option (or in this case called MandrakeMove) and tried to check the modelines. However, the system crashed with the "... fatal server error..." rant. It said "no screens were found. No usable screens were found.":confused:  But then, this was not to be expected (or is it?). However, I did installed once the Mandrake 10 full version in this same laptop and worked on it for some time.

So for the time being I can't find any other solutions. I still believe this is not a hardware problem, but rather a firmware one. The ati chipset worked correctly in Red Hat 7, so they (or Dell, in fact I found the Dell Red Hat 7 driver for the ati chipset if you want to check it, my knowledge does not go that far or that deep yet :D) must have found a way through all this fuzz.

melotron

---

### Post by sigmason on 2006-07-08
If you got the fatal server error, were you changing the video modes with the VESA driver loaded?  If you were, then yes it was expected.  Perhaps if that is not the case, are you sure there was a valid xorg.conf going in for the r128 driver or the vesa driver?  Could you have not listed the only 'available' resolution in the Display section.  I'd like to see the Xorg.0.log.

I would love to see the RPMs for the Dell Redhat 7 Driver (or whatever you've got.)  Something isn't right in this Dell/r128 mix for sure.  Even if the hardware is 'right' my experience with Rage chipsets is even ATI knows they aren't quite 'right' :rolleyes: 

I've submitted a bug to X.org, didn't seem too active though.

I've yet to see anything with r128 boot correctly into a video mode below 1280x1024, if we can find one, we can surely figure out why.  I'd even install RedHat 7 just to test it.

Of course, there's another option :twisted: you know you can get Accelerated-X drivers from Xi or swap the C800 video cards for their NVidia counterparts (GeForce2Go in my case with 32Mb.)

---

### Post by sigmason on 2006-07-08
[http://lists.us.dell.com/pipermail/linux-precision/2002-July/000022.html](http://lists.us.dell.com/pipermail/linux-precision/2002-July/000022.html)
[http://www.redhat.com/archives/fedora-list/2004-May/msg07064.html](http://www.redhat.com/archives/fedora-list/2004-May/msg07064.html)
Hmmm....that doesn't sound promising.

---

### Post by melotron on 2006-07-08
> **sigmason said:**
> If you got the fatal server error, were you changing the video modes with the VESA driver loaded?  If you were, then yes it was expected.  Perhaps if that is not the case, are you sure there was a valid xorg.conf going in for the r128 driver or the vesa driver?  Could you have not listed the only 'available' resolution in the Display section.  I'd like to see the Xorg.0.log.

I would love to see the RPMs for the Dell Redhat 7 Driver (or whatever you've got.)  Something isn't right in this Dell/r128 mix for sure.  Even if the hardware is 'right' my experience with Rage chipsets is even ATI knows they aren't quite 'right' :rolleyes: 

I've submitted a bug to X.org, didn't seem too active though.

I've yet to see anything with r128 boot correctly into a video mode below 1280x1024, if we can find one, we can surely figure out why.  I'd even install RedHat 7 just to test it.

Of course, there's another option :twisted: you know you can get Accelerated-X drivers from Xi or swap the C800 video cards for their NVidia counterparts (GeForce2Go in my case with 32Mb.)

Unfortunately, when booting from the Live CD I could not get past the booting process. I simply had no possibility of looking at any xorg.conf or xor.0.log files :(. It is strage, as it did use to work before...

Anyways, you'll find attached the Red Hat 7 driver for the ATI Rage 128 M3 card (which is the one which i have in my box and which I downloaded from the Dell website). As well, I attached the latest Video driver for win2000 which was also downloaded from the Dell website (just to compare). I have no idea how to open this files, and if I get to open them, then I would not be able to understand what they say with my current knowledge. I also updload the driver for Fedora 3 (which in the end is also red hat). I changed the extension of the win2000 file as it was a .exe and would not upload.

After some time trying, the "#%$(/ wasn't able to upload the other two files, so only the redhat rpm with a .zip extension was uploaded. If you wnat the other files, tell me and I can tell you where to get them precisely.

Good luck!

---

### Post by videodrome on 2006-07-09
Does psyke83's response in this thread solve your problem???

[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

Works for me on a ATI Rage Mobility on a Dell Inspiron 8000.

---

### Post by melotron on 2006-07-09
The refresh rate part I have already tried, but not the other options mentioned. I'll try them later when I get back to my box. Thanks for the suggestion! Hope this thing works. It might be what sigmason is looking for! [-o<

---

### Post by sigmason on 2006-07-10
> **videodrome said:**
> Does psyke83's response in this thread solve your problem???

[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

Works for me on a ATI Rage Mobility on a Dell Inspiron 8000.

Much appreciated, but sadly, this does not fix the issue.
There several i8k (this refers to the style Dell laptop) video cards available.  I tested this and it does not help, but then again the ATI Mobility M4 that you have is the 32MB version right?  What these options did do, and I didn't notice this before, was get Xorg to allow me to see all the available video modes that I normally have to force by using modelines.  So that is a step in the right direction.

My bet is, Dell probably changed the video firmware and chipset to make the newer card they distributed in the Inspiron 8000.  I also have an Inspiron 8200 (fully loaded) and that has an Radeon 9000 which I have had to replace twice.  The cards keep producing flawed output in 3D rendering in Windows XP (which is NOT very helpful when you are using the laptop for 3D work & CAD/CAM.)  However, my point is, none of the 3 Radeon 9000s I've seen put in by Dell in my 8200 where the same chipset version or firmware level.  It is very likely that the problem we are experiencing might be related to a specific version which others with similar i8k laptops and even similar video cards don't have.  Sadly, the symptoms of the problem you describe do match our issue.  Just the fix doesn't address the crazy display as much as unlocking the missing video modes.

Thanks,
sigmason

---

### Post by sigmason on 2006-07-10
Thanks to E-Bay, I've ordered the 32MB version of the Mobility M4 chipset video card.  It should be here in a few days.

I'm also going to keep an eye out for another C800 16MB version, and the NVidia 32MB GeForce2Go.  I don't mind spending a little money to get to the bottom of this.

My bet is, if I change the video card...even to the 32MB version...this problem goes away.

sigmason


Scratch that..for my $100.00US I just bought 3 video cards.  Now I've got a NVidia GeForce2Go w/32MB, another ATI Mobility 4 w/16MB and last but not least an ATI Mobility 4 w/32MB.  In a few days I'll find out what works and what doesn't and if not, I've got plenty of spare parts.

---

### Post by JeremyWorst on 2006-07-10
Hmm, now this is interesting.  I have a C800 also, same problem as everyone else here. I tried using dpkg-reconfigure xserver-xorg to change to vesa, banged away at all the stuff I didn't understand, but made sure to asterisk the lower resolutions.  I rebooted and now the system won't accept my username and password.  Oops.

This is off the subject of this thread, but a result of the thread, sort of, but does anybody know how I can recover from this?

Jeremy

---

### Post by sigmason on 2006-07-11
> **JeremyWorst said:**
> Hmm, now this is interesting.  I have a C800 also, same problem as everyone else here. I tried using dpkg-reconfigure xserver-xorg to change to vesa, banged away at all the stuff I didn't understand, but made sure to asterisk the lower resolutions.  I rebooted and now the system won't accept my username and password.  Oops.

This is off the subject of this thread, but a result of the thread, sort of, but does anybody know how I can recover from this?

Jeremy

Nothing 'dpkg-reconfigure xserver-xorg' does should cause you to be locked out.  Now, the question is, does GDM (the screen you type your password and username into) simply tell you you have the wrong password?  Or does it log in, then kick you back to the username and password prompt with no information boxes or warning at all.  If it's the later, you should simply rerun the dpkg command and put yourself back on the ATI card...it's possible to create a non-functional configuration with dpkg, I've managed it before.  If that doesn't help, then please note that by default dpkg will create a backup in the /etc/X11 directory with a crazy date/time based extension (in short, you can go back to your working config by simply copying the old config back to the filename xorg.conf.)

Now, here's the most important part, obviously you can't log in, so in order to fix anything you have at least 2 choices (there are plenty more ways but these are all easy.)
1. Press the key combo CTRL-ALT-F1 which will take you to the standard shell log in, and bypass the GDM login screen.  Assuming the problem is with Gnome/X, this will let you log in.
2. At the Grub boot menu select the Recovery Mode boot option for your kernel.  That mode should not require a log in at all, however, I'm pretty sure that's single user mode so don't try to use your computer like that forever, just fix your files.

In case you don't use Linux from the command line some commands you need to Google (since you could send this forum post I'll assume you have Internet access somewhere):

cp - copy
nano - a simple text editor
sudo - a command prefix that allows you 'root' temporary 
       privledge
cd - change directory
ls - list directoy (a little like the DOS dir command)

With those commands, you should be able to get yourself back online.  Otherwise, you'll need to post your xorg.conf so we can see what went wrong :-| 

sigmason

---

### Post by sigmason on 2006-07-11
Step one in my quest to figure out what's with this and which cards it effects.

A friend has a Dell Inspiron 8200 that bit the dust (motherboard took a bath in Grey Goose) but the spare parts are salvagable.
I yanked his NVidia GeForce4 440 w/64MB.  The card works fine in my Dell Inspiron 8200, but it doesn't work in the Dell Latitude C800 and I DID expect this.  From what I can see, the C800 is a 100MHz front side bus PC with AGP 4x, but the GeForce4 440 is an AGP 8x card and doesn't like Hitachi displays.  So I wasn't thinking this was going to work and I got what I expected.  The system powered up...then immediately shutoff when the AGP bus realized the timing issue.  Also, these NVidia cards (this particular chipset) really work better on Samsung displays and few C800 models had them (if any, most of the Samsung displays were 1600x1200.)  So at least I've confirmed this.  I don't know if this particular NVidia card would work in a C810 (which is a 133MHz front side bus P3) but I hear it works great in the C840 which is actually a P4.

So I guess I have to wait for my E-Bay parts to continue my work on this.  I really want to see if the other ATI Mobility M4 chipset card w/16MB I've ordered has the same issue.  Some of those parts should be here before the weekend. :twisted: 

sigmason

---

### Post by JeremyWorst on 2006-07-11
Since I'm replying from my Latitude, all is now well and your advice was worth its weight in gold.  As you suspected, I simply had a bad configuration.  CTRl-ALT-F1 worked fine, I reran dpkg-reconfigure xserver-xorg and voila it works again.

I'll be following this thread closely and I'm sure you'll eventually solve the ATI video card problem for all of us.

Again, many thanks.

Jeremy

---

### Post by sigmason on 2006-07-14
Well, I got my extra ATI Mobility M4 w/16MB in the mail last night.
Just took apart the laptop and put it in.

Both cards are REV.A00 and BOTH the extra card and my original card have the exact same issue.  So I don't have a bad video card, well, at least not one that's more bad the then rest ;) .

That said, I'm waiting on my 32MB Mobility and the NVidia card.
I hope to see them both soon.  Since my system BIOS is already A23 (the last release for the Dell Latitude C800, and I had this problem with A16 before the BIOS upgrade...I'm still thinking there's something not quite right in this video cards design.)

sigmason

---

### Post by sigmason on 2006-07-15
Okay so I got my ATI Mobility M4 w/32MB and my NVidia GeForce2Go w/32MB in the mail.

I put in the 32MB ATI card first.
I got the exact same results I did with the 2 16MB versions of the card.
So I guess that didn't fix anything at all.
Interestingly this means that it applies to all the ATI cards as they work in this system.

So now it was onto the NVidia.
Interestingly I do have an issue with the NVidia card, but not really a bad issue.
With the NVidia card in the system, Grub needed some adjustment to keep the text on the screen, Windows had no issues with it, nor did the BIOS.
Also, with the nv driver from Xorg loaded, I had similiar problems with the Fn & F7 keystrokes being required to get a reasonable display.
However, the screen would simply reduce to native display resolution in the modes below 1024x768 and require the Fn & F7 to expand the screen the limits of the actual display, there was NO distortion like the ATI cards had.
This is not a serious problem from my perspective, I bet a few settings would fix it right up, or maybe the use of the drivers from NVidia instead of the drivers from XOrg.

That said, there's something wrong with this screen scaling function in the system BIOS as it relates to the XOrg video drivers (both nv & ati).  Neither driver seems to tolerate this function in a reasonable manner.

sigmason

---

### Post by videodrome on 2006-07-17
Oops. Ya know it would help if I read better. I misread. I thought you couldn't get it to run at 1400x1050. But you can. That's it. I was never able to get 1024x768 to run. I just get that totally messed up split screen no matter what I do.

Again, for the record, I am running a Dell Inspiron 8000 laptop with the ATI Rage Mobility M4 32M card under Xubuntu. I used psyke83's aforementioned tweaks to my xorg.conf, and it works at 1400x1050. The driver is set to ATI. No additional drivers were installed. I believe that the driver actually being loaded is the r128. Once in awhile the screen gets garbled for no good reason, but for the most part it works.

Loomis

---

### Post by sigmason on 2006-07-18
> **videodrome said:**
> Oops. Ya know it would help if I read better. I misread. I thought you couldn't get it to run at 1400x1050. But you can. That's it. I was never able to get 1024x768 to run. I just get that totally messed up split screen no matter what I do.

Again, for the record, I am running a Dell Inspiron 8000 laptop with the ATI Rage Mobility M4 32M card under Xubuntu. I used psyke83's aforementioned tweaks to my xorg.conf, and it works at 1400x1050. The driver is set to ATI. No additional drivers were installed. I believe that the driver actually being loaded is the r128. Once in awhile the screen gets garbled for no good reason, but for the most part it works.

Loomis


Well you're right R128 is what the ati wrapper loads for your card.

As for what you are experiencing the same is true for me.
But I can get 1024x768 and you can probably too if your hit the
Fn & F7 key combo...but you'll keep having to do it.

I've finally found a link to all the older BIOS revs for the C800  (which incidently, your Inspiron 8000 has the same motherboard as my Latitude C800) and I'm thinking of trying a downgrade to version 11, which seems to have most of my major concerns addressed and a much older ATI BIOS.  I'm curious to see if that fixes anything.  As the ATI and NVidia video BIOS are actually part of the system BIOS on these laptops, I'll have to see what happens.

It's funny though, the NVidia BIOS descales properly with the video mode change in the XOrg driver, but not the ATI driver.  Someone missed something.  I think I'll try the NVidia provided driver for my NVidia card and see if it descales with that or if Accelerated X had a patch to address this ;) 

sigmason

---

### Post by sigmason on 2006-07-19
Oh nice, typed a nice reply and now it's not posted ](*,) 

Okay let's try that AGAIN!

I've reinstalled the NVidia GeForce2Go in my Dell Latitude C800.
I decided after trying the XOrg nv driver to give the NVidia driver a shot.

Now I was wrong about something, I just spoke with Accelerated-X and despite some rumors I read, NVidia is not involved with them regarding the NVidia custom driver, I guess NVidia made it in house.

Since the card is a GeForce2Go I need to run the nvidia-glx-legacy driver.

I installed it and the first issue was that it didn't detect any mode above 1024x768.  Odd, but not a big deal.  I was able to switch between 640x480, 800x600 & 1024x768 without any problems.  The screen scaling did not descale like the nv driver.  The screen did not get split/scrambled like the ati/r128 driver.  The system didn't need to restart X like VESA driver.  So this is a major improvement (way to go NVidia.)

I snatched the modeline section I got from Kubuntu when I told it I have a Dell Laptop 1400x1050 LCD Panel and put it in in place of the standard XOrg configured monitor.  Suddenly all the modes that the nv driver had detected without editing xorg.conf appeared (not so good nvidia, way to go XOrg.)  I was then able to do what I wanted...I could switch to any supported mode, without descaling, and without rescaling even if I went to a different vterminal and back.

However, regardless of XOrg's presence, I've noticed that with the NVidia GeForce2Go in my system at all, my Linux text screens are all shifted down by 3 lines and therefore the bottom 3 lines of my display are off the display (really ANNOYING!)  This seems to be a Linux kernel issue however.  In PC-DOS it works fine, in Windows 2000 Pro, it works fine, in the BIOS it's fine.  So this is a kernel video issue, because the Grub screen is fine.  Also, I've noticed if I boot into version 2.6.15-23-386 of the kernel this doesn't happen :-k so someone done messed something ELSE up.

So that said:

1. I have just proved Linux can get this to work from software on the Dell i8k platform.
2. We know that NVidia must know how, cause they did it.
3. We know that this can be fixed.
4. We know that the XOrg ati/r128 and nv driver DO NOT like the screen scaling function one bit.

Now, at this point I'm running out of tricks for the faint of heart.

1. I can still try a major BIOS downgrade, but I'm not hopefull.
2. I can try RedHat 7.0, but I don't think it worked right with the ATI chipset either, I think that is bad information.
3. I can try the Accelerated-X drivers (they have a 25 minute demo.)

Sadly, it's looking like the legacy of bad Linux support for ATI chipsets is biting us.  Too bad ATI doesn't want to address their older cards with a driver.  Oh well, maybe I'll have better luck with the Accelerated-X driver.  I don't think XOrg will have a chance to address this screen scaling issue anytime soon.

sigmason

It's really too bad that for the cost of <$40.00 it doesn't make any sense to do what I'm doing to get this ATI card working.  The  NVidia card which is <$40.00 does work, and has drivers that work and is not that hard to put in or install the drivers for.  It's a shame that ATI didn't address the older cards with Linux support and that XOrg hasn't noticed the screen scaling issue.

---

### Post by sigmason on 2006-07-19
Oh and by the way, with the NVidia GeForce2Go in my Dell C800 I had to put the vga=771 kernel loading option into the Grub menu.lst file.  That resolved my issue with the text displaced off the bottom of the screen, and that wasn't even an XOrg problem (it happened even in recovery mode.)  So I guess there's an issue with the NVidia BIOS detecting the LCD panel's settings, given that the XOrg server couldn't find any setting about 1024x768 either.

BUGGY! ](*,) 

sigmason

---

### Post by sigmason on 2006-07-19
Adding to my list of helpful pointers, if you switch to the NVidia GeForce2Go in the C800:

When using Xinerama, for dual display instead of TwinView use:

Option "IgnoreDisplayDevices" "DFP"

in one Device section and

Option "IgnoreDisplayDevices" "CRT"

in the other respective device section.

Seems that non-functional ability for the Dell BIOS to tell which is which will otherwise make your dispaly go crazy...and yes I can attest to it, I just tested this.

It's pretty funny, XOrg actually puts sections on the same monitor without this.

sigmason

---

