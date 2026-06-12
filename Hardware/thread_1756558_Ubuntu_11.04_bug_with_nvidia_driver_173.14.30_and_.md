---
title: "Ubuntu 11.04: bug with nvidia driver 173.14.30 and FX 5200"
date: 2011-05-12
forum: Hardware
---

### Post by rvboutin on 2011-05-12
Hi,
I have checked many forums and website about it, and it seems that there is a lot of people out there with a bug in the nvidia drivers 173.14.30 that are the one for the GeForce FX5200 that I have running on one of my PC.
I can boot and work fine in basic graphic mode (no 3D features), and whatever I do to install the nvidia driver, then I got stuck on boot at "checking battery..." and it does not go any further. I have then to boot in recovery mode and choose low graphic.
If I remove all nvidia drivers, then I can boot in but I have no 3D working...
Any news anyone on that front?
Cheers,
Rv

---

### Post by Riskexas on 2011-05-12
I have similar problem:
Bad resolution makes black screen (everything else works fine). I´m using GeForce FX5200.
And by the way it would be GREAT that it will be fixed.
[U][B]
[COLOR=Red]NOTE:[/COLOR][/B][/U]**[COLOR=Red][COLOR=Black]installing older drivers(was in 10.10) makes it different!!! [/COLOR][/COLOR]**[COLOR=Red][COLOR=Black]*Then it works....*[/COLOR][/COLOR]

---

### Post by boriolis on 2011-05-20
It worked right away on mine FX5200 and ubuntu 11.04. Only thing that is bothering me is AGP Fast write Disabled. One thing to note is that I use the driver from NVIDIA website. I don't use the repository version.


cat /proc/driver/nvidia/agp/status 

gives

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled



PS:


OK I used the same old fix to enable Fast Write : 

created a file /etc/modprobe.d/nvidia.conf and entered following into. Restarting X didn't enable it though. I had to reboot it to get it working.

#########

alias char-major-195 nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1


###########


Now 

 cat /proc/driver/nvidia/agp/status

gives

Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled



......

---

### Post by mannyyamzon on 2011-06-28
Hi, I have the same problem with GeForce FX5200, uBuntu 11.04. I have just installed uBuntu and after selecting to boot to uBuntu it did not even show the mode options. Should I re-install uBuntu?

---

### Post by rreyes3713 on 2011-06-30
I'm bumping up this post. 
 
Did any of you guys have any trouble installing the driver on 10.04 (well if you did use 10.04 Ubuntu, I know this thread is about11.04).
 
I have the same Nvidia card and download the same driver. I have yet to install it (well rather run it) on Ubuntu 10.04.
 
As of now, resolution seems fine although some video clips seems a bit pix-sy (mosiac) so I'm not sure if I'm running this Nvidia card at optimum performance with the given Nvidia default driver on the 10.04 system.

---

### Post by rvboutin on 2011-06-30
Hi guys,
I did not try it on 10.04, although I had it working before on a Wubi install of Ubuntu 10.10.
Trouble came when I install Ubuntu 11.04. Personally, I do not know why Canonical have become so obsess about releasing a new version every 6 months... this is silly, that does not even leave time for people to fix problems with one release than ](*,) another release is there before you know it.
Obviously, part of the problem being that it is a rather old graphic card. :(
Cheers,
Rv

PS: by the way, I have now the driver installed in 11.04, and working, although it seems that not all 3D features are working... I have kind of given up on this to be honest.

---

### Post by rmbzz on 2011-07-03
I am also having trouble with the nvidia drivers and an fx5200 graphics card and mythbuntu. 

The drivers are installed, but there is nothing on the display. The restricted drivers manager says that the nvidia driver is not in use. 

Where do I look to find out what the problem is?

---

### Post by MG&amp;TL on 2011-07-03
Sigh...me too, GeForce FX 5200, try the nouveau driver, it should be labelled 'experimental 3d' in the hardware drivers section. While not as good as the proprietary one, it does work for most 3d acceleration tasks. 

Major bug, though, it does appear to kill Unity, and we haven't found a way to fix this yet, I have an active thread here:

[http://ubuntuforums.org/showthread.php?t=1795383](http://ubuntuforums.org/showthread.php?t=1795383)

Compiz is dodgy, too, although that might be because of the dead unity problem.

I'm hoping to get a new pc soon, so hopefully it shouldn't be a problem for me. I guess eventually these old cards will die out. :(

---

### Post by MG&amp;TL on 2011-07-03
[QUOTE=rmbzz;11007801

Where do I look to find out what the problem is?[/QUOTE]

You have tried rebooting? And deactivating/activating? Other than that, I don't have a clue, try googling it, it's quite a common problem, I think. :)

---

### Post by Lystrade on 2011-08-06
I have just installed 11.04 and I have the fx 5200 card.  When it boots I can see my background picture, but everything else flashes and can't really be seen.  If I connect to the onboard video card, then ubuntu works, but without 3d support.  How do I make it work with the nvidia card?

---

### Post by HipHopBlond on 2011-08-06
Come oon guys.. nVidia GEForce 5200 FX... that's a prahistorical card... I'm building a new PC soon, time to move on with time :)

---

### Post by Lystrade on 2011-08-06
That certainly isn't a helpful post.  Have you ever heard the phrase, "if it ain't broke don't fix it?"  This card worked just fine with XP.  I just need a bit of help setting it up on Ubuntu.

---

### Post by Tripmonkey_uk on 2012-02-08
Had this problem myself today but it looks like I got it sorted.

It turns out that _only_ the **173.14.xx legacy drivers** from the Nvidia website fully support the card.

[This is the page I got them from!]("http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver.html")

**WARNING:** You will need to change the permissions on the downloaded file and make sure that it can be executed as a program before doing anything with it.
You will also need to install it through the command line **[B]_without your xserver running_**[/B] otherwise it wont work.

Hope that helps you guys out a little. Good luck! :)

---

