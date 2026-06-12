---
title: "Hardy - Lenovo T61 Nvidia dual monitor support"
date: 2008-08-18
forum: Hardware
---

### Post by mrbrice on 2008-08-18
Greetings,

I'm running Hardy 8.04.1

Linux darkhelmet 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


I have a Lenovo Thinkpad T61 running a NVidia NVS 140 graphics card.

My xorg.conf is quite basic, but shows;

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


I've looked through a great number of posts on this forum and random google searches regarding this laptop, but most of the articles speak about an Intel card instead of the nvidia i have, or the instructions regarding the laptop/vid card combo is relating to older versions of ubuntu. 

I tried following all the instructions for each, but none of it worked. 

What i'm trying to do is have an extended desktop. 

Could someone please explain to me or point me towards some recent documentation regarding my setup? I'd really appreciate any assistance anyone can give.

If you require any more information, please ask. 

Cheers,

---

### Post by pwnprog on 2008-08-18
hey man. i've been able to get this working before. i'll post a how-to for you later on and we'll see if that works.

quick question first though, do you have nvidia-settings installed? that typically makes stuff like this easier. if not, go into terminal and type sudo apt-get install nvidia-settings . that's a good first step if you haven't done that yet.

---

### Post by mrbrice on 2008-08-18
> **pwnprog said:**
> hey man. i've been able to get this working before. i'll post a how-to for you later on and we'll see if that works.

quick question first though, do you have nvidia-settings installed? that typically makes stuff like this easier. if not, go into terminal and type sudo apt-get install nvidia-settings . that's a good first step if you haven't done that yet.

omg, that's all it took. 

nvidia-settings ftw. 

Thanks so much dude.:)

---

### Post by mrbrice on 2008-08-18
Well, dual monitors is nice, but for some reason when running with dual monitors, it disables my visual effects for my desktop appearance. When I try to select the 'normal' setting, it says "The Composite extension is not available" now. :(

Can't switch screens with the scroll wheel or move windows over anymore. That's a bummer. 

Wouldn't happen to know why it would disable that would you?

I have:

Section "Extensions"
Option "Composite" "1"
EndSection 

in my xorg.conf


Still says it's not available.

---

### Post by pwnprog on 2008-08-18
hmm... that depends. are you using twinview or separate x-screens? 

also, i learned the hard way that for options where it says requires x restart, it really means it! for that, you firstly need to save your settings to the x configuration file, and then log off and log on again. this could make a difference if you haven't already tried that.

also... while saving to the x configuration file, it may say that you don't have the proper privileges. if this is the case, you should open your nvidia settings via terminal by typing sudo nvidia-settings . your nvidia thing should open up like it normally does, but this time you have administrator privileges.

hopefully that may help you along. if not, let me know.

---

### Post by pwnprog on 2008-08-18
and by the way... here is the how-to i was talking about. it's not for dual monitors, but it was for single display on my television using an s-video cable. perhaps this might be enough to give you a push in the right direction for finding a solution to your problem. i can't imagine it would be much different in your application. it seems like it would be a matter of simply choosing a different setting in your nvidia-settings.

if its still not working, post a step-by-step of what you are doing and i'll see if i can make a suggestion.


in other news... ubuntu needs to have MUCH BETTER dual/external monitor support for laptops. i've never been in a situation yet where the good ol function+f4 actually worked the way i wanted it to. i'm sure you're feeling the same right now!

anyway.... heres the how to:


1.In terminal, enter sudo nvidia-settings
2.type in password
3.click xserver display configuration
4.connect computer to tv via svideo cable
5.click &#8220;detect displays&#8221;. Tv0 should show up in the image beside your original monitor, but should not be physically displaying anything.
6.Click on the tv0 screen in the layout viewport
7.click configure and select &#8220;separate xscreen&#8221;
8.click on your original monitor, and click configure again
9.click disabled and click ok. When asked if you would like to disable the monitor, accept this. This will not turn off the monitor immediately, but it will once you logout and log in again.
10.Click &#8220;save to x configuration file&#8221;. When the dialog box pops up, make sure that &#8220;merge to existing file&#8221; is checked. Click save
11.Quit out of everything.
12.Log out.

Voila! Now the tv should be displaying your monitor without any weirdness and glitches. Log in and do as you please with the tv displaying things in its default resolution mode. When you want to switch back to the regular monitor, follow the same steps except having your normal monitor as separate xscreen, and tv0 disabled.

---

### Post by mrbrice on 2008-08-19
Well, 

I'm able to get dual monitor/extended desktop working, but i have a choice it seems.

* Using nvidia-settings worked perfectly for me to get this up and running in case anyone else has a similar issue.

If I choose the 'seperate x screen' option (which is what I want) for my second display, and I save the config and restart x, i have two (2) displays (excellent), and my visual appearance settings are still intact, however afterwards the video seems to run sluggish. 

If I choose the same 'seperate x screen' option and I enable Xinerama, it looks and runs quite smoothly, however, my visual appearance settings get set to default and I no longer have any of the cool effects that come with it. If I try to enable them, it proceeds to tell me "The Composite extension is not available". Unfortunately, even if I enable this in my xorg.conf it will still not work.

So I'm assuming it just doesn't work with Xinerama (lame). 

I'm not sure why it would run sluggish without xinerama enabled, but I'm fine with not having the cool effects that come with the visualization settings. Wish I could use them as well, and if anyone has an idea how to let me have my cake and eat it too, that'd be great.

Otherwise I guess I'll survive. :)

Thanks again for your assistance pwnprog

---

### Post by pwnprog on 2008-08-19
are you using compiz for your desktop effects?

---

### Post by mrbrice on 2008-08-19
> **pwnprog said:**
> are you using compiz for your desktop effects?

I would say yes, as compiz is installed, but I'm not sure. 

I'm using whatever gnome uses for System > Preferences > Appearance by default.

---

