---
title: "[SOLVED] Issue with 30&amp;quot; monitor"
date: 2008-12-03
forum: Hardware
---

### Post by test006 on 2008-12-03
Hi,
I am using Kubuntu 8.10 to boot using the Live CD. Everything works  fine except that i do not get any graphical stuff...i.e. no KDE. I am using Nivida GeForce 8500 GT video card and Dell 3007WFPHC (30") monitor. My monitor can support maximum resolution of 2560x1600.

I can access command line no problem but i cannot get KDE to work. Can someone let me know how should i go about trouble shooting this?
No command line when i type startx it says that it is already running.

Has anyone know how to overcome this problem? Please help me out...
Do i need to download and install video card drivers in order for this to work...

 
Thanks

---

### Post by stinger30au on 2008-12-03
this is where ubuntu needs a startup like mandriva 2009 has where you can select 3d effects like compiz, or metaciy or nill

our of interest , i would try simple stuff first, like try the monitor on another pc and make sure it is ok

also how is the monitor connected, i assume it is via dvi???

what video card do you have??

---

### Post by test006 on 2008-12-03
> **stinger30au said:**
> this is where ubuntu needs a startup like mandriva 2009 has where you can select 3d effects like compiz, or metaciy or nill

our of interest , i would try simple stuff first, like try the monitor on another pc and make sure it is ok

also how is the monitor connected, i assume it is via dvi???

what video card do you have??

Hi,
The monitor is fine...I aready have windows running on the same box with the same monitor...So monitor is not a problem.
My video card is: Nivida GeForce 8500 GT
Monitor is connected to the video card via dvi connection.

Hope this helps...Any hints on how i can fix this problem?

Thanks in advance...

---

### Post by test006 on 2008-12-04
Hi,
Can anyone let me know how i can fix this problem....

Thanks

---

### Post by andreasis on 2008-12-04
I have a 26" Samsung monitor, and, like you, I tried Kubuntu, and Xubuntu too, before I settled with Ubuntu.  It may not be an answer you want or are willing to accept, but I would suggest to give Ubuntu a try.  For some reason, Ubuntu was able to not only get the graphical desktop to show right after the install, but it was the correct resolution, too.

Time to think of it, actually, it might have well been a driver problem.

If you do live session off of the install cd, do you get a graphical interface?  If not, do you get one with Ubuntu?

If yes, then download the the graphics driver from the nvidia website (the most recent stable version is 177.82 I think) and install it (sudo sh NVIDIA-Linux-177......pkg2.run)

Tell me if this helps.

---

### Post by test006 on 2008-12-05
> **andreasis said:**
> I have a 26" Samsung monitor, and, like you, I tried Kubuntu, and Xubuntu too, before I settled with Ubuntu.  It may not be an answer you want or are willing to accept, but I would suggest to give Ubuntu a try.  For some reason, Ubuntu was able to not only get the graphical desktop to show right after the install, but it was the correct resolution, too.

Time to think of it, actually, it might have well been a driver problem.

If you do live session off of the install cd, do you get a graphical interface?  If not, do you get one with Ubuntu?

If yes, then download the the graphics driver from the nvidia website (the most recent stable version is 177.82 I think) and install it (sudo sh NVIDIA-Linux-177......pkg2.run)

Tell me if this helps.
Hi,
I have tried ubuntu 8.10 live CD and no i do not get graphical interface at all. Same thing for Kubuntu as well. 
I have also tried latest version of Fedora and same thing no graphical interface. I can get to CLI and wheni type startx it says that xserver is already running....

Instead of graphical interface a get a blank screen....Please help....

Thanks in advance...

---

### Post by razy60 on 2008-12-05
IF you can download a copy of Ultimate edition 2.0(its a jazzed up variant of 8.10) it needs a DVD to run as its 1.6gig in size, run the live disc to see if it works, the only reason i suggest this is it already has a huge amount of options pre-installed so it may help.
Another alternative may be PCLinuxOS its a good OS and again has a lot of video drivers, as it was built to be easy alternative to those that just want a Linux os thats very similar to windoze(it uses KDE).

Raz

---

### Post by EV500B on 2008-12-05
It can be an resolution incompatibility between your monitor and your graphic card.
Try to hit (Ctrl +) or (Ctrl - )

You can also try (If you can get into the console or any terminal) to type
*xrandr* -s 800×600
(800x600 is the resolution, you know it works with both. Change it to adapt to your machine)

**xrandr --auto**
or
**xrandr** [B]--preferred
(Not sure about this one)


[/B]

---

### Post by stefangr1 on 2008-12-05
> **andreasis said:**
> I have a 26" Samsung monitor, and, like you, I tried Kubuntu, and Xubuntu too, before I settled with Ubuntu.  It may not be an answer you want or are willing to accept, but I would suggest to give Ubuntu a try.  For some reason, Ubuntu was able to not only get the graphical desktop to show right after the install, but it was the correct resolution, too.

Time to think of it, actually, it might have well been a driver problem.

If you do live session off of the install cd, do you get a graphical interface?  If not, do you get one with Ubuntu?

If yes, then download the the graphics driver from the nvidia website (the most recent stable version is 177.82 I think) and install it (sudo sh NVIDIA-Linux-177......pkg2.run)

Tell me if this helps.

I would recommend you, whether the gui of the live-cd works or not, to install the NVIDIA drivers from the terminal.

---

### Post by EV500B on 2008-12-05
> **EV500B said:**
> It can be an resolution incompatibility between your monitor and your graphic card.
Try to hit (Ctrl +) or (Ctrl - )

You can also try (If you can get into the console or any terminal) to type
*xrandr* -s 800×600
(800x600 is the resolution, you know it works with both. Change it to adapt to your machine)

**xrandr --auto**
or
**xrandr** [B]--preferred
(Not sure about this one)


[/B]
If the **xrandr -s something** works.
You can make the change permanent using the instructions in this link 
:arrow: [http://fluxbox-wiki.org/index.php?title=Howto_change_resolution](http://fluxbox-wiki.org/index.php?title=Howto_change_resolution)

---

### Post by andreasis on 2008-12-05
> Are you saying that you installed ubuntu from the desktop/live cd without the graphical interface?

I'm surprised to hear that because I wasn't aware that that was possible.. I thought that that's what the alternate cd was for.. this question is open for anyone to answer / I'd appreciate it.

Moving further, I would still go ahead and install the nvidia driver, as you've said that you can get to the CLI.  If you need help with that it's not a problem... your problem's more common than you may think (ever tried installing Debian?)

There are some good suggestions on this thread.. try them out and post results.

If you got it to work, post how so you'll be helping out someone else in the same situation as yourself.

---

### Post by test006 on 2008-12-05
O.K i finally got it working.
So now using the Live CD i.e.without installing i can get graphical interface on my 30" monitor.
I tried xrandr and it did not work for me i.e. it keeps telling me it cannot open display.
So this is what i did:
1. During the CD bootup process use the F4 key and select safe graphics mode.
2. This gives me the graphical interface off course this is not optimum for my screen i.e. its 800x600. Now i tried crtl + and crtl - but this does not work.
3. I used firefox to download the nvidia drivers from their website.
4. In order to install the nvidia driver you need to stop the xserver so i did the following: /etc/init.d/gdm stop (do kdm if you are using Kubuntu)
5. Than i used CLI mode to install the nvidia drivers i.e. "sh nvidia...."
6. After the driver is installed i did /etc/init.d/gdm start
7. Now i get the graphical interface which is 2560x1600 which is the best resolution for my screen....

So i hope this information will be helpful to other people. I would also like to thank everyone for their help as well....
Thanks and problem solved....

---

