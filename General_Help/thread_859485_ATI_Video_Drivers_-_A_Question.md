---
title: "ATI Video Drivers - A Question"
date: 2008-07-14
forum: General Help
---

### Post by solwic on 2008-07-14
So I'm running Ubuntu HH with an ATI Radeon X1300 PCI-E 256MB video card, and I'm trying to enable desktop effects.  There's lots of lag, which I understand is due to Compiz not playing nicely with the ATI Drivers, or the other way around.  I also understand that the conflict has descended, as so many such conflicts do in the Linux world, to the level of a playground fight between the two companies/groups, which goes something like:

COMPIZ:  It's ATI's fault!  They make crap drivers for Linux!
ATI:  Nuh uh!  It's compiz's fault!  Their code is crap!
COMPIZ:  Nuh uh!  You started it!
ATI:  Nuh uh!
COMPIZ:  Yes huh!

....

And so on.

My question is this:  I'm using the restricted driver that was offered to me when I installed Ubuntu.  I know that in distros like openSUSE, you can choose to add the ATI repository to the list of repositories checked during the update process, which brings us to my questions:

1.  Is this "ATI Repository" from ATI, or was it an openSUSE thing?
2.  Is the official ATI driver different from the restricted driver I am currently using?
3.  Would installing the official ATI driver remedy the problems I'm having with compiz (when desktop effects are enabled, video playback is choppy, screensavers and 3d programs like Google Earth and all 3d games flicker, CPU usage spikes when accessing 3d video, etc.)?
4.  Are there any good tutorials for installing the official ATI driver?
5.  I've heard of a program called Envy...does it work with ATI drivers?

I know that's a lot of questions, most (or all) of which have been answered before, but a few searches didn't give me any satisfactory results, so I thought I'd try an open request for help.

Any help would be great!  Thanks!

---

### Post by markbuntu on 2008-07-14
1. ATI does not maintain a repository of releases for the various distros, distros maintain those repositories. ATI does maintain a repository of their drivers. The latest is 8.6.
2. The restricted driver you are using, if it came from the Ubuntu repository is most likely 8.47.3 or something like that and is an official ati driver but not the latest one.
3. The latest driver 8.6 will fix your gooogle earth problem and 3D issues but not the compiz issues but we expect that to be fixed by the fall, ati is promising big things.

4. If you want to install the latest ATI driver you can download it from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The best directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use Method 2 and follow the directions very carefully and completely especially if you are using 64 bit.

After installing the driver you can use the tweaks here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

5. Envy will not install the latest 8.6 driver, it is still installing the 8.47.3 driver. Use the directions above. Personally, I have had nothing but problems using envy. It seems to work better for nvidia users.

---

### Post by solwic on 2008-07-14
> **markbuntu said:**
> 1. ATI does not maintain a repository of releases for the various distros, distros maintain those repositories. ATI does maintain a repository of their drivers. The latest is 8.6.
2. The restricted driver you are using, if it came from the Ubuntu repository is most likely 8.47.3 or something like that and is an official ati driver but not the latest one.
3. The latest driver 8.6 will fix your gooogle earth problem and 3D issues but not the compiz issues but we expect that to be fixed by the fall, ati is promising big things.

4. If you want to install the latest ATI driver you can download it from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The best directions for installing it are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use Method 2 and follow the directions very carefully and completely especially if you are using 64 bit.

After installing the driver you can use the tweaks here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

5. Envy will not install the latest 8.6 driver, it is still installing the 8.47.3 driver. Use the directions above. Personally, I have had nothing but problems using envy. It seems to work better for nvidia users.

So my best bet is probably to either wait until fall and get the better ATI drivers or just break down and go buy an nVidia card, right?  I don't care so much about the movies and google earth as I do compiz.  I hate having all this capability with my desktop and not being able to use it without crippling the rest of the video capabilities.  :(

Thanks for the help!

---

### Post by solwic on 2008-07-14
Actually I have another question:

I only have the issues with video playback and 3d graphics if I enable desktop effects.  If I turn those off, I have no video issues at all.  Since the new ATI drivers fix the 3d issues, does that mean I can turn on compiz and have smooth video playback?  

I have no issues with compiz itself; I enable the desktop effects and they all work great, they just break video playback and 3d.  If the new driver fixes video playback and 3d, I shouldn't have any problems, right?

---

### Post by Execute_Method on 2008-07-14
I have an x1650 agp 256mb (rv535 chip). This was a "problem" card from start, as it is "unsupported" by ati because of the AGP interface... No matter what I did I could not get the proprietary driver to work. It always ended in black after installing. I tried for about a week straight every day....I decided to use the radeonhd driver (no 3d...yet), which is open source and it worked really well for 2d. Then came along May of this year -> major advancements in the open source driver "ATI (radeon)". Because of a major release of 3d documentation form AMD/ATI to the open source community, the progress is in leaps and bounds.

I followed this article:
[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

I am able to run compiz uber-smooth, it never breaks 3d, and I get over 2300fps in glxgears, which is on par if not better than people are getting w/ the _PCI-E_ version of this card using fglrx (proprietary driver)

Your card is of the same family (RV500 series) and will most likely work better with the newest open source driver!!

I hope this helps you, because I struggled with this issue (ati drivers) for months. I even considered getting an nvidia card, but now that I have 3d using open source drivers I couldn't be happier.

There are however some features that are not fully developed yet.

BTW are you using "LIBGL_ALWAYS_INDIRECT" when starting Compiz?

This is the way I start compiz, so I don't have any problems:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & exit
```

**** Support Open Source wherever possible, it's the only way to undo the damage that Microslop has doen to this industry****

---

### Post by Execute_Method on 2008-07-14
> **jrock612 said:**
> 
video playback and 3d graphics if I enable desktop effects.

This hasn't been a problem for me with the new open driver. I can run games, and videos w/o a problem.

---

### Post by solwic on 2008-07-14
> **Execute_Method said:**
> I have an x1650 agp 256mb (rv535 chip). This was a "problem" card from start, as it is "unsupported" by ati because of the AGP interface... No matter what I did I could not get the proprietary driver to work. It always ended in black after installing. I tried for about a week straight every day....I decided to use the radeonhd driver (no 3d...yet), which is open source and it worked really well for 2d. Then came along May of this year -> major advancements in the open source driver "ATI (radeon)". Because of a major release of 3d documentation form AMD/ATI to the open source community, the progress is in leaps and bounds.

I followed this article:
[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

I am able to run compiz uber-smooth, it never breaks 3d, and I get over 2300fps in glxgears, which is on par if not better than people are getting w/ the _PCI-E_ version of this card using fglrx (proprietary driver)

Your card is of the same family (RV500 series) and will most likely work better with the newest open source driver!!

I hope this helps you, because I struggled with this issue (ati drivers) for months. I even considered getting an nvidia card, but now that I have 3d using open source drivers I couldn't be happier.

There are however some features that are not fully developed yet.

BTW are you using "LIBGL_ALWAYS_INDIRECT" when starting Compiz?

This is the way I start compiz, so I don't have any problems:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & exit
```



I thought Compiz Started automatically with everything else?  When I say start compiz I mean I'm going to the Visual Settings tab and switching the option from "none" to "normal".  

Where would I put that code to start compiz?  In terminal?  If so, can I make it run automatically at boot?  

Thanks!

---

### Post by Execute_Method on 2008-07-14
> **jrock612 said:**
> I thought Compiz Started automatically with everything else?  When I say start compiz I mean I'm going to the Visual Settings tab and switching the option from "none" to "normal".  

Where would I put that code to start compiz?  In terminal?  If so, can I make it run automatically at boot?  

Thanks!

This line is necessary for compiz to get along with most ati drivers

Yes, in terminal, and yes you can make it start with this line passed as well.

Try this in terminal first and see if it helps:

kill compiz:

```
pkill compiz
```

restart compiz w/ indirect:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp & exit
```

---

### Post by Execute_Method on 2008-07-14
Here is the startup script I use: I am also using emerald WM, so I have the emerald line in there to ensure it starts after compiz.


```
gedit start-compiz
```
add this
```
#!/bin/bash
sleep 5
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
sleep 5
emerald --replace

```
save it

it has to be executable, so:

```
chmod +x start-compiz
```

add it to your startup:

system -> preferences -> session preferences

add it to the startup programs

---

