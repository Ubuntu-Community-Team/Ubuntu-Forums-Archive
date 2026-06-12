---
title: "Where is &quot;Screens &amp; Graphics&quot; in 8.10"
date: 2008-10-31
forum: Hardware
---

### Post by mcgo on 2008-10-31
"Screens & Graphics" is missing from the Application>Other
menu. Fault or design?

---

### Post by cariboo on 2008-10-31
Screens and Graphics is no longer needed in Intrepid as Xorg auto senses your monitor. I have tried it out, and it works quite well. I normally use an Acer lcd monitor, but when I tested the compouter after blowing all the dust out I connected it to a 19" crt the crt was detected and resolution was set to 1600X1200. If you need to adjust the resolution try System-->Administration-->NVIDIA X Server Settings

Jim

---

### Post by mcgo on 2008-10-31
> **cariboo907 said:**
> Screens and Graphics is no longer needed in Intrepid as Xorg auto senses your monitor. I have tried it out, and it works quite well. I normally use an Acer lcd monitor, but when I tested the compouter after blowing all the dust out I connected it to a 19" crt the crt was detected and resolution was set to 1600X1200. If you need to adjust the resolution try System-->Administration-->NVIDIA X Server Settings

Jim

OK when it works, but it didn´t find my onboard NVidia graphics or
my 1024x768@70hz Phillips Monitor, Sad 8^((

---

### Post by CalcProgrammer1 on 2008-10-31
> **cariboo907 said:**
> Screens and Graphics is no longer needed in Intrepid as Xorg auto senses your monitor. I have tried it out, and it works quite well. I normally use an Acer lcd monitor, but when I tested the compouter after blowing all the dust out I connected it to a 19" crt the crt was detected and resolution was set to 1600X1200. If you need to adjust the resolution try System-->Administration-->NVIDIA X Server Settings

Jim

LOL HAHAHA OMG FUNNY I'm rolling on the ground laughing!!! No, seriously!

COME ON!  Keep Screens and Graphics in!  The so-called autodetection thing DOESN'T WORK 100% and, face it, will NEVER work 100%.  The xorg system is too based on xorg.conf and the mess of drivers that all have different abilities to ever detect all systems perfectly.

The autodetection worked fine on my new laptop and desktop on 8.04 and 8.10, no problems here, HOWEVER, on my old laptop (IBM ThinkPad A21p), the idiot thing thinks my 1600x1200 monitor is a pathetic 800x600 and won't go higher.  The ONLY way to fix it was to use SAG in 8.10, because it knew how to rewrite the xorg.conf file to eliminate the failing autodetection thing.  The PC has an ATi Rage Mobility 128 M3 16GB graphics chip using the "ati" driver, but it is stuck with generic VESA with the autodetect.

How do you get Screens and Graphics back in 8.10?  It's obviously not installed, so where can I get a .deb of it to install?

FYI:  If you're going to eliminate a configuration system in favor of an automatic detection system, only do so if you're 100% sure that the autodetect will not mess up on ANY system that users may want.  If this is not the case, leave the configuration in, just hidden...or better yet, make a new Screens and Graphics that allows you do choose Automatic or Manual configurations and change settings as necessary.

As for your case with the nVidia Settings, it only works if you have a newer nVidia card.  Many people don't have these.  nVidia's settings is awesome, but relying on it instead of the system default isn't a good idea, those who are using older cards, ATi cards, Intel cards, etc, lose the capability to configure stuff.

---

### Post by ben@layer on 2008-10-31
bumb me to that auto thing s#$%'s

---

### Post by ill1cit on 2008-10-31
Yeah I am having a similiar problem. It doesn't detect my plasma screens res and I can't work how to change it.

---

### Post by mcgo on 2008-11-01
> **CalcProgrammer1 said:**
> LOL HAHAHA OMG FUNNY I'm rolling on the ground laughing!!! No, seriously!

COME ON!  Keep Screens and Graphics in!  The so-called autodetection thing DOESN'T WORK 100% and, face it, will NEVER work 100%.  The xorg system is too based on xorg.conf and the mess of drivers that all have different abilities to ever detect all systems perfectly.

The autodetection worked fine on my new laptop and desktop on 8.04 and 8.10, no problems here, HOWEVER, on my old laptop (IBM ThinkPad A21p), the idiot thing thinks my 1600x1200 monitor is a pathetic 800x600 and won't go higher.  The ONLY way to fix it was to use SAG in 8.10, because it knew how to rewrite the xorg.conf file to eliminate the failing autodetection thing.  The PC has an ATi Rage Mobility 128 M3 16GB graphics chip using the "ati" driver, but it is stuck with generic VESA with the autodetect.

How do you get Screens and Graphics back in 8.10?  It's obviously not installed, so where can I get a .deb of it to install?

FYI:  If you're going to eliminate a configuration system in favor of an automatic detection system, only do so if you're 100% sure that the autodetect will not mess up on ANY system that users may want.  If this is not the case, leave the configuration in, just hidden...or better yet, make a new Screens and Graphics that allows you do choose Automatic or Manual configurations and change settings as necessary.

As for your case with the nVidia Settings, it only works if you have a newer nVidia card.  Many people don't have these.  nVidia's settings is awesome, but relying on it instead of the system default isn't a good idea, those who are using older cards, ATi cards, Intel cards, etc, lose the capability to configure stuff.

How about when a NVidia GeForce6100 nForce 405 with a bias date
of 12/2006 isn´t found. Liked your post but someone´s got to get
a handle on what is considered old because the average user changes desktops(my case) every 5 years if the fatest CPU is not twice as fast as his existing computer(AMD64 x2 5200+ in my case) Thx again for the ray of sunshine:)

---

### Post by jhenager on 2008-11-01
I am stuck with 800x600 with icons as big as my head. That'll teach me to upgrade right away, I guess.
I have an integrated nVidia 6xxx chip. The ASRock manual doesn't specify which one, but it looks like I missed the bus.

---

### Post by overdrank on 2008-11-01
Hi and I was testing on a system with a nvidia 6100 chipset and no issues. Have you tried using a older driver than the 177.XX?

---

### Post by mcgo on 2008-11-01
> **overdrank said:**
> Hi and I was testing on a system with a nvidia 6100 chipset and no issues. Have you tried using a older driver than the 177.XX?

Running the older! I can´t get a download on 177, computer
just sits there 8^(( No anger intended 8^))

---

### Post by laurielegit on 2008-11-01
This whole argument that Xorg works is ridiculous. Even if it does work 99% of the time you still don't get rid of the other option. Please bring this back.

---

### Post by Yellow Pasque on 2008-11-01
You can always configure your monitor through xorg.conf. For example, my monitor doesn't autodetect (because it doesn't send EDID through DVI properly).

Generate a mode line with cvt. For example:
```
cvt -v 1680 1050 60.0Hz
```
returns
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

So I copy the Modeline part and edit my xorg.conf (gksudo gedit /etc/X11/xorg.conf)
I paste the Modeline into the Monitor section.
```
Section "Monitor"
	Identifier   "VX2025wm"
	VendorName   "ViewSonic"
	ModelName    "VX2025wm"
	Option	     "DPMS" "True"	
	Gamma        1
	ModeLine     "1680x1050@60.00" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync
EndSection
```

For those stuck with the VESA driver, edit the Device section to pick your driver. I use the open-source radeonhd driver, so mine looks like this:

```
Section "Device"
	Identifier  "Device"
	Driver      "radeonhd"
	BusID       "PCI:1:5:0"
EndSection
```

---

### Post by dpaint4 on 2008-11-01
It absolutely MUST be brought back. Auto-detection fails, and I'm stuck working on my graphics projects at a ridiculously low resolution. I always used that tool in the past to force Ubuntu to use the correct resolution for my monitor.

Is there some way to add it back to my OS? I'm lost without it.

---

### Post by PendragonUK on 2008-11-02
At least you can see something, auto detection is so bad my LCD shuts down and I'm looking at the Black Screen of Death!!!

---

### Post by mcgo on 2008-11-02
> **mcgo said:**
> Running the older! I can´t get a download on 177, computer
just sits there 8^(( No anger intended 8^))

My post here was/is BS. Sorry about that. Put my anger aside,
checked xorg.conf and found absolutely nothing had been detected.
Which, in reality, changes nothing. I must, however, say I should
not have answered until I exhausted every possibility and am
truly sorry about that!

Walking in a giant world with a very small screen!

---

### Post by sdavmor on 2008-11-03
> **laurielegit said:**
> This whole argument that Xorg works is ridiculous. Even if it does work 99% of the time you still don't get rid of the other option. Please bring this back.

I'd love to have "Screens & Graphics" back in Intrepid.  My aging laptop is a Toshiba Satellite Pro 4600.  I had it running fine on Hardy by fixing the xorg display (it has a Trident Cyberblade XP graphics card).  "S&G" made doing that pretty easy.  I should have written down all the X settings before upgrading to 8.10 this weekend but I didn't because it didn't occur to me that "S&G" would have vanished -- serve me right.   Now I'm back at 800x600 on a dinky screen. I guess it's time to roll up the shirtsleeves and hack at it via a terminal as suggested by Temüjin. [sigh]

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by sdavmor on 2008-11-03
I didn't wind up having to go to the lengths suggested by Temüjin, but it did take a little grunt-work to get my screen resolution to 1024x768.

Here's what I wound up with in xorg.conf for my Trident Cyberblade XP card.  It applies to Intrepid 8.10 Ubuntu, and hasn't been checked on any other 8.10 variants.  But it's so basic that it should be enough to get there regardless of Ubuntu flavour.  And it should provide enough clues for anyone looking to troubleshoot other cards that won't let you ask in "Screen Resolution" for more than 800x600.

Section "Device"
Identifier "Trident Microsystems Cyberblade XP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizonSync 28-31
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Generic Monitor"
Device "Trident Microsystems CyberBlade XP"
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 32
Modes "1024x768"
EndSubSection
EndSection

It took me a while to get to that. I actually had more stuff in there but things kept blowing up on boot. So it was a case of less-is-more, removing settings that caused video to crash on boot (it dropped me into the log) to arrive at just enough in xorg.conf to access all the screen and provide for various bit depths. You may not even need the 8 & 16 bit sub sections under "Screen".

If you find that your screen comes up in 1024x768 at the login prompt, but drops back into 800x600 after you login, you should go into System-->Preferences-->Screen Resolution and select 1024x768 which should now appear in your menu. Don't be alarmed if that happens the first time you boot up after getting it set correctly.

If you want higher resolutions than 1024x768, just add them in under "Modes" using the above as a guideline.   

HTH those as aggravated as me by the absence of "Screens & Graphics" in 8.10.

:guitar: SDM (Systems Theory internet music project)
[http://systemstheory.net](http://systemstheory.net)

---

### Post by theduffman on 2008-11-04
[QUOTE=Temüjin;6081579]You can always configure your monitor through xorg.conf. For example, my monitor doesn't autodetect (because it doesn't send EDID through DVI properly).

Generate a mode line with cvt. For example:
```
cvt -v 1680 1050 60.0Hz
```
returns
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

So I copy the Modeline part and edit my xorg.conf (gksudo gedit /etc/X11/xorg.conf)
I paste the Modeline into the Monitor section.
```
Section "Monitor"
	Identifier   "VX2025wm"
	VendorName   "ViewSonic"
	ModelName    "VX2025wm"
	Option	     "DPMS" "True"	
	Gamma        1
	ModeLine     "1680x1050@60.00" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync
EndSection
```


interesting... my laptops widescreen screen size is 1680x1050 also, and this +vsync option might be what i was looking for to fix the tearing issue in games/videos.  Im not currently able to test it but would this fix it?

---

### Post by Yellow Pasque on 2008-11-04
> **theduffman said:**
> Interesting... my laptop's widescreen screen size is 1680x1050 also, and this +vsync option might be what i was looking for to fix the tearing issue in games/videos.  I'm not currently able to test it, but would this fix it?

Probably not. In fact, if your monitor does 1680x1050 without any hacking/configuring, then I would guess that X.org is already reading that information directly from your monitor's EDID (1680x1050 is not a VESA-compliant resolution).

Video tearing... Hmmm, let me guess - you're running fglrx/Catalyst?

---

### Post by theduffman on 2008-11-05
> **Temüjin said:**
> Probably not. In fact, if your monitor does 1680x1050 without any hacking/configuring, then I would guess that X.org is already reading that information directly from your monitor's EDID (1680x1050 is not a VESA-compliant resolution).

**Video tearing... Hmmm, let me guess - you're running fglrx/Catalyst?**

Yes.  Its a common problem thats not got any fix i take it?
great

---

### Post by RobHK on 2008-11-10
> **dpaint4 said:**
> It absolutely MUST be brought back. Auto-detection fails, and I'm stuck working on my graphics projects at a ridiculously low resolution. I always used that tool in the past to force Ubuntu to use the correct resolution for my monitor.

Is there some way to add it back to my OS? I'm lost without it.


I second what the above posters have been saying.

My Fujitsu Siemens Esprimo laptop needed special SiS drivers and took a lot of setting up in 8.4, but I eventually did it. I upgraded to 8.10 and it has destryed my settings.

I went through the routine I'd used in 8.4 again, but I can't get the proper resolution back because I can't access Screens and Graphics.

As for fiddling with xorg.conf, I don't know how to. I just want to use my computer, like I did before Intrepid screwed it up.

---

### Post by wgrant on 2008-11-10
Have you looked at [the documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

---

### Post by RobHK on 2008-11-11
> **wgrant said:**
> Have you looked at [the documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

Thanks, I'll check it out. Though I'm not crazy about getting into a lot of command line stuff. Screens and Graphics previously allowed me to find the settings I needed, once I'd installed the drivers.

I think I'm going back to 8.4.

---

### Post by davidgeeee on 2008-11-11
Just in case this helps someone that found this thread, here is how I fixed my screen resolution with 8.04.  

First my graphics adapter and monitor were not detected.  Tried all kinds of edits to xorf.conf with no success.  

The Fix for me was this:

I used a 7.04 live CD to boot into Ubuntu (not install).  The resolution was set to the highest my monitor could handle. Detected my graphics card correctly. Checked in "Screen Resolution" utility and all the resolutions were there.  So, I copied xorg.conf to a USB drive.  Restarted 8.04 and made a backup of the current(faulty) xorg.conf file. Then I copied the sections of xorg.conf (from 7.04) that were about the graphic card and monitor and modes to the xorg.conf of the 8.04 installation.  Restarted X and everything was peachy!  

I may try this with 8.10 today, but I am pretty sure it will work there too.  

Hope this helps someone that has been banging their head like me!:)

---

### Post by mcgo on 2008-11-11
> **wgrant said:**
> Have you looked at [the documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

Used xrandr to check settings after loading old nvidia "nv" driver
and found the resolutions above 1024x768 are truncated at 60.0,
in 8.04 they reach 85.0. Any idea why? And I´m another that does´nt
like mucking around in terminal if there could be a gui solution.

---

### Post by mcgo on 2008-11-14
Loaded Ultimate Edition and questioned auto xorg.
Got a solution for nVidia 173, 177 users. Downlaod the
correct drivers and load them. Activate the module on Admin>nVidia
and follow the intructions. Reboot x, ctrl+alt+backspace.
then go to terminal sudo nvidia-settings and ajust for your
monitor/driver. Worked on the first try. Forget Screen Resolution.
I found my settings by running the live 8.04 CD. Walk in the park!
For me this issue is SOLVED

Quoting LeadFingers on the Ultimate 2.0 site:
Re: What I hope I don´t see in 2.0 - auto xorg.conf

"Just remember, the big trick is to open it up as root.
if you don't ,it won't write your changes to xorg.conf."

---

### Post by dugb on 2008-11-15
> **wgrant said:**
> Have you looked at [the documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

Yes, I looked at this link you provided. Like most here, command line is not what we want to do. I ran 'xrandr' and it displayed what I expected it to display (a maximum resolution of only 800x600). I ran the next line from the documentation to try to get it to use a larger resolution and nothing happened. The resolution I selected is in the xorg file. It is extremely disappointing after trying Ubuntu to be discouraged from its continued use because of bugbears like this. It should be easy, but instead we are expected to become command line junkies

---

### Post by Yellow Pasque on 2008-11-15
dugb,
Have you tried generating modelines with cvt as I posted earlier in the thread?
> It should be easy, but instead we are expected to become command line junkies Please stop exaggerating... You're not being asked to read through technical man pages, you're being spoon-fed commands to copy and paste. If you want everything in a GUI, then get Mac OS X. (Of course, you have to pay a significant "Mac tax" and your hardware selection is limited).

---

### Post by dugb on 2008-11-15
Thanks for your reply Temujiin. I did follow your instructions and pasted the Modline into xorg, saved it, re-logged in and checked if the new resolution is available...it is not and has made no changes to the list of 2 minimum resolutions available.

I also re-booted the PC...each time I do (even from first boot after upgrade) I get an error message advising running in low graphics mode: (EE)intel(0): no valid modes (EE)screen(s): found, but none have a usable configuration. 

With regards to command lines, I have 2 PC's and in every install of Ubuntu (total =5) I have had to research the web for answers to problems and done command line work to get screen resolution and onboard LAN to work...I exaggerate not.

---

### Post by pullapint on 2008-11-15
This solved it for me. Alt-f2, gksudo nautilus, renamed my current xorg.conf file to xorg.confold. I copied my xorg.conf file from another distro into /etc/x11 and reboot.
I do agree, a gui settings manager for resolution would have been helpful.

---

### Post by coolethan on 2008-12-10
thanks so much this worked out great. i now have working resoltuion on my computer. i used the xorg.conf file from the 7.1 live cd and completely replaced the one in 8.1. why is it that 7.1 should have better auto detection for my screen than 8.1?

---

### Post by ummduh on 2008-12-21
Just wanted to say...


[SIZE="7"]I quit![/SIZE]

:confused:

This was the last straw. I'm not a newb to figuring things out but Linux/Unbuntu is a PIA. Now I'm stuck at 800x600 and I can't do anything about it.. Already have researched and played with it for the last few hours..

Oh well. I'll revisit you guys in another 2 or 3 years and see if it got any better.. I'm off to reclaim 3 partitions worth of HD space!:guitar:

---

### Post by dugb on 2008-12-21
LOL...

I quit too. I found developer's thread where they kept going off track and seemed to not provide an answer to the problem. In the end, they said fixed and create a new bug for the other defect. Which was all gobbldygook to me as they never said what part was fixed and what the new defect they officially raised was. So, I went back to Ubuntu 8.04. Sad when a new version regresses.

---

### Post by coolethan on 2008-12-21
hold on you guys i figured it out it was easy as pie and it only takes 10 minutes tops. what you gotta do is just use the live cd from an older version which registered your resolution properly or you were able to do so with screens and graphics. find the xorg.conf file on the live cd and then just copy the file and put it into the appropriate file in 8.10 which should be X11 and remove the other xorg.conf file. reboot and thats all you gotta do.

---

### Post by mulder_edu on 2009-01-03
Hey.  That worked great.  Just copied and pasted the xorg.conf file from 7.10 into 8.10 and it works great.  Thanks for the idea!

System is a Portege 4010.

---

### Post by ligerzero459 on 2009-01-03
Could someone post a copy of that xorg file as an attachment? I don't have a previous live CD and have no way to get one.

---

### Post by coolethan on 2009-01-03
whats your resolution? i need to know so i can set it up properly to fit your screen.

---

### Post by ligerzero459 on 2009-01-03
1024x768

---

### Post by coolethan on 2009-01-03
there may be a small problem with different graphics cards than i have. i have a rage 128 which is horribly prehistoric and xorg.conf uses that info to properly set up my screen. i would copy your current xorg.conf file somewhere first before attempting to use the one i'm attaching. keep in mind that this may just as easily horribly disfigure your monitor setup as actually fixing your problem. personally i would try all the other options posted in this forum before trying this. good luck.

---

### Post by ThomasArildsen on 2009-03-02
> **RobHK said:**
> I second what the above posters have been saying.

My Fujitsu Siemens Esprimo laptop needed special SiS drivers and took a lot of setting up in 8.4, but I eventually did it. I upgraded to 8.10 and it has destryed my settings.

I went through the routine I'd used in 8.4 again, but I can't get the proper resolution back because I can't access Screens and Graphics.

As for fiddling with xorg.conf, I don't know how to. I just want to use my computer, like I did before Intrepid screwed it up.

I am currently experiencing the same problem as you. I have an Esprimo laptop as well with SiS 761 graphics. I also got lost after upgrading from 7.10 to 8.10, of course without backing up my xorg.conf ](*,)
Did you succeed in setting it up for your Esprimo, and could you tell me how?

Thomas Arildsen

---

### Post by JonNiccolls on 2009-03-03
coolethan, mulder_edu, you are diamonds!!

I have a Portege 4010 too and it's been driving me nuts that I can't get the full screen working

Thanks a lot guys!!\\:D/

---

### Post by stchman on 2009-03-03
> **mcgo said:**
> "Screens & Graphics" is missing from the Application>Other
menu. Fault or design?

I don't think there has been a Screens & Graphics option in Ubuntu.  I have been using Ubuntu since Edgy.

Yes, once your Nvidia drivers are installed the correct resolution (if LCD) is selected for you.

---

### Post by PaulHuffman on 2009-03-05
I plugged a 1680 x 1050 LCD monitor into my 8.04 system, but haven't been able to get that kind of resolution out of it. Because this monitor was never on this system, I don't think it would be helpful for me to go back to my 7.* xorg.conf.  

But I ran [[COLOR="DeepSkyBlue"]FONT="Courier New"]cvt 1680 1050 60[/FONT][/COLOR], got a modeline of [COLOR="DeepSkyBlue"][FONT="Courier New"]Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/FONT][/COLOR]

Then tried  [COLOR="DeepSkyBlue"][FONT="Courier New"][FONT="Courier New"]xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960[/FONT] 2240  1050 1053 1059 1089 -hsync +vsync [/FONT][/COLOR] and xrandr shows a new mode when I type xrandr without arguments. 

I thought I was almost there but what do I put in for --output? [COLOR="DeepSkyBlue"][FONT="Courier New"] xrandr --output VGA-O --mode  1680x1050_60.00[/FONT][/COLOR]  didn't make a change to my screen.

---

### Post by RobHK on 2009-05-31
> **Temüjin said:**
> dugb,
Have you tried generating modelines with cvt as I posted earlier in the thread?
 Please stop exaggerating... You're not being asked to read through technical man pages, you're being spoon-fed commands to copy and paste. If you want everything in a GUI, then get Mac OS X. (Of course, you have to pay a significant "Mac tax" and your hardware selection is limited).

He's not exaggerating. He's a computer *_user_* who wants to * _use_* his computer, not spend his life setting it up.

If you want Linux to be for a nerd population of 1% keep up that attitude. If you want ordinary people to use it to replace Windows then encourage user-friendliness.

And we don't want to be spoon-fed commands, because it may solve the immediate problem but blindly copying doesn't help understanding. With a GUI you can find your way back to resolve similar problems another time. And don't give us the crap about Macs. 95% of the world has Windows. Numerically that's the only competition worth looking at.

---

### Post by RobHK on 2009-05-31
> **ThomasArildsen said:**
> I am currently experiencing the same problem as you. I have an Esprimo laptop as well with SiS 761 graphics. I also got lost after upgrading from 7.10 to 8.10, of course without backing up my xorg.conf ](*,)
Did you succeed in setting it up for your Esprimo, and could you tell me how?

Thomas ArildsenHi Thomas,
I've only just seen your post as I gave up on this and went back to Vista-only on the laptop.

However the good news is that Ubuntu 9.04 works out of the box on the Fujitsu! Not only screen but wireless as well.

---

