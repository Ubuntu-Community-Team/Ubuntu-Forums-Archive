---
title: "Why does my screen look like this?? Its really making me ANGRY!"
date: 2008-11-28
forum: General Help
---

### Post by kevdog on 2008-11-28
Ive Included a screencap of what my screen looks like.

Im using the 82830 Intel Chipset on Ubuntu:

Here is what lshw reports:
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82830 CGC [Chipset Graphics Controller]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82830 CGC [Chipset Graphics Controller]
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=11

Why is this unclaimed -- I thought these kernel modules were included by default in the kernel?

---

### Post by lswb on 2008-11-29
Hi kevdog,

I don't see your screenshot. I have intel 855 graphics in my system a slightly later version than the 830, and my lshw output is pretty much the same as you have posted, with the displays "unclaimed" and just before that, it also says system:0 and system:1 unclaimed.

Everything works OK, though. (Well, if you don't count the occasional unrecoverable black screen or system crash when playing videos)

---

### Post by kevdog on 2008-11-29
Screen shot added!!!

---

### Post by lswb on 2008-11-29
Maybe a font selection problem? Is it only happening with firefox?

---

### Post by alwayshere on 2008-11-29
maybe ya xconf is stuffed up if its happening all around .
you could fix it bt starting in recovery mode and choose fix xconfig .
then things should be all good you will have to reset appearance effects again if you want them on .

---

### Post by kevdog on 2008-11-29
Yes, but if I reboot, everything is good for awhile and then everything just slowly corrupts.

What is the deal with the intel 830 chipset and Ubuntu?

---

### Post by alwayshere on 2008-11-29
intel 830 chipset i think is a bit forgotten and in the almost just sort of supported i do know compiz will mess with it ,the word on the street seems to say ya might be better off going back to an older version of ubuntu 7.04 maybe ?. or find a intel 830 chipset friendly linux  distro.to my knolage that seems to be your options ,but i hope im wrong!

---

### Post by kevdog on 2008-11-29
I disabled compiz, or the screen was black upon boot.  However the font corruption system is system wide.  You are right that with Feisty on this machine I had no problem.  I did a fresh install to Intrepid, and the appearance is terrible.  Its obviously a kernel issue, but somethings I can never understand when it was working great with a previous kernel.

Is there a guide that exists how to edit xorg.conf and activate this file, since it seems Ubuntu no longer uses this file -- its totally blank!

---

### Post by lswb on 2008-11-29
Maybe a long shot, but I remember that when I first installed hardy, I was playing with the video drivers and resolutions. The default X driver for intel graphics is "intel" but there is an older driver named "i810" that can also be used. Maybe you can try that and see if you have better results. There is a man page on both.

I remember that my system would run with the i810 driver OK but I don't recall if I tried it with compiz. I have been using the intel driver except for that brief period of experimentation.

Unfortunately I don't remember the exact steps it took to change the drivers. I haven't seen much info about editing the new minimalist style xorg.conf file. There is a utility program named "displayconfig-gtk" that may help you there. In hardy it can be added to the main menu under Applications/Others and shows up with the name "Screens and Graphics" I don't know about intrepid but you should be able to start it from the cli with "sudo displayconfig-gtk"

---

### Post by kevdog on 2008-11-29
Great suggestion, however displayconfig-gtk was last offered with hardy, and not intrepid.  How the heck to do edit the xorg.conf file??  It is a minimalist system -- there is nothing in the file.  How do I change video drivers?

---

### Post by lswb on 2008-11-29
> **kevdog said:**
> ...  How the heck to edit the xorg.conf file??  It is a minimalist system -- there is nothing in the file.  How do I change video drivers?

I've wondered about that also. The documentation, if there is any, is difficult to find. The man page for i810 says to put it in xorg.conf like this:

Section "Device"
  Identifier "devname"
  Driver "i810"
  ...
EndSection

I don't know if this is out of date or not. If you read through a /var/log/xorg.o.log file, though, it appears that the xorg.conf file is still parsed when X starts, so it might work to override the automatic configuration. Of course, it may not solve your problem even if it does work to load the older driver.

The only thing in the intrepid xorg.conf device section on my system is

Section "Device"
        Identifier      "Configured Video Device"
EndSection

so I guess you could just add ' Driver "i810" ' after the Identifier line if you wanted to try it. What could possibly go wrong? :)

You know, I hadn't looked at the intrepid xorg.conf til now. (I have hardy and intrepid both on my laptop, can't make up my mind) I thought the hardy xorg.conf was amazingly small, but in comparison it now seems positively verbose!

---

### Post by kevdog on 2008-11-29
Here is what I did, and it slightly improves the situation.

Please notice that I have turned off and disabled compiz completely since its incompatible with the Intel 830 Chipset.

sudo dpkg-reconfigure xserver-xorg

The generated a skeleton xorg.conf file.  

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I added the following to the Screen Section:

	DefaultDepth	16


Rebooted. 

Its better, but not ideal.  I hope this might help someone. Why this chipset was phased out and worked a lot better even with Compiz in the Feisty kernel is beyond me.  I'm sure there was a reason, however it baffles me how hardware support gets more skant with newer releases.  Things are supposed to move forward, not backward.

I did try the i810 driver, however the xserver failed to load.  I'm open to other suggestions.

---

### Post by kevdog on 2008-11-29
I'll retry the i810 solution you suggested.  I have to say the solution I just posted really sucks!!

---

### Post by kevdog on 2008-11-29
I totally open to new suggestions.  I tried the i810 driver as you suggested with your config, but the xserver would not boot.

---

### Post by lswb on 2008-11-29
Sorry you are still having trouble, but at lease we now know that the xorg.conf file can be edited if necessary. I wonder if manually specifying a driver also requires manually adding the other options for that driver also? Maybe if you have a copy of your Feisty xorg.conf you could try the whole device section.

I agree the regressions in hardware support are a pain. I have a few devices that worked with dapper but not with hardy. OTOH the reverse is also true.

I don't know much about how fonts work in X, I wonder if that could be related to your display problem rather than the video driver.

---

### Post by kevdog on 2008-11-30
Seems like all the old intel chipsets are covered by one generic driver: [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

This particular piece of hardware -- everywhere I've looked -- in a lot of other forums, is horribly supported since the specific i815 driver was removed and replaced by this generic driver.  Unfortunately I don't see a way around it other than downgrading.  With Hardy there was a random lockup problem -- never tried the Gutsy distro -- Feisty was working great.

Why did I upgrade?

---

### Post by alwayshere on 2008-11-30
maybe ya find a few tricks here mix it up a bit ????

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#xorg.conf](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#xorg.conf)

---

### Post by pedor on 2009-04-19
I am sitting here and have that same issue with ubuntu  9.04

It is bad because it have works perfectly with earlier versions of Ubuntu.  it is little to usually of case like this in Ubuntu :(

---

### Post by kevdog on 2009-04-19
Its not Ubuntu specifically -- its the linux kernel.  They dropped i810 support along the way.  The only solution would be to either use older Ubuntu versions, or downgrade the kernel -- compile it from scratch.  Neither is a great solution, but the only one I can suggest.

---

### Post by jerrylamos on 2009-04-26
> **pedor said:**
> I am sitting here and have that same issue with ubuntu  9.04

It is bad because it have works perfectly with earlier versions of Ubuntu.  it is little to usually of case like this in Ubuntu :(

I'm another one on jaunty with IBM Thinkpad R31 which has i830 graphics.  

It runs fine on Ubuntu Intrepid but the fonts gradually muck up on jaunty.

I'm currently dual booted with jaunty 2.6.30-rc2 which is slightly better, and intrepid when I get fed up with jaunty.

screen performance with 2.6.30-rc2 is near intrepid - jaunty with 2.6.28-11 is distinctly(!) slower.  hardy is faster yet however ubuntu has acquired a lot of polish since then and some of the benchmarks don't run on hardy.

launchpad bug #1 from Mark Shuttleworth is that Microsoft is dominant in the marketplace.  The more hardware that linux abandons is good for Microsoft since this system runs XP fine.  

Another VGA hardware set that is being abandoned is ATI.

Jerry

---

### Post by kevdog on 2009-04-27
A bummer that support for older hardware is being phased out for sure!  Everytime I mention this in the forums however I get my head ripped off and usually get responses like:
"Get a new computer"
"How long do you want your old piece of crap hardware to be supported!"
"Computer's are cheap these days, no reason you can supply not to upgrade!"

---

