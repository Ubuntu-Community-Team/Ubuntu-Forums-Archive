---
title: "ATI Video Cards and xorg.conf"
date: 2009-08-04
forum: Hardware
---

### Post by johntrottier on 2009-08-04
There are a huge number of threads as to how to modify your xorg.conf file to use the abilities of the fglrx driver for ATI cards. After the battle I just had, I wanted to pass along some observations.
I'm running 8.04 on a older Dell box with an ATI graphics card. When I first installed Ubuntu, I was trilled and impressed at how easily the proprietary driver was installed, how easily I was able to download and install the ATI Catalyst control center, and how easily I was able to configure my Big Desktop. Getting this to happen on OpenSuse (my previous distro) had been a long hard slog. I got it, but it was no fun at all.

What Happened:
I had my mother in law coming over, and I wanted to set her up on the machine, so I created a new user and went to customize her desktop
Disaster struck!!!!
Using the controls in system>preferences>screen resolution I went to adjust her screen. This immediatly distroyed the Big Desktop, wasted the screen resolution and generally trashed the whole system. This affected not only the new user account, but my original account as well.:confused:

What I did:
I spent more than a few hours over the next several days insralling and uninstalling the propriatary driver, and following various how-to's as to how to set up xorg.conf, all with little to no luck. No matter what I did, I could not get back to where I had been.
Finally, I gave in, reloaded the OS and bang!! - there we were
In a hour and a half (inluding downloading and installing all upgrades) I was back on line.
So the first thing I do is go to xorg.conf and so I can make a copy and never, ever, have this happen again.:grin:

When I open it up - I get a rude shock. There is no configuration there. The file does not descibe my monitors, it does not call out the options all the how-to's say are needed, it does not even show I have two devices!! :confused:

So could the real heavies out there explain what is going on? All I can guess is that there are things happening in the kernal when the propriatary driver is installed, and that bypasses the xorg.conf file. Using the system tools corrupted that connection, and the only fix was a kernal hack or a reload.
I'm happy it's up and running, but it should not be like this.

---

### Post by tgalati4 on 2009-08-04
If you went from 8.04 to 9.04, then yes, things have changed.  Xorg.conf is now a simple file and almost everything is auto-configured.

You can still add switches to xorg.conf, you just need to know what they are.  For instance to save some power on a thinkpad laptop with an ati card, you can turn on dynamic clock scaling:  (my entire xorg.conf)

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"DynamicClocks" "on"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#	Option		"VertTwoFingerScroll"	"1"
#	Option		"HorizTwoFingerScroll"	"1"
#EndSection

---------------

Of course, you saved your previous user-modified configuration files to a flash disk so you have all of those switches handy.

---

### Post by johntrottier on 2009-08-04
Nope - still 8.04 Just went back to where I was before "the troubles"  What I want to know is where the big desktop is being configured from if it's not in xorg.conf!!!!

---

### Post by latev on 2009-08-05
No offence but reading your post reminds me of my old ATI days and I'm so happy I'm not you right now!

This has always puzzled me - how can something that works fine at one moment be so easily and mysteriously and badly broken in the next.

Setting up my ATI card under Linux is probably my worst Linux experience ever. I finally gave up the battle and switched to NVidia, however things are far from smooth in the NVidia world too.

So - to the subject. My advice is - get rid of the card! It'll spare you LOTS of headaches. Until you decide to do that, just a few things:

* I remember ATI switched to their proprietary BINARY format where they keep their settings! Yes, it's a binary file, you cannot edit it and making changes in xorg.conf file is not gonna do you any good. 

* Their drivers are EXTREMELY buggy and will break your x server on a regular basis with no apparent reason - simple things like changing screen resolution, switching displays, enabling tv out - may totally screw your system up and the damage would not be undone even after driver reinstallation. 

* If you like - search for my old ATI postings to find out more about my ATI nightmares

Wish you good luck with this unfair battle

---

### Post by johntrottier on 2009-08-05
LATEV -

Thanks for confirming what I was seeing. There has to be another file that holds the configuration information
Do you know the name of the file? I may not be able to edit it, but at least I could back it up, and if the world died, boot into the command line, copy the backup and restart X
It may not work, in which case I would be no worse off than before, or it may save the installation and save me the hassle of reloading the entire system the way I had to this time

Thanks

---

### Post by tgalati4 on 2009-08-05
What happens when you bring up aticonfig?

---

### Post by johntrottier on 2009-08-05
> **tgalati4 said:**
> What happens when you bring up aticonfig?
Do you mean when after I had crashed the original install and unloaded and reloaded the driver? (who know how many times - I lost track)
Because I ran aticonfig numerous times, using various initializations, setups, command line switches, until I was blue in the face. 
aticonfig would would modify the xorg.conf file, but no matter what I did, I could not get the "big desktop" to work. In most cases, I ended up having to boot in recovery mode, and "fix" the x server, which rewrote the xorg.conf file, loaded the open source drivers and put me back to a 640x480 resolution cloned screen that was useless for anything other than a post-it note holder, because you surely could not do anything on it.
It was not until I reloaded the OS and then reloaded the proprietary driver that I was able to use the Catalyst control center to enable the "Big Desktop". This happened with no fuss, no muss, it just worked. 
If you think I am running aticonfig on this new install before I know how to back up what I have, your wrong. There is no way!

---

### Post by latev on 2009-08-05
The problem is that it was awhile since I was messing around with ati drivers, but take a look at your etc folder - may be do a search for ati and see what pops up. Do you have an ATI subfolder? If you give me a list of files I might remember which was the right one

---

### Post by tgalati4 on 2009-08-07
I think you have found a bug in the behavior of aticonfig and Big Desktop settings.  The bug is such that it renders the system without a display when it messes up.

Perhaps you should file it with the Catalyst folks.

Things don't get fixed unless they are submitted to the right people.

---

### Post by arcdrag on 2009-08-07
Right now I really wish I would have done a bit more research before buying my last video card.  I think I'm just going to return my Radeon 4830 to Newegg.  Pretty much every time I boot into Ubuntu it almost seems completely random how my display is going to look.  Sometimes both of my monitors display, sometimes one displays correctly and the other is in some crazy resolution like 300x300, sometimes only one starts, etc...  Really, the only thing that is for certain is that its going to lock up within 10 minutes of starting the computer.

---

### Post by tgalati4 on 2009-08-07
That's too bad.  I recently bought a used IBM thinkpad T43P with an ATI card.  Not much choice in the older thinkpad line.

I think the ATI drivers will improve with time.  AMD seems amenable to releasing some data to help developers.  It will take some time though.

For gaming in Windows, ATI works well with ATI proprietary drivers.  Open ATI drivers in Linux work OK.  I've got compiz and lots of effects running, but I don't game in Linux so I can't really compare performance.  According to others, the ATI proprietary drivers work OK in Hardy and below.  With a new Xorg and open ATI driver architecture, I expect lots of breakage over the next few releases.

---

### Post by latev on 2009-08-07
> Right now I really wish I would have done a bit more research before buying my last video card. I think I'm just going to return my Radeon 4830 to Newegg. Pretty much every time I boot into Ubuntu it almost seems completely random how my display is going to look. Sometimes both of my monitors display, sometimes one displays correctly and the other is in some crazy resolution like 300x300, sometimes only one starts, etc... Really, the only thing that is for certain is that its going to lock up within 10 minutes of starting the computer.

That's EXACTLY what I was experiencing an year ago. It's so sad that ATI guys are well aware that they've lost the Linux battle to NVidia long time ago and they don't seem to care at all now about their Linux customers. Everyone knows that if you want to use Linux, you simply DONT buy an ATI card.
So, my advice again: Don't waste your time and go get an NVidia card as soon as possible. Save your patience and energy for it, cause trust me it won't be perfect with nvidia too. But at least you have a fair chance there. Good luck!

---

