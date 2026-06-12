---
title: "SiS / Asus video difficulties"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by floppy on 2005-08-16
There are apparently problems getting the SiS driver from [www.winischhofer.at](www.winischhofer.at) to work properly with Ubuntu. I don't know enough to figure out how this should all work.

Ubuntu's install routine uses the "vesa" driver in xorg.conf. This driver is exhibiting poor performance on my system.

Has anyone sucessfully installed the SiS driver? Can you explain in simple terms how to proceed? Help with the proper text for the configuration would go a long way.

---

### Post by new2hoary on 2005-08-17
I have just installed Hoary on a asus/sis pc.

As you said the install configured the vesa driver. What I did was to reconfigure xorg 
after the install completed.

Make sure you have all the details about you video hardware ie. video ram in kB, resolutions, refresh rates and the like.

Then as root run;

dpkg-reconfigure xserver-xorg

answer the questions and select the sis driver - worked a treat for me.

---

### Post by floppy on 2005-08-17
[QUOTE=new2hoary]I have just installed Hoary on a asus/sis pc.

As you said the install configured the vesa driver. What I did was to reconfigure xorg 
after the install completed.

Make sure you have all the details about you video hardware ie. video ram in kB, resolutions, refresh rates and the like.

Then as root run;

dpkg-reconfigure xserver-xorg

answer the questions and select the sis driver - worked a treat for me.[/QUOTE]
 Sounds great, but... where did you get the details for the SiS chip? I've been unable to find that kind of info. Probably stupidity on my part, sorry!

I'm curious, too. Which Asus board are you using?

It's amazing that's it's working for you, considering the problems I've noticed people (like me) are having. Have you noticed any speed difference between the vesa driver and the sis driver?

Thanks for the guidance!

---

### Post by new2hoary on 2005-08-17
Sorry for the vague response.

My mother board is a ASUS A7S8X-MX with  intergrated sis graphic (sorry can't remember the chipset - I just selected SIS driver when reconfiguring xorg).

The graphics memory is 128mb shared so when asked about the video memory I just multiplied 128 by 1024 to get the amount in kilobyte which is what xorg requires.

Hrizontal/vertical refresh times is to do with the monitor and I got them from the monitors manual.
Resolution is dependant on both video card and monitor. My monitor supports resolution to a max of 1280x1024 so that is what I entered as well as some lesser resolutions. I assumed that the card would handle 24bit colour at this resolution.

The rest of the questions are about the mouse and keyboard and pretty straight forward.

When I originally installed Hoary I noticed the graphics were wrong. The colour wasn't great - slightliy washed out looking. I also noticed that the resolution could only be set to 1280x788. Finally If I logged out the their was a slight 'painting in' effect from top to bottom as the login screen was displayed.

Once I reconfigured with sis as the driver I can get 1280x1024 the colour is great, and there is no 'painting' effect so I'd say the speed has improved greatly also.


EDIT: I just downloaded the MB manual and the graphics chipset is SIS741/SIS741 GX

---

### Post by floppy on 2005-08-17
Thanks so much!! A Great Help!

For others that may reference this, I found the video memory size documented in the motherboard manual. For my Asus P4S800-MX, it can be set in the bios to 32 or 64 megabytes.

---

### Post by new2hoary on 2005-08-17
No problem - I hope you get it sorted.

---

### Post by az on 2005-08-17
[QUOTE=floppy]There are apparently problems getting the SiS driver from [www.winischhofer.at](www.winischhofer.at) to work properly with Ubuntu. I don't know enough to figure out how this should all work.

Ubuntu's install routine uses the "vesa" driver in xorg.conf. This driver is exhibiting poor performance on my system.

Has anyone sucessfully installed the SiS driver? Can you explain in simple terms how to proceed? Help with the proper text for the configuration would go a long way.[/QUOTE]


Make sure you are using the sis driver and you have a compatible chipset:

Look at this:
[http://www.ubuntuforums.org/showpost.php?p=258361&postcount=33](http://www.ubuntuforums.org/showpost.php?p=258361&postcount=33)
[http://www.ubuntuforums.org/showpost.php?p=253620&postcount=15](http://www.ubuntuforums.org/showpost.php?p=253620&postcount=15)
[http://www.ubuntuforums.org/showpost.php?p=253620](http://www.ubuntuforums.org/showpost.php?p=253620)


Sis acceleration is not that great...


Also, when you ru dpkg-reconfigure xserver-xorg, it is best to shut down the X server so that autodetection does not screw up.  You can do this by running 
init 1
in a terminal and that will drop you down to a console.  Run 
init 2
to restart X

---

### Post by floppy on 2005-08-17
[QUOTE=azz] when you ru dpkg-reconfigure xserver-xorg, it is best to shut down the X server so that autodetection does not screw up.  You can do this by running 
init 1
in a terminal and that will drop you down to a console.  Run 
init 2
to restart X[/QUOTE]

Do you mean I do the "init 1", then the reconfigure, then the "init 2"?
Sorry for the stupid question.

---

### Post by new2hoary on 2005-08-17
If when reconfiguring xorg you get it to auto detect then you should shut x down then reconfigure and finally start up x again.

I have found the auto detection not to be that great. especially with regards to video memory.

If you reconfigure xorg and choose manual entry of settings then you don't need to stop x first.  You will need to restart x for it to pick up the new configuration though.

---

### Post by az on 2005-08-17
[QUOTE=new2hoary]If you reconfigure xorg and choose manual entry of settings [/QUOTE]


"Sounds great, but... where did you get the details for the SiS chip? I've been unable to find that kind of info. Probably stupidity on my part, sorry!"

I think most people would have to rely on autodetection.

You can type 

sudo init 1

from and command line.  You should be brought to a console just like when you shut down (runlevel2 services will be stopped, and that includes X/(GDM).  You should end up at a command line prompt.  You are root.
Then run
dpkg-reconfigure xserver-xorg
and answer everything.  When you are done, run

init 2
and that will start the runlevel 2 services again and you will be back in X.

---

### Post by new2hoary on 2005-08-17
I've done it this way since I started using Debian, now that I've switched to ubuntu I figured I'd give the auto a try.

Using the LiveCD to test my hardware when it asked me what video I had I told it SIS and added the 1280x1024 to the resolution. It did the rest itself and X wouldn't start.

When I did the install for real I don't recall it asking me anything about my hardware and sure enough I ended up with VESA and the performance hit.

I did a dpkg-reconfigue xserver-xorg and answered the questions I knew, but let it detect the memory of the card. I ended up with better colour but still not the resolution.

I reconfigured again and told it my memory was 131072 (my video memory is 128mb (128x1024=131072))

The good thing about dpkg-reconfigure is it mirrors the content of you existing conf into the answer boxes - so any question that I don't know I just accept whats there (it must have been put there by the original auto detection) by pressing enter.

I'm not saying its the right way - but my three years of Debian - it never let me down yet.

---

### Post by floppy on 2005-08-18
new2hoary, your methods work. As you noted, the SiS video on Asus motherboards is not detected by Ubuntu's installation. Following your procedures, I got my chips working properly.

In case anyone else stumbles across this, I'll note that on some Asus boards the amount of shared RAM allocated to video can be set in the board's BIOS. Whatever is set there is the value to use (multiplied by 1024) in the configuration settings.

Thanks again for the help!

---

### Post by new2hoary on 2005-08-18
Glad to offer help - and pleased it worked for you.

---

### Post by Paul Bramscher on 2005-08-26
[QUOTE=new2hoary]Glad to offer help - and pleased it worked for you.[/QUOTE]

I tried your steps on my ASRock P4S61 motherboard (SiS Real256E video chipset) and the performance difference between the default VESA and the new settings is simply no comparison.  HUGE improvement!

A couple things you should add.  I'd recommend that anyone screwing around with this first back up his /etc/X11/xorg.conf.  Though I later discovered that this appears to automatically be backed up?  Are there any other files that someone who's worried about seriously messing up his video ought to back up first?

Secondly, when it asked for the amount of video RAM, I left it blank.  I can adjust between onboard 32 MB or 64 MB, and forgot what I currently had it set at.  Looks like the detect tool didn't have any problem with that.  I went with default values for scan rate, and when I restarted X it was like 100 MHz with a slight flicker on my Samsung Syncmaster.  I moved it down to 85 MHz.  Excellent performance!

And here I was thinking about spending $50-100 for a lower-end video card with better compatibility to avoid this sort of thing.  You saved me some cash.

---

### Post by FloSynergy on 2006-04-05
ok,

i have similar issues. 
i run a kubuntu linux breezy badger distro on an asus a2 laptop.
the machine has 345mb ram,
with an additional 1gb swap memory partition
an intel celeron 2.4ghz processor
and an audigy zs 2 pcmcia sound card.
on-board graphics card: vga compatible Silicone Integrated Systems 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
i'm not sure what the video ram is...i remember something like 32 or 24mb, but i'm not sure how to check this out.

i'm looking to install a driver for the sis card that will allow dri for 3d graphics acceleration.
i have downloaded a driver from winischofer's site which has apparently been fixed to allow dri. 

opengl is running: the  mesa glx indirect version 1.2 1.5 Mesa 6.2.1)

it seems that the info on this thread is relevant.
so please correct me if i get it wrong:
copy the new driver into the right location, eg:
usr/X11R6/lib/modules/drivers/sis_dri.so
rename existing driver (sis_drv.o) so the system doesn't pick it up
add

change setting: "MaxXFBMem" "12288"

in the xorg driver section. i'm not sure where to find this section, though. any default locations?

drop down into console level with init 1
sudo dpkg-reconfigure xserver-xorg
and answer everything.
init 2

and then it should be running?

lemme know if i misunderstood anything.

i really don't want to break something i might not be able to fix...

thanks,

be well,

flo

---

