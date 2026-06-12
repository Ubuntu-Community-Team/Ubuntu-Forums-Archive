---
title: "Nvidia Drivers finally installed with no problems!"
date: 2008-09-15
forum: General Help
---

### Post by niko32 on 2008-09-15
Hello Everyone! I'm Linux newbie but quite experienced computer user and I like terminal and solving various software problems. :)

After "3 DAYS" of struggling to install proprietary Nvidia Drivers, following nearly 50 of various advices, ways, manual editing from various posts in this forum, and my own combinations, I have finally made it work in my case. Before that I've had various problems and most of them are described in forums. I think that graphic card problems should be on top of the list for Ubuntu developers because I know that 90% of people would just give up on Ubuntu after such stressing installation of graphic card and forums are full of similar problems.

I've installed Ubuntu 8.04.01 (Hardy Heron) and have Nvidia **GeForce 6600 GT** graphic card and here is a little tutorial:

**1-you have to be connected to internet**

**2-in "terminal" type, and press enter after each line:**

sudo apt-get install nvidia-settings

sudo apt-get install envyng-core

sudo apt-get install envyng-gtk

**3-run EnvyNG program, choose nvidia drivers and let it automatically download by pressing apply; install and reboot**

**4-in "terminal" type, and press enter:**

sudo dpkg-reconfigure -phigh xserver-xorg

**5-reboot**

**6-in "terminal" type, and press enter:**

gksudo displayconfig-gtk

**7-choose your monitor type, resolution and frequency monitor** (mine is LG F900P 1280*1024 75Hz)

**8-in "terminal" type, and press enter after each line:**

sudo nvidia-xconfig

sudo nvidia-xconfig --no-logo

**9-reboot**

**10-in "terminal" type, and press enter:**

gksudo gedit /etc/X11/xorg.conf


**11-now scroll down and find this:** (this was one of the problems: only one third of login screen was visible)

    SubSection     "Display"
        Virtual     2048 1536
        Depth       24

**12-and change it to this:** (or different resolution of your choice)

    SubSection     "Display"
        Virtual     1280 1024
        Depth       24

**13-if your keyboard is not "us" you can change it here too:**

    Option         "XkbLayout" "**us**"

**14-reboot**


Anyway only this and exactly that order worked for me, maybe this could help someone to save time and nerves. I know it probably wont work for everyone, but I will be glad to hear if this way helped someone! :)

Cheers!

---

### Post by tuxxy on 2008-09-15
Good stuff, glad it finally worked for you, I imagine it was worth the wait :)

Also for nvidia cards that run out of the box the 8000 range are good.

---

### Post by niko32 on 2008-09-15
Yeah, it was worth of wait. Ubuntu is fantastic, although must admit I was thinking about other distros when I was troubled by nvidia drivers installation.

> Also for nvidia cards that run out of the box the 8000 range are good.

8000 range?

---

### Post by tuxxy on 2008-09-15
Yes for example 86, 8800 etc

---

### Post by HousieMousie2 on 2008-09-16
niko32,

I don't know if your walk-through works well or not (my nVidia driver installation went fine from the restricted drivers offer after I installed Hardy from CD)...

But I just HAD to comment and say that you did an excellent job of writing out the steps!  So many threads are littered with cryptic code mixed in with abbreviated program and function names that a newbie has no clue what they are looking at, much less what to do with the "help."

Well done! :KS

---

### Post by ycnano on 2008-09-16
Hello niko,
I am having Nvidia geforce Go 6150 driver.
I have installed Ubuntu 8.04.01 (Hardy Heron)on vista with virtual box.
I am getting limited display problem. 
I was following your steps but I encountered problem during running EnvyNG system tool. It was giving error while checking for compatibilty and throwing error as "nvidida card not found" 
So I am not able to follow any further. Can you please provide some solution.
YC

---

### Post by niko32 on 2008-09-16
> **ycnano said:**
> Hello niko,
I am having Nvidia geforce Go 6150 driver.
I have installed Ubuntu 8.04.01 (Hardy Heron)on vista with virtual box.
I am getting limited display problem. 
I was following your steps but I encountered problem during running EnvyNG system tool. It was giving error while checking for compatibilty and throwing error as "nvidida card not found" 
So I am not able to follow any further. Can you please provide some solution.
YC

Well, it might be the fact that you installed it inside virtual box? Anyway you might try installing newest nvidia drivers from their site or search this forum for envyNG nvidia compatibility in virtual box.

---

### Post by ycnano on 2008-09-16
Hello There, 
The solution given by other member I could overcome the problem in step 3 and I could install nvidia 96.x.x series but I stuck in step 6 gkconfig setting resolution. As the resolution is giving only 800 and 640.No change so far.

---

### Post by niko32 on 2008-09-16
> **ycnano said:**
> I stuck in step 6 gkconfig setting resolution. As the resolution is giving only 800 and 640.No change so far.

After typing: gksudo displayconfig-gtk you get a window in which you should try to find your monitor model and select it. After that you can adjust resolution and frequency in same dialog. Apparently it seems that nvidia drivers doesn't recognize correctly some type of monitors.

---

### Post by fsmithred on 2008-09-16
You don't need to reboot all those times. I'm not certain about step 3, but for all the others, you only need to restart the xserver, either by logging out or by hitting ctrl-alt-backspace. Generally, the only time you need to reboot is if you install a different kernel.

---

### Post by niko32 on 2008-09-16
> **fsmithred said:**
> You don't need to reboot all those times. I'm not certain about step 3, but for all the others, you only need to restart the xserver, either by logging out or by hitting ctrl-alt-backspace. Generally, the only time you need to reboot is if you install a different kernel.

Ah that's old habit from windows still sticking with me. :)
At **step 3** actually, after installation of drivers, either system or envyng ask of you to reboot, and at **step 14** only after reboot I saw desired change in resolution of login screen. You are probably right about others.

---

### Post by rmls on 2008-09-17
Just have to say good stuff, worked fine for me (GForce2). I had a few problems with my monitor (iiyama) not listed at step 7, but if you have or can download the .inf for windows you can choose "add" monitor, and browse to the location you put the .inf file .. worked a treat for me.

Cheers
rml

---

### Post by Rhyader on 2008-09-17
"The War to make Multiple Monitors Work"

I've tried your methods, and others; but after 2 days of fighting I still can't get success. The best I can get is something (I've did so many things I can't remember exactly what) that results in getting both monitors to work and work at a decent resolution... but in a strange mode. In this mode the "desktop" is larger than the monitor screen, so that I can't see the entire desktop and have to scroll in all directions just to see the edges of it. This is unacceptable.  I can't even find any system setting that would seem to be related to this functioning.  If there was some way I could turn it off, that setup would be usable.

Ubuntu works just fine with only monitor enabled. I use a nvidia 128 Meg card and run 1600 resolution or higher with no problems. But trying anything to enable a second monitor results in Ubuntu constantly ditching all my settings and changing everything to generic, vesa, 640X480. With a lot of work and several restarts, I can get it to boot with the second monitor enabled at say 1024 and the first monitor generic generic generic 640X40 - then change the first monitor back - twice - and then after 2 restarts it works in the scrolling mode above at #1=1600 and #2=1024. 

I'm at a loss to straighten out or even completely describe the many things that happen.
Suffice it to say the following...
In the screens and graphics settings...
My Working 1 monitor configuration uses a "custom" monitor setting. After trying to change it, the word "custom" no longer appears. I have to pick Gateway ev910c because even though not exactly correct, it's the closest to ev910. I've also tried generic "monitor 1600 X 1200" but either way, it goes into scroll mode. 

I have downloaded and installed the nvidia settings many times.  I have done "sudo dpkg-reconfigure -phigh xserver-xorg" many times. I have run the screens settings utility (gksudo displayconfig-gtk) many times. Each time I save a "location". This does not appear to do anything at all. Each time, if I enable 2 monitors at all, it puts me into a loop where Ubuntu restarts in "low graphics" 640X480 mode, because Ubuntu constantly changes what I entered in the  screens settings utility back to the most generic settings. 

"sudo apt-get install nvidia-settings"
This seems to work, although no program is launched.

"sudo apt-get install envyng-core"
"sudo apt-get install envyng-gtk"

It says it cannot find any such.

"sudo nvidia-xconfig"
"sudo nvidia-xconfig --no-logo"

This seems to rewrite xorg.conf. But nothing really changes. Back to the "you are 640X480 again" loop. 

It's sad that it's so hard to make Ubuntu work with two monitors, and so easy with windows. It's maddening how Ubuntu constantly changes the "screens" settings back to everything generic. It's odd how I have to boot the Suse linux command line to backup and restore Ubuntu linux.  Today I will once more nuke the Ubuntu partition, restore it, and start over with the working one-monitor setup. But at this point I'm only willing to make one last final war on Ubuntu. If I can't win, I'll still use Ubuntu; but only occasionally, to show people how incredibly beautiful it is, and then go back to ugly old Windows so I can have twice the screen real estate. 

If I could get back the the "scroll mode" where I do have both monitors at high resolution, but eliminate the "scroll mode", that would be wonderful.

Scanning the forums, it also seems that problems with screens and resolution, particularly getting unwantedly reset to low resolution generic settings, seem to be very common in Ubuntu. I hope it will improve in the future.

PS: Another hour of forum reading and I see that Envy is a program by Alberto Milone, and you can get it from his webpage without going through "apt-get". 
Here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I shall attempt to use Envy as my next weapon in the war.

---

### Post by niko32 on 2008-09-17
I've had practically every issue you described and lot more with 1 monitor, I can imagine that things can only get worse with 2 monitors. I hope that in next Ubuntu version, which is suppose to be released this October, at least some of the issues will be corrected.

> "sudo apt-get install envyng-core"
"sudo apt-get install envyng-gtk"

It says it cannot find any such.

That's strange, I think I've had this program in repository right after Ubuntu install. (Also I did update right away before installing nVidia divers).

---

