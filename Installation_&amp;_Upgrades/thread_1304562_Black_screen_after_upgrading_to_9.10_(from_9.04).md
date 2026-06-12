---
title: "Black screen after upgrading to 9.10 (from 9.04)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by gully on 2009-10-29
An Ubuntu upgrade wouldn't be complete without a black screen on boot or something component failing that worked just fine in the previous version.

So here it is, after the installation the system reboots and hangs on a black screen, no disk activity whatsoever.

Great f*cking job canonical, this is like the third time an upgrade completely f*cks up my system!

---

### Post by NormanFLinux on 2009-10-29
If something failed during the upgrade process, it won't boot up correctly. You'll have do a clean install. But sometimes its best to do it from scratch for the best results. ;)

---

### Post by pablo180 on 2009-10-29
> An Ubuntu upgrade wouldn't be complete without a black screen on boot or something component failing that worked just fine in the previous version.

I agree, having been forced to upgrade after stupidly updating to Jaunty and finding out that Xorg uses 60% CPU at idle, rendering it useless, I stupidly thought Karmic might solve the problem, instead it goes one better and doesn't even bother to boot!

It starts to boot up, but as above, just stops and leaves me with a black screen.

Now I have the choice, spend hours restoring my backup, to then spend more hours attempting to upgrade again and have the same thing happen, put up with only be able to use 40% of my CPU at best, or go right back to an old back up of Intrepid.

Good job I took the day off.

---

### Post by sheetzam on 2009-10-29
If you were using a third party video driver, that'll happen.  Personally, I had the same issue, and had to re-install the NVIDIA drivers.  All was beautiful after that!

---

### Post by niite on 2009-10-29
> **sheetzam said:**
> If you were using a third party video driver, that'll happen.  Personally, I had the same issue, and had to re-install the NVIDIA drivers.  All was beautiful after that!

Same here - just installed my nvidia driver via command line, and all was good with the world after.

---

### Post by upchucky on 2009-10-29
your system is not f---up, your understanding of it falls a little short, this is understandable as the vid drivers can not possibly be bloated to allow every possible combination of pc to boot up a display. (remember that unlike windows, Linux is custom built for the machine it is set up on) thus by trying to have it work "right out of the box" on every bit of hardware out there, it would suck just like windows. 

since you never indicated your machine specs, you will not get quality help from anyone, it is impossible to doctor a patient if the patient is not there.

if by chance you are having trouble with a nvidia card,there is only one proper way to set up a nvidia card with ubuntu. there are a few other ways that kinda work but they are only tweaks and patches that do not properly set up the card to its full potential, these are known as workarounds not solutions.

you never need to redo an install nor do you need to install again from scratch, just learn your system and you will find that unless you have purposely destroyed Linux system files the solution to most problems involves editing the right files.
Linux is not the same as windows where windows self destructs or lets the user destroy it without warning.

to set up an nvidia card, follow the instructions here to the letter.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by MisterSix on 2009-10-29
> **upchucky said:**
> your system is not f---up, your understanding of it falls a little short, this is understandable as the vid drivers can not possibly be bloated to allow every possible combination of pc to boot up a display. (remember that unlike windows, Linux is custom built for the machine it is set up on) thus by trying to have it work "right out of the box" on every bit of hardware out there, it would suck just like windows. 

since you never indicated your machine specs, you will not get quality help from anyone, it is impossible to doctor a patient if the patient is not there.

if by chance you are having trouble with a nvidia card,there is only one proper way to set up a nvidia card with ubuntu. there are a few other ways that kinda work but they are only tweaks and patches that do not properly set up the card to its full potential, these are known as workarounds not solutions.

you never need to redo an install nor do you need to install again from scratch, just learn your system and you will find that unless you have purposely destroyed Linux system files the solution to most problems involves editing the right files.
Linux is not the same as windows where windows self destructs or lets the user destroy it without warning.

to set up an nvidia card, follow the instructions here to the letter.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

That response seems a little harsh!!! I also have a black screen of death after a clean install of Karmic, and I have an Asus motherboard with an Nvidia vid card connected to a Dell 2407 LCD.
This isnt an exotic setup!!! 
Two boards made by the biggest manufacturers in their field, so "Ya", I do expect it to work without having to mess with it.  Also the fact that you point to a forum post that is a year and a half old indicates that this has been a known issue for a LONG time...
Maybe we could of lived with ext3 a while longer IF they could have used the time to fix a fatal install bug with the largest manufacturer of video cards....
So actually Canonical IS acting a lot like Microsoft, ignoring bugs that should have been fixed a long time ago. As for being bloat-ware, I just spent most of the day torrenting down the 3.85 GB iso, so "yeah"... it is bloated and I do expect it to work.

---

### Post by upchucky on 2009-10-29
> **MisterSix said:**
> That response seems a little harsh!!! I also have a black screen of death after a clean install of Karmic, and I have an Asus motherboard with an Nvidia vid card connected to a Dell 2407 LCD.
This isnt an exotic setup!!! 
Two boards made by the biggest manufacturers in their field, so "Ya", I do expect it to work without having to mess with it.  Also the fact that you point to a forum post that is a year and a half old indicates that this has been a known issue for a LONG time...
Maybe we could of lived with ext3 a while longer IF they could have used the time to fix a fatal install bug with the largest manufacturer of video cards....
So actually Canonical IS acting a lot like Microsoft, ignoring bugs that should have been fixed a long time ago. As for being bloat-ware, I just spent most of the day torrenting down the 3.85 GB iso, so "yeah"... it is bloated and I do expect it to work.

Sigh!

I am not trying to be harsh, just trying to point out a valid reason for the trouble. the fact that the post i pointed to is an old post indicates that the proper way to set up a nvidia card was fixed long ago and all one needs to do is search for Nvidia in these forums and low and behold there is the fix.

there is no fatal install bug to speak of, in fact ubuntu will boot up with a GDM just fine with generic settings, its when one wants to have a 3d display that the card needs to have the driver installed properly.

your dell lcd is the problem, generic install does not recognize the lcd and does not know what to set the frequencies at. you will need to find out the refresh rate and mode settings for the lcd, then edit those settings into the xorg.conf file.

since it takes so long for you to obtain the os of your choice, why not get a bare bones copy then  add only programs to it that you really need, this is the beauty of Linux, you do not need to install stuff you are never gonna need. there are versions available from 50meg all the way up to 3.5 gig. most cd's have around 650 meg, and you can add to that or remove stuff and create your own custom installable version with about an hours work.

---

### Post by pablo180 on 2009-10-29
> **upchucky said:**
> your system is not f---up, your understanding of it falls a little short, this is understandable as the vid drivers can not possibly be bloated to allow every possible combination of pc to boot up a display. 

Mine's not an Nvidia, but an Intel graphics chip, and the drivers do come with the default installation of Ubuntu, they also worked fine on the Live CD. Which is the ironic part, the only reason that I was updating was to get the fixed graphics drivers as they were broken (and never fixed) on Jaunty. 

But my guess is that it isn't just to do with the graphics drivers, lots of people seem to be having problems. 

I've spent 12 hours trying to update, failing and then trying to restore from a backup, bloated Windows may be, but I have never had this much trouble with it.

---

### Post by MisterSix on 2009-10-29
> **upchucky said:**
> there is no fatal install bug to speak of...Oh no, it is fatal... the install program is still running, but I can't see it, so effectively it might as well be hung!

> **upchucky said:**
> ...your dell lcd is the problem, generic install does not recognize the lcd and does not know what to set the frequencies at.  Well the obvious solution was to change monitors, and {drumroll...} this didn't help a bit, same exact problem when I switched over to a Samsung monitor. I have about 8 monitors in my home, but somehow I didn't think it was worth trying the rest of them...


> **upchucky said:**
> ...you will need to find out the refresh rate and mode settings for the lcd, then edit those settings into the xorg.conf file.Well I already know those, but there is nothing to edit... sda1 (hard drive) has been freshly reformatted, but nothing is on it yet...  So are you saying I have to edit xorg.conf file on the iso image, then re-burn the DVD???


> **upchucky said:**
> ...since it takes so long for you to obtain the os of your choice...  Well I don't mind the bloat as long as it works!!!  It's that feeling of having wasted my time d/ling this when it wont even complete an install.
Also wasn't there something called "Bulletproof" that was going to solve this??  What happened to that?
I mean defaulting to a 640x480 60Hz display seems to be an obviously solution, then the user could install whatever drivers where needed.  In fact why does the install application even care about higher resolutions, 3D support, etc.  Just keep it simple.

---

### Post by RJARRRPCGP on 2009-10-29
Huh? 3.8 GB? Give me a break! Ubuntu is only around 700 MB! Ubuntu fits on one CD!

---

### Post by saulysw on 2009-10-30
> **niite said:**
> Same here - just installed my nvidia driver via command line, and all was good with the world after.

Please can you provide details on how to do this, exactly?! Thanks!!

---

### Post by MisterSix on 2009-10-30
> **RJARRRPCGP said:**
> Huh? 3.8 GB? Give me a break! Ubuntu is only around 700 MB! Ubuntu fits on one CD!You are quite correct, the "Ubuntu Installer" is 690MB... but that is just the installer, it will then download the rest.
If you d/l the entire iso image for Ubuntu it is 3937 MB.

Actually, your comment gave me an idea, maybe the installer would work where the iso image doesn't... So I am going to give the installer a try, before I give up and re-install 9.04.

BTW just to enumerate the details of issue here (since there is so much written about display issues):
I am using an Asus motherboard (P4S533) 2GB of RAM with a Nvidia 7600GS video card connected (via analog VGA) to a Dell 2407 LCD display.

I am using a DVD with the full iso image burned to it.
The PC cold boots up and recognizes the bootable DVD and boots up.
It asks for language to use (I select the default "English")
It then displays the usual start up menu, I select "Install Ubuntu"
The slowing fading in and out Ubuntu logo is displayed in the center of the screen..... The DVD drive trundles.... For several minutes... I get a brief flash of the textual status and then the monitor goes to black and the Dell monitor reports and "out of range" signal.
Pressing a ctrl-alt {keypad minus} or {ctrl-alt {keypad plus} results in various different screens being presented, all  unreadable.  One screen does present in an almost readable (but not really) way the request from the install to select a language.
I cant really proceed from here as the next few steps cannot be read well enough to proceed.

So.... pressing ctrl-alt-F1 presents the text based command line.... moving to /etc/X11 I find only a couple of files, certainly no xorg.conf file that could be edited to include the H&V refresh settings or video card settings....
And there I am stuck....  Any ideas?

---

### Post by gully on 2009-10-30
> **upchucky said:**
> your system is not f---up, your understanding of it falls a little short, this is understandable as the vid drivers can not possibly be bloated to allow every possible combination of pc to boot up a display. (remember that unlike windows, Linux is custom built for the machine it is set up on) thus by trying to have it work "right out of the box" on every bit of hardware out there, it would suck just like windows. 

since you never indicated your machine specs, you will not get quality help from anyone, it is impossible to doctor a patient if the patient is not there.

if by chance you are having trouble with a nvidia card,there is only one proper way to set up a nvidia card with ubuntu. there are a few other ways that kinda work but they are only tweaks and patches that do not properly set up the card to its full potential, these are known as workarounds not solutions.

you never need to redo an install nor do you need to install again from scratch, just learn your system and you will find that unless you have purposely destroyed Linux system files the solution to most problems involves editing the right files.
Linux is not the same as windows where windows self destructs or lets the user destroy it without warning.

to set up an nvidia card, follow the instructions here to the letter.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

The thing is I have an ATI card (the 5870), I installed the latest drivers for it a couple of days ago, the driver version included with Karmic is actually older then what I had, so if the driver is the problem someone at Canonical really screwed up if they programmed the installer to A) overwrite a newer driver and B) make it so that the older driver doesn't even install properly.

I know my installation can be saved, and I did, I removed the fglrx drivers manually from the recovery menu, then reinstalled them, then I was greeted by a desktop with a "hardware not supported" watermark, then I reinstalled the drivers from ATI's website and all is fine, but if that's the way it's gotta be with every upgrade it really isn't surprising more people aren't switching to Ubuntu.
Imagine you had a black screen after every Windows Service Pack upgrade, you wouldn't accept that now would you?

Sure I found a way out, but the average PC user would've assumed their install was dead, so yeah, way to f*ck up Canonical, way to maintain Linux's image as an OS that only programmers and enthousiasts can work with.

So it would be nice if Canonical included a warning to uninstall video drivers before upgrading, it would be even better if they didn't let their installer overwrite an existing newer driver.

Oh, by the way, I have the following system with a Compaq monitor: Graphics: ATI HD 5870, CPU: Intel i7 920, Memory: 6GB of 1600mhz OCZ RAM, HDD: 1TB Seagate, Mobo: ASUS P6T SE, I know this isn't an exotic setup, if Karmic won't boot with my setup it won't boot for a lot of people.

---

### Post by MisterSix on 2009-10-30
Woohoo.... fixed it!

OK, Using the full install DVD (3.8GB) of Ubuntu 9.10 Karmic I did the following:
Insert DVD into target PC
Cold boot PC
Select the language of choice (in my case "English")
From the main Ubuntu Install menu select &#8220;Install Ubuntu in text mode&#8221;.
Let the installer complete it's install including answering all the usual questions (machine name, time zone, default account, etc).
Once the install is complete, remove the DVD and reset the PC
Ubuntu boots and once again doesnt work, the screen goes blank or displays the "out of range" error.
Press ctrl-alt_f1
A text window should appear
Login to Ubuntu using the name and password you gave it.
Then at the command prompt type:
sudo apt-get install nvidia-glx-185
(Note: this is ONLY for Nvidia video cards)
Allow it to install (including all dependencies), once it is back at the command prompt then... reboot the PC.
As before use ctrl-alt-f1 to get to a login screen and login.
At the command prompt type:
sudo nvidia-xconfig
Once that completes there will now be an xorg.conf file in /etx/X11.
So then at the command prompt type:
cd /etx/X11
sudo nano &#8211;w xorg.conf
And manually make changes to the "Monitor", "Device" and "Screen" sections for your particular video card and monitor.  Save the file and reboot the PC.
It should now work!

I have attached my edited xorg.conf which will work for nvidia and the Dell 2407 LCD, but yours will be different.
Google for your particular configuration.

No guarantees (I really don't know what I am doing), but this worked for me.  Enjoy!

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Device0"
    Option         "DPMS"
    Modeline       "1920x1080@60" 182.28 1920 1952 2640 2672 1080 1102 1113 1135
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Device0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```

---

### Post by upchucky on 2009-11-02
Very happy u spent the time to figure it out, and gratz to you.

as one does more reading and experimenting they learn just how powerful a pc really is, I too had that whoo hooo feeling when the light came on and i started to understand. the next thing to grasp is GRUB,and how to repair a non bootable machine, from there one needs to ensure that they have a separate home partition. this can ensure that when one of your experiments does what you tell it to do instead of what you wanted it to do, you can safely have all your files intact and only have to do some editing to get the os bootable again.

---

