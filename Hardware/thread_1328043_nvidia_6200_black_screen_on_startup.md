---
title: "nvidia 6200 black screen on startup"
date: 2009-11-16
forum: Hardware
---

### Post by benmorrison on 2009-11-16
I installed Ubuntu 9.10 on an old Dell GX260 with an inboard graphics card and everything worked nicely.

I then added a nvidia GeForce 6200 AGP card and the problems began.  When booting up I get to the BIOS screen and then the little white Ubuntu logo, but before the login screen appear the screen goes black and stays black.  Eventually I will give up and hold the power button down and then I get the white Ubunut logo back and then the computer shuts down.

I presume it is a problem with the graphics driver, but how do I install the correct driver when I can't see anything on the screen.  Seems to be a catch-22.

I am relatively new to Ubuntu, but can follow instructions.  Any help would be appreciated.

Thanks

---

### Post by Just A # on 2009-11-18
Hi BM,

I'm going to piggy-back on your thread as I am having difficulty getting my nvidia card working as well. I started a thread in the absolute beginers forum... but haven't got any help yet.

good luck!

---

### Post by Just A # on 2009-11-18
Hey BM,

I'm getting almost the exact same behaviour. Upon restart after installing the nvidia accelerated graphics driver- version 185 the usual BIOS stuff is done, then the GRUB stuff, then the little white Xubuntu mouse/koala icon pops up. Up to this point everything is happening the way it has in the past (ie before nvidia driver update) Then three lines of text appear under the icon:

[COLOR=Blue]filesystem check in progress
/usr(/dev/disk/by-uuid/9772d47-****-***-**) 45%
press ESC to cancel checks

[COLOR=Black]where the ***'s are replaced with numbers and letters that I didn't have enough time to copy, and the last number was a progress % that counted up.

After counting to 100% my screen went black (but not off), then it indicated that no signal was present, then dark (ie off, but still power).

A Hard reboot is about all I could do. (only know three ways: POWER, RESET, <CTL><ALT><DEL>). Hitting "Reset" wakes up my monitor about 5 seconds later with the little white icon in the middle for about a second, followed by a commandline like interface complete with prompt and flashing cursor, but then powers off system about a second later. "Power" shuts down the system with no noticable effects. <CTRL><ALT><DEL> has no effect. After rebooting I could do the steps/commands that I tried in this other thread [http://ubuntuforums.org/showthread.php?t=1329050](http://ubuntuforums.org/showthread.php?t=1329050)  to deactivate the driver, and everything was back to the way it was pre-driver-update.

Subsequent reboots of my system do not include the filesystem check. That only happened the first time. This is odd to me, because the only time the system was shutdown/restarted properly (without hard boot) was the first time. You would think that a filesystem check would be more neccesary after a hard boot?!?!?!

Now, the difference between the screen of colours that I witnessed before, and the screen of blackness that I get now is when I use the DVI-out I get colours and when I use the VGA-out I get blackness. With this in mind, I'm going to recommend to the moderators to merge our threads.

[/COLOR][/COLOR]

---

### Post by Just A # on 2009-11-19
... so I have been trying all sorts of things to get this video card working. I tried using the Ubuntu9.10 LiveCD and installing the nvidia driver while in the LiveCD's environment. After downloading and some auto-configuration I got the black screen, and then power off.

Then I tried installing the drivers directly from nvidia using their directions. This time I was using the 190.42 version. Still the same, after grub, my screen looks like that couch my parents had in the 70's! ...except now I don't know how to uninstall it! becuase my "jockey-text" method doesn't know about this effort.

Finally, after cruising Distrowatch.com I download a couple of distributions that included Nvidia drivers with their LiveCD (Mint-7, Sabayon-5.0 G, pcLinuxOS-2009.2K) Mint-7 had the same result as the Ubuntu9.10 LiveCD. I haven't tried Sabayon-5 yet, But pcLinuxOS recognized my video card without any input from me. It even had an NVidia splash screen. Since my intention is to run one of the ubuntu flavours on my desktop I will need to investigate what differences exist betwenn pcLinuxOS and X/Ubuntu. The most obvious is KDE vs Gnome. Maybe I will try a Kubuntu disk?

---

### Post by Paul D on 2009-11-19
Not sure how new you guys are to Ubuntu, or Linux in general, but I am an old timer with about two weeks behind me. This thread appears to be close to what I have been experiencing with Karmic in that time. I find that these forums are marginally useful for my issues so far. Hard for me to imagine many people who might be trying Ubuntu for the first time would not be having similar video problems. With that introduction, I will make my point. My Nvidia card appeared to work ok for the original Karmic install, but the graphic performance was lacking. A DVD movie video skips from scene to scene every few seconds. I somehow managed to install or enable a Nvidia driver. I think I typed in a command shell sudo xconfig-nvidia or something like it. It created an xorg.conf file that it put in the /etc/X11 folder. When I tried to play the DVD again it played fine. After rebooting the computer, the display came up to a black screen with a blinking command prompt. I inserted the boot CD and got to a non-blinking command prompt, where I managed to delete everything in the xorg.conf file. After rebooting again, I got back to where I started, which is where the DVD video skips. So I can go around and around this cycle all day. I don't know for sure what to do next. There is a system>administration>log file viewer, where you can view what happed as text there. I have looked through there, it mentions stuff about the video driver not found or something like that. I have a friend who messes around with various versions of linux. Just kind of hoping someone posts something to help all of us with this. There is also a tool called Envy, but I don't know if it is meant to work with Karmic or not, for installing video drivers. I think I tried it at one point, and it ended up at the blinking command prompt deal after rebooting.

---

### Post by MIJ-VI on 2009-11-20
> **benmorrison said:**
> I installed Ubuntu 9.10 on an old Dell GX260 with an inboard graphics card and everything worked nicely.

I then added a nvidia GeForce 6200 AGP card and the problems began.  When booting up I get to the BIOS screen and then the little white Ubuntu logo, but before the login screen appear the screen goes black and stays black.  Eventually I will give up and hold the power button down and then I get the white Ubunut logo back and then the computer shuts down.

I presume it is a problem with the graphics driver, but how do I install the correct driver when I can't see anything on the screen.  Seems to be a catch-22.

I am relatively new to Ubuntu, but can follow instructions.  Any help would be appreciated.

Thanks

Hi benmorrison.

I'm fairly new to Ubuntu and use an Nvidia-based EVGA e-GeForce 6200.

As a time-saving workaround, have you considered shutting off your Dell's on-board graphics card in its BIOS and then re-installing Ubuntu so that it only sees the '6200?

Gary

---

### Post by benmorrison on 2009-11-20
Some progress.  I didn't realise you could install the nvidia drivers from the package manager.  I had thought you had to use the Hardware Drivers screen - and as the only way I could access that was with the onboard video card in use (and the nvidia one out of the machine) I never got the chance to select the driver.

So - after installing the driver (185), shutting down, installing the nvidia card and re-starting I got to the Checking filesystems messages and then black screen that Just A# mentions.

I had previously tried just re-installing from the CD with the nvidia card in, but that has not worked either.  I get to the initial menu and choose Install Ubuntu, then get the logo (which changes shades of white), but then get a whole lot of text on the screen - the last line of which is about detecting the file systems - and then it goes black again and nothing appears to be happening.  From memory when I installed with the onboard graphics card I never got the text on the screen, but instead a series of GUI setup screens.  Holding down the power button takes me back to the same screen of text with some shut-down messages.

So - then I thought I would try installing from a Ubuntu 9.04 CD I found (again with the nvidia card installed).  After choosing Install Ubuntu I get the coloured logo with the red/yellow progress bar, but then another couple of screens of text which eventually end in a ubuntu@ubuntu:~$ prompt.  I can enter commands, etc but have no idea how to continue the install from here.

What is going on!

---

### Post by Just A # on 2009-11-23
> **Paul D said:**
> Not sure how new you guys are to Ubuntu, or Linux in general, but I am an old timer with about two weeks behind me. This thread appears to be close to what I have been experiencing with Karmic in that time. I find that these forums are marginally useful for my issues so far. Hard for me to imagine many people who might be trying Ubuntu for the first time would not be having similar video problems. With that introduction, I will make my point. My Nvidia card appeared to work ok for the original Karmic install, but the graphic performance was lacking. 

I believe that this is because you (we) are using default linux drivers up to this point that don't take advantage of the GPU's accelerated graphics processing capabilities.

> **Paul D said:**
> A DVD movie video skips from scene to scene every few seconds. I somehow managed to install or enable a Nvidia driver. I think I typed in a command shell sudo xconfig-nvidia or something like it. It created an xorg.conf file that it put in the /etc/X11 folder. When I tried to play the DVD again it played fine. 

My computer can watch a DVD without any problem using the linux drivers. If you look at the specs of my machine in my signature you will see that my 'puter is nothing special. Are you sure that the nvidia drivers are what is being used to play the DVD correctly? Every method I tried with installing nvidia drivers required a restart before the installation was complete. Perhaps something else is preventing your DVD from playing correctly... something that was fixed using one of the commands that you tried while installing the nvidia card?

> **Paul D said:**
>  After rebooting the computer, the display came up to a black screen with a blinking command prompt. I inserted the boot CD and got to a non-blinking command prompt, where I managed to delete everything in the xorg.conf file. After rebooting again, I got back to where I started, which is where the DVD video skips. So I can go around and around this cycle all day. I don't know for sure what to do next. There is a system>administration>log file viewer, where you can view what happed as text there. I have looked through there, it mentions stuff about the video driver not found or something like that. I have a friend who messes around with various versions of linux. Just kind of hoping someone posts something to help all of us with this. There is also a tool called Envy, but I don't know if it is meant to work with Karmic or not, for installing video drivers. I think I tried it at one point, and it ended up at the blinking command prompt deal after rebooting.

This is different behaviour from what I get (the prompt). I'm in the process of downloading Kubuntu right now to see if KDE vs Gnome is a possible issue. If that doesn't go well, I might look into Envy.

---

### Post by benmorrison on 2009-11-23
Well I got it working, but don't understand why.

I installed 9.04 from the CD, but with the nvidia card out (so using the onboard video card).  Install went fine and then I shut-down and installed the nvidia card and re-started.  Again booted fine and I installed the nvidia driver from the Hardware Drivers screen.  Then upgraded to 9.10 (from the Update Manager) and ... it all worked.

---

### Post by teadystring on 2009-11-23
Hey guys,

I've been running Vista Business 64-bit for a few weeks now. It's been a
mostly good experience for me, with very few complaints. In fact, I've
decided that most of the whining about Vista is totally unfounded.

I have now, however, run into my first killer problem. I have been using an
NVIDIA Geforce 6200 card, but recently bought an XFX 8600GT. I take out my
6200, slip in the 8600, turn my computer on. I see the BIOS screen,
everything looks fine, but as soon as Vista starts booting (at the point
where you would normally see the Vista logo with the loading bar under it),
my screen goes blank! Everything else is still processing normally as after a
bit I hear the Vista startup sound coming out of my speakers. The card works
fine in Ubuntu.

System hardware:
ECS mobo w/ nForce 4 chipset
Athlon 64 3500+ (AM2)
2x Corsair ValueSelect 512MB sticks
430W Cooler Master PSU

I have tried:
1. Auto-repair from Vista DVD. ("Cannot fix the problem automatically")
2. chkdsk /r
3. Ubuntu (works fine)
4. Pulling out all the non-essentials parts.
5. Booting with the latest Forceware drivers and also with no drivers
installed.
6. Applying all the Vista hotfixes recommended by NVIDIA (except SLI ones).

Any ideas?
__________________________________
[remortgage bad credit rating](http://www.adverse-mortgage-centre.co.uk/remortgage-bad-credit-rating.html)
[discount auto insurance](http://www.quotes-auto-insurance-review.com/2009/09/car-insurance-quotes.html)

---

### Post by Just A # on 2009-11-23
> **benmorrison said:**
> Well I got it working, but don't understand why.

I installed 9.04 from the CD, but with the nvidia card out (so using the onboard video card).  Install went fine and then I shut-down and installed the nvidia card and re-started.  Again booted fine and I installed the nvidia driver from the Hardware Drivers screen.  Then upgraded to 9.10 (from the Update Manager) and ... it all worked.

So, maybe the issue arrises when we are trying to install the nvidia drivers under the 9.10 kernel? ...but the driver works fine after an upgrade to 9.10 with the nvidia drivers already installed!

I'll give this a try after I try my Kubuntu install.

---

### Post by Jules Delespy on 2009-12-03
As it turns out, there have been many similar posts since 2005.
The issue is installation on machines where 1) graphics processing is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references where a solution was proposed. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. It seems reasonable to think that it is the best current solution.
The problem has existed in all versions of Ubuntu since at least version 5.10, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_...integrated.txt"]
[/URL][http://www.albertomilone.com/nvidia_int ... grated.txt]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1256691](http://ubuntuforums.org/showthread.php?t=1256691)
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
[http://ubuntuforums.org/showthread.php?t=675497](http://ubuntuforums.org/showthread.php?t=675497)
[http://ubuntuforums.org/showthread.php?t=1308919](http://ubuntuforums.org/showthread.php?t=1308919)
[https://bugs.launchpad.net/ubuntu/+sour ... +bug/55104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104")
[http://www.bikechatforums.com/viewtopic.php?p=2356664](http://www.bikechatforums.com/viewtopic.php?p=2356664)
[http://www.nvnews.net/vbulletin/showthread.php?t=128934](http://www.nvnews.net/vbulletin/showthread.php?t=128934)
[http://ubuntuforums.org/showthread.php?t=196693](http://ubuntuforums.org/showthread.php?t=196693)
[http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)
[http://ubuntuforums.org/showthread.php?t=192677](http://ubuntuforums.org/showthread.php?t=192677)
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)
[http://ubuntuforums.org/showthread.php?t=295133](http://ubuntuforums.org/showthread.php?t=295133)
[http://javadocs.wordpress.com/2008/09/2 ... -gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")
[http://ubuntuforums.org/showthread.php?t=207303](http://ubuntuforums.org/showthread.php?t=207303)
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)
[http://mepislovers.org/forums/showthread.php?t=6487](http://mepislovers.org/forums/showthread.php?t=6487)
[http://www.opensubscriber.com/message/s ... 46049.html]("http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html")
[http://ubuntuforums.org/showthread.php?t=126492](http://ubuntuforums.org/showthread.php?t=126492)

---

### Post by Just A # on 2009-12-04
Great info J.D.!

I think this is the type of help that I was looking for. I don't have enough time right now to read all of the links that you posted... but I will.

One thing to note: my mobo doesn't have a built in graphics chip. So my problem is slightly different.

For those who were waiting for my results of trying Kubuntu... fail. In fact, both live CD's for Kubuntu (KDE) and Ubuntu (Gnome) 9.10 freeze either while running the Cd in Live mode, or during an install. Is this a kernel panic? It is interesting to read once again that people running 9.04 flavours have had much better luck.

I will post more when I get some free time (stupid work!)

---

### Post by karukera7 on 2010-02-21
hello,


after reading several forums with people who are having problems installing "nvidia accelerated graphics driver version 185" and got black screen after rebooting their computer, i do have the same problem and want to know how can i resolve it, wanna know you resolved your problem ? if you can tell me how did u do it ?
me i have a sony vpccw13fd with ubuntu 9.10

---

### Post by karukera7 on 2010-03-02
i finally resolved this problem after reading several forums and finally got this one : 
 
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)
 
i performed steps below, from above link  : 
 
 
[B]The Problem

[/B]For some reason, the current nvidia driver does not auto-detect that a display is attached to an internal digital port. Even if you force the driver to assume a display is attached, it is still unable to read the EDID information from the display. It is this information which tells the driver how to drive the display. Starting X yields just a blank screen. I encountered this problem on a Sony Vaio VPCCW with a GT230M card. I am running Archlinux.

**The Workaround**

The EDID information is detected fine in windows, so we can extract it from there. We then edit xorg.conf to tell the driver that a display is connected to DFP-0 (the internal port) and to use use the EDID we extracted intead of probing the monitor for it. 

Please note: I am just a user and take no responsibility for any problems that may occur as a result of this workaround. Make sure you understand the purpose of each step and proceed at your own risk. 

[LIST=1]
[*]Extract the EDID file from within windows. I used the program softMCCS which can be found [[COLOR=#0000dd]here[/COLOR]]("http://www.entechtaiwan.com/lib/softmccs.shtm"). Open the program and go to *file -> Save EDID as*. The filename you choose doesn't matter, but make sure use the binary (bin) format. Put this on a memory stick or use some other method to copy it to your linux filesystem.
[*]Boot into linux and put the EDID file in your /etx/X11 folder (it could actually go anywhere, but I found this to be convenient).
Code:
sudo mv /path/to/your/edid.bin /etc/X11/.
[*]Backup your current xorg.conf file (if you have one).
Code:
sudo mv xorg.conf xorg.conf_backup
[*]Create a new minimal xorg.conf file. Alternately, you can choose just to add to your existing one.
Code:
sudo touch /etc/X11/xorg.conf
[*]Edit xorg.conf and create a simple device section containing the following:
Code:
Section "Device"   Identifier          "Device0"   Driver              "nvidia"   VendorName         "NVIDIA Corporation"   Option             "ConnectedMonitor"   "DFP-0"   Option             "CustomEDID"          "DFP-0:/etc/X11/youredid.bin"EndSection
Replace "youredid.bin" with whatever you named your EDID file. The two Option lines are what does the trick. The first tells the driver you have a display connected on the internal DFP-0 port. The second tells it not to probe for an EDID, but rather to use the one you are providing.
[*]Restart X and you should see the NVIDIA logo flashing right at you.
[/LIST]
When the driver is next updated, try commenting out the two option lines to see if the bug is fixed.

---

### Post by Heinrich_Evers on 2012-04-12
That's pretty much exactly what happens with my computer with the exception that it's on a clean install of Linux. It works for install but upon reboot GRUB gives me a blank screen.


I had a Geforce FX5200 card running a dual-boot operating system (XP /  Ubuntu Desktop 11.10) and I recently purchased a brand new Gigabyte  Geforce 6200 card. upon boot up The GRUB menu did'nt even display, just a  blank screen. I rebooted, and the issue persisted, so I inserted my XP  install disc booted to that and removed the Linux partitions on my  drive. When I rebooted XP booted perfectly so I figured maybe it was a  driver conflict with the previous FX5200 173 driver. So I re-installed  Ubuntu 11.10 on the blank space freed from deleting the partitions and  it installed perfectly but when it rebooted the same issue occured. Now  I've gone through quite a few threads now and I haven't found report of  this occuring post fresh install with GRUB itself. Is this problem  solvable? If so how?:confused::confused::confused:

---

### Post by nutellajunkie on 2012-07-18
> **karukera7 said:**
> 
**The Workaround**

The EDID information is detected fine in windows, so we can extract it from there..

Why complicate things?

Just got your NVidia X Server Settings UI from the System/Preferences menu.

Select your GPU's DFP-0 section.
Click Aquire EDID and save it as a .bin then continue with Karukera7's help.

---

