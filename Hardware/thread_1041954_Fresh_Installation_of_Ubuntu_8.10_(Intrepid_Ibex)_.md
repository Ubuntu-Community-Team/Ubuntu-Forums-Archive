---
title: "Fresh Installation of Ubuntu 8.10 (Intrepid Ibex) on a Samsung X360"
date: 2009-01-17
forum: Hardware
---

### Post by washakie on 2009-01-17
Instalation of Intrepid Ibex on a Samsung X360:

Background:
Me: An experienced 'amateur' linux user. I use Fedora 9 at work, mostly at the prompt. I have never used KDE or Gnome as a part of my 'workflow'. I have been using coLinux on XP for about three years (a TERRIFIC solution by the way. I wasn't sure if I would go 100% Linux - but after about a week of use, I'm quite sure I will.

Purpose of this document:
To provide an accounting of my software / driver installations and to (hopefully) provide a community resource for those who wish to install Ubuntu on a Samsung X360.

Overview of the OS Installation:

1)To create a live USB installer that worked I used Fedora's liveusb-creator with the Ubuntu image. I would have installed Fedora as it is what we use at work, however, it had too many driver problems initially. I'm not biased, just want to spend the least amount of time possible 'tweaking' my computer. For whatever reason, Ubuntu's live usb stick wouldn't boot for me, but after I installed the Ubuntu.iso file using the Fedora liveusb-creator, it was a simple follow through of the menus.

Update:
I tried both Kubuntu and Ubuntu - notes below marked with (K) apply to the Kubuntu experience.
I have now used Super Ubuntu available here:
[http://hacktolive.org/wiki/Super_Ubuntu](http://hacktolive.org/wiki/Super_Ubuntu)

I believe this likely saved me several headaches with drivers, etc. It seems safe, and I recommend giving it a try.

2)Things that worked 'out of the box' on Super Ubuntu / Ubuntu / Kubuntu:
-Multimedia card reader (only tested SD)
-Mounting USB sticks
-Knetwork Manager and NetworkManager (K)
-Kmix and audio (see note below) and Pulse audio on SuperUbuntu
-Most of the system in general
-Some FN keys (Volume, Numlock, Sleep, mousepad lockout)
-Installing KDE and Gnome was not a problem
-Synaptic works well to install most software
-Adept also works fine

3)Things that have not been tested:
-Bluetooth
-Fingerprint reader *see below

4)Slight Challenges

- Amarok/Audio (it took me a while to get the version 2) and I had to install Xine. Eventually uninstalled the default version (thought 2.0 was default in KDE 4 but it wasn't for me) and followed these instructions:
  [http://www.kubuntu.org/news/amarok-2.0](http://www.kubuntu.org/news/amarok-2.0) 
- FN keys (K) - worked straight away with Ubuntu/Gnome
  Volume controls eventually just magically worked, but it took some 'fiddling' with Kmix and also, as for most FN keys, I found the:
  Kicker>SystemSettings>Keyboard>Keyboard Shortcuts to be very helpful! Especially the section on "KDE components"
- Compiz (consider this a test of the graphics card) (K) works fine on Ubuntu
  I am still having some strange behavior with the X-server / graphics. I have an Intel GMX4500 chipset and haven't changed the default xorg-xserver driver, which I understand should work with Intel. Mostly, it works, but I usually have to login twice in order to see the top bars of the windows. 
- Flash players: Adobe worked in Firefox, Gnash did not.
- Hibernate / Sleep: I haven't tested this extensively yet, but sleep does seem to work. The challenge results from sometimes strange X-behavior following wake. Sometimes I have to logout and log back in. This applies to both KDE and Gnome


5) Unsolved
-Backlight Control (now *patched* see below)
-Battery Usage (related to above)
-Shaky graphics (possibly the 128m is not a good enough card to handle all of compiz effects) - *edit* seems fine now.
-Recognition of a few FN keys (Backlight, Wireless switch, and a few others perhaps specific to Samsung)


General Review of the X360:
Overall
The formfactor is very nice overall, the machine is incredibly lightweight - almost too much so as it feels 'cheap', the screen resolution is good, not great (1400 would be nice), the brightness amazing. I would prefer to have a few 'hard' controls for things such as volume control and wireless. There are essentially no hardware controls aside from the power switch. It seems a little fragile, and I am already noting a few places where the screen seems to get touched by the keypad when the lid is closed. The glossy surface is just that: 'gloss'. I don't find it very practical, and it seems to attract smudges extensively. I have already some scratch on the metal portion of the finish which I am not sure what caused it - clearly something while in my bag.

UPDATE: 20.02.2009
I'm starting to notice rapid deterioration of quality with this machine. The mouse pad is showing signs of de-lamination and the bottom edge of the LCD screen seems to have a problem. Nothing serious yet, but these are causing me some concern... they make me suspect the quality of the machine overall. However, it is still running well, and Ubuntu is as ever, 'rock solid'.

Keypad and Mouse
The 'silver ion' buttons is pure marketing. I have had the machine for two weeks, and already I note 'smudges' on the space bar and e,r,t,i,o keys... typical of any 'used' keyboard. The mouse pad sensitivity drives me nuts, and I am hoping eventually to find a software solution, but I have not yet (**edit see below). All too often is my cursor placed on some random point of the screen as a result of my palms gently hitting the pad. It does have the side scroll bar which I consider essential. The buttons for the mousepad are a bit stiff and 'click' too loudly. The number keys are also a bit scrunched together with the pageup and pagedown keys and I often mis-key pageup for left, pagedn for right.

Bottom / Inside
I tried to open it up out of curiosity, but quit. It simply was not easy. I wanted to 'test' putting in a larger non-Flash HDD, but quickly realized this was getting in over my head. I am curious how I'll add the 1gb more to memory.

Sound
Don't count on the speakers filling a room. They are very 'tin'ee.

Screen
13" is a nice improvement over 12". Brightness is amazing. A slightly higher resolution would be nice, and as I noted earlier, it does seem it may be slightly fragile - only time will tell.

Missing Optical Drive
This is a big feature not to include. If Toshiba and Sony got it in their machines of equivalence... why not here. I didn't think I would miss it, as my prior machine did not have one, but recently I have found myself missing it.

Installation Notes:

*Installation of the fingerprint reader*
1) followed all instructions here:
[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

followed trouble shooting and chgrp of /dev/bus/usb from root:root to root:plugdev... hasn't worked yet.

*Touchpad sensitivity*
This was critical as the touchpad is entirely too sensitive and drove me crazy. Follow these instructions:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

*Backlight Control*
I was able to get a 'fix' following the work here, note the entry from washakie later in the thread as well.
[http://ubuntuforums.org/showthread.php?t=1031764](http://ubuntuforums.org/showthread.php?t=1031764)

---

### Post by daizumi on 2009-01-18
Thanks for this post! Very helpful, since I just bought this machine 12 hours ago. On my previous notebook I used ubuntu for everything, except for the casual game I had a dual boot.

I bought this machine for its portability and battery life. Can you tell me something on how the battery in ubuntu relates to that in Vista? Is it comparable? And the time it takes to suspend?

---

### Post by washakie on 2009-01-21
Suspend is still a little flaky, but it works well about 8 of 10 times. As for hibernate, I get a strange error, something about not enough space to dump memory despite have a 6 gb swap partition with only 3gb ram.

As for the time things take, let's just say there is no longer enough time for me to get a coffee while rebooting. In fact, I can barely get up from my seat before I'm being asked to log in again!

---

### Post by daizumi on 2009-01-30
Thanks for the reply. And how does the battery life relate to the battery life in Vista?

I've been using Ubuntu for years, this is the first time I'm on vista cause it came with the machine, and its not all that bad. It's a bit slow though. I might go back to ubuntu, but I do not want to sacrifice portability. What do you say are the pros for ubuntu on this machine? Is it faster?

---

### Post by avilella on 2009-02-07
Hi,

I took the liberty of creating a Linux Launchpad team for the people who own or develop for the Samsung X360 series laptop, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~samsung-x360](https://launchpad.net/~samsung-x360)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~10 users I've identified so far.

Cheers,

Albert.

---

### Post by feydrutha on 2009-02-14
Has anyone manged to install 64 bit ubuntu (or any linux for that matter) on this laptop? I am not so happy with having 32bit ubuntu on a machine with 4GB ram, as some memory will not be accessible (unless you use PAE).

I created an installation USB-stick using the tool that comes with ubuntu (on intrepid, it is under system->Administration->Create a USB startup disk). If the USB stick is formatted fat-32, it doesn't work at all, so I had to make sure it was fat-16 (I used gparted). I also had to change boot order in the bios on the x360 to make sure I would boot from it.

I tried the intrepid alternate iso s for the 32 and 64 bit version. The 32 bit version seems to work, although I haven't actually gone through with the installation (need to decide what to do first). 

With the 64 bit version, I get to the initial screen of the ubuntu installation, choose the language, choose "install", then the system reboots and I am back to the first screen of the ubuntu install cd. This is an endless loop so it doesn't seem to be working. Anyone had better luck?

The PAE kernel option would be an alternative way of making use of my 4GB of memory. Apparently it is enabled in the ubuntu server kernel, but not in the desktop kernel. So I suppose I could do a desktop install, and then install the linux-server package (or do a server install, and then install the desktop package). Apparently the server kernel is not as user-friendly as the desktop one because the restricted drivers packages are not available for it. Do I need any restricted drivers for ths hardware?

I will try this now, and report on what I find.

UPDATE: I also tried using UNetBootin to install the 64-bit intrepid alternate cd directly from the hard drive, and got similar results. Eventually the system just reboots on its own. So this does not seem to be a USB-related issue.

---

### Post by FelixFBL on 2009-03-07
Hey

I have bought a Samsung X360 with the SSD drive and I would really like to use Linux, but I’m a complete newbie in Linux and not very experienced working with OS. I created a live USB installer Fedora's liveusb-creator as proposed by Washakie. I changed the priority boot list in the bios and Ubuntu started up. I ran the “install without any changes…” and began the installation from Ubuntu. Step 4 the guided resize will “only” divide and share the first half of my entire 128GB SSD. I thought it was obvious to install Ubuntu on the second partition. I then tried to use the second partition - I selected manual partition in step 4. Selected the free space…. And what should I do now……

I have learned at bit now! I have made a partition “/” for Ubuntu, as primary, Ext3, in the beginning, at the amount 10 GB and pressed “ok” 

Problem is first of all, after I pressed ok and the new partition was created, I’m asked to highlight the free space and continue to create /swap and /home, but the installer will not give access to the free space! I can’t make a new partition in the remaining 45gb??
   
And then I want to make a swap (6gb!) but there are no option: “/swap” 
What of the options are equivalent to swap?? “/boot, /tmp, /usr., /var, /srv, /opt, /urs/local???

I hope someone can help.

/Felix

---

### Post by feydrutha on 2009-03-14
Hi FelixFBL, hope this answer doesn't come too late to be useful to you.

I have not used the fedora installer, and also I do not quite understand exactly what you are trying to do. Do you want a dual boot system with windows and linux, or only linux?

> **FelixFBL said:**
> 
And then I want to make a swap (6gb!) but there are no option: “/swap” 
What of the options are equivalent to swap?? “/boot, /tmp, /usr., /var, /srv, /opt, /urs/local???


This at least I can answer. Those /boot, /usr, etc are "mount points". That is, they are the place on the file system where that partition will be found.. sort of like drive letters C:, D: etcetera under windows. Swap does not have a mount point, because it is not really part of the file system. To make a swap partition you should look at another option, probably selecting "swap" in the same menu where you select the file system type "ext3" for normal partitions.

---

### Post by feydrutha on 2009-03-14
> **feydrutha said:**
> Has anyone manged to install 64 bit ubuntu (or any linux for that matter) on this laptop? I am not so happy with having 32bit ubuntu on a machine with 4GB ram, as some memory will not be accessible (unless you use PAE).


About this issue... I installed the server kernel and now I can see the full 4GB of RAM (instead of just 3), and everything else is still working fine.

Just install package linux-server (sudo apt-get install linux-server), reboot and you're set.

---

### Post by FelixFBL on 2009-03-14
Hi feydrutha

Thanks for the answer. It's not to late. I'm still carefully planning this installation.

Yes I'm trying to make a dualboot. I want to use wireless conection to the server at work, copenhagen municipal, (not only surfing the web, but share the domaine or something) and my college says that I need to to use windowsXP. One college says that it can harm/dammage the hardware having and running dualboot?

Is it risky to have dualboot on the X360?

Making a dualboot - do anyone have some suggestions about the installation!


/Felix

---

### Post by feydrutha on 2009-03-14
> **FelixFBL said:**
> 
Yes I'm trying to make a dualboot. I want to use wireless conection to the server at work, copenhagen municipal, (not only surfing the web, but share the domaine or something) and my college says that I need to to use windowsXP.


You will be able to connect to wireless under linux without much trouble, I think. But if you need some kind of domain authentication I don't know, you may be able to do it under linux, depends on what it is exactly. Dualboot seems like a good idea so you can try everything out, and have windows available if you really need it. 

> **FelixFBL said:**
> 
One college says that it can harm/dammage the hardware having and running dualboot?

Is it risky to have dualboot on the X360?


No, that is really not true. There is certainly no risk of hardware damage. Of course if you really mess up installation you could end up in an unausable state, but nothing that cannot be fixed in software (by re-doing an install, or maybe even using the recovery tools installed by samsung)

> 
Making a dualboot - do anyone have some suggestions about the installation!


Since you are a first time user, I suggest you use "guided" partitioning,
choosing the option to resize the windows partition and automatically resizes the remaining space for you. There is a guide on how to do that here: 

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p24.html) 

He is using ubuntu hardy, but it shouldn't be very different if you are using the newer version (intrepid).

---

### Post by dietwaterrr on 2009-03-16
Does anyone know if the hdmi port works??

Does anyone know how to get the microphone to work? 

Thanks.

---

### Post by feydrutha on 2009-03-30
> **dietwaterrr said:**
> Does anyone know if the hdmi port works??

Does anyone know how to get the microphone to work? 

Thanks.

I have not tried the HDMI port yet.. I'll try to do that in the next couple days, since my external monitor has an HDMI input. (EDIT: I never ended up trying that because I don't have an HDMI cable...)

The built-in microphone has worked out of the box here... you may need to play with the mixer settings a bit. Right-click on the volume icon and select "open volume control". Go to preferences. Checking boxes in the preferences menu selects whether these options will be displayed in the volume control. Make sure front mic boost is selected (and maybe also mic boost..). Without the boost sound recording volume was too low. Now in the volume control try playing with some of the settings and testing it with the "sound recorder" application until you are happy with the results. I think you need to select "front mic" as input source. I have "front mic boost" up at about 1/3, and capture up at the top.

Also, if you use skype be sure to disable the option to "allow skype to automatically adjust my mixer levels" as in my experience it automatically messes them up ;-)

---

### Post by dietwaterrr on 2009-04-02
> **feydrutha said:**
> I have not tried the HDMI port yet.. I'll try to do that in the next couple days, since my external monitor has an HDMI input.

The built-in microphone has worked out of the box here... you may need to play with the mixer settings a bit. Right-click on the volume icon and select "open volume control". Go to preferences. Checking boxes in the preferences menu selects whether these options will be displayed in the volume control. Make sure front mic boost is selected (and maybe also mic boost..). Without the boost sound recording volume was too low. Now in the volume control try playing with some of the settings and testing it with the "sound recorder" application until you are happy with the results. I think you need to select "front mic" as input source. I have "front mic boost" up at about 1/3, and capture up at the top.

Also, if you use skype be sure to disable the option to "allow skype to automatically adjust my mixer levels" as in my experience it automatically messes them up ;-)

thanks, I'll try that out later. I remember when I enabled front mic, it was really annoying because the recorded audio would always play back to the speakers/headphones.

---

### Post by FelixFBL on 2009-04-13
Hi 

I hope someone could help me out with the backlight issue!

I aks Yetiicom at this thread - **Brightness adjustment not work - Samsung X360**- but didn't get a reply.

I'm kind of new in this Linux and OS business, so maybe some one could guide me a little more.

yetiicom wrote

Add this command to System->Preferences->Sessions->> +Add
xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto

this command allow adjust LCD brightness by gnome brightness applet, and set about 40% brightnes default (180 set to 70%). Parts "--output VGA --auto" set graphic mode for console - check it by press Ctrl+Alt+(F1-9)


this is very helpful - I can easyli follow these directions.... I also understand how to run the gconf-editor in the terminal - and I found "global keybindings"....

but then things get technical.. I have no idea what to do with the following directions........

Check actual parameters, all changes should be list:
xrandr --prop


II. Look for right keycode to set.

xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'

This will only output pressed keycode and currently assigned keysym, for example:

160 XF86AudioMute
174 XF86AudioLowerVolume
176 XF86AudioRaiseVolume


III. Set short-cuts and right command to change brightness.

install xbacklight:
sudo apt-get install xbacklight

check if you can change backlight from console (command repeated few times should take visible effect):
xbacklight -inc 10
or
xbacklight -dec 10

Is it possible if someone can help me out!

/Felix

---

### Post by sokolovss on 2009-06-16
I've bought Samsung X360 and got the same trouble with installation. The x64 version of Ubuntu reboots after choosing language and boot option.

How can I fix this problem?

---

### Post by feydrutha on 2009-06-18
I was not able to boot the 64 bit version. Just use the 32-bit version instead. 

Then just install the linux-server package and you will be using  all 4 GB of RAM anyways, so no big problem (the only real advantage of 64 bit architecture is the ability to use more RAM).

---

### Post by sokolovss on 2009-06-18
As I understand there are not so many differences between Linuk kernels 32 and 64 bits. Windows 7 x86-64 works great (boot - 10 seconds, shutdown - 4 seconds), so I thought that Ubuntu amd64 can be also so fast.

May be it's just a boot parametr, that should be fixed or BIOS settings? Any ideas? I installed amd64 version from alternate installer, but then was unable to boot.

Also, how do you turn the bluetooth off? (With blacklist of modprobe) And hoe is to get every hotkey work?

---

### Post by sokolovss on 2009-06-22
OpenSolaris x86-64 and Windows 7 x86-64 both works. So, that's really problem with x86-64 Linux Kernel

---

### Post by sokolovss on 2009-08-13
Ubuntu amd64 works!

All you have to do is update your BIOS to the newest version available on Samsung website and Ubuntu will work fine and "see" all 4 Gb of RAM.


But backlight control stopes working after several reboots, that is bad.

Also, how is to turn bluetooth off? But not with modprobe blacklist, because I may need to use it without rebooting.

---

### Post by feydrutha on 2009-08-22
> **washakie said:**
> Instalation of Intrepid Ibex on a Samsung X360:

5) Unsolved
-Shaky graphics (possibly the 128m is not a good enough card to handle all of compiz effects) - *edit* seems fine now.


Hi,

what do you mean "seems fine now"? Any idea what you might have done to fix it? 

For me compiz works but it is very slow. The compiz benchmark tool shows <30 fps most of the time. Even scrolling down a window in firefox is annoyingly slow, and alt-tabbing is a pain. I am pretty sure it is not that the card cannot handle this, it must be some kind of driver problem. Under vista (the 2 times that I booted into) the GUI was pretty snappy. Also I have seen an eeepc with ubuntu+compiz doing all of the most flashy effects, and it has an intel card which is supposedly less powerful than the one on the x360 (sorry, I forget the models). Anyone have any insight on how to debug such problems?

Edit: 
Did you update your firmware? which version do you have?
Also, are you still using intrepid, or did you upgrade to jaunty? It seems that jaunty specifically has a performance problem with intel cards:
[http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904#Other%20known%20issues)

I tried following this howto:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This has at least solved the problem of scrolling in firefox, which is now nice and smooth. Alt-tabbing in compiz is still very slow.

I followed instructions for the "safe" option, but I had to remove one line from the xorg.conf or X would not even start. This is the offending line:

Option		"AccelMethod"			"uxa"

Also, the fixmmtr.sh step makes no difference, so it does not seem necessary. I have had no problems with video playback. 

So basically the things to do are:

1) add this text to the Device section of /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" 
EndSection

2) Add the X Updates PPA to your sources.list and upgrade, as described in part B of the guide
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by feydrutha on 2009-11-26
Just a quick self-reply to say that the karmic upgrade fixed my graphics issues. I reverted the changes I have made (discussed in the previous post) before upgrading. I am now using compiz with a few flashy options enabled and everything is nice and snappy.

---

### Post by washakie on 2010-01-11
Hey all... OP here.

I just wanted to ask if anyone else is experiencing a strange, seemingly random crash of the X server/OS from time to time.

I don't know what triggers it, but periodically, my entire system just freezes hard. It's not often enough to totally piss me off, but it's too often for me to be comfortable making a strong endorsement. Overall my system, now running:

Linux fieldbook 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

with Compiz

runs like a charm. But periodically (it seems to happen most often with a desktop switch, or google aps such as googleearth or picasa) my entire screen just freezes. I can't do anything except a hard kill. No response from CTRL-F keys or CTRL-ALT-Backspace... nothing.

I have another identically configured laptop (HP nc4400) which has no problems.

Any thoughts?

Best to y'all!

---

### Post by feydrutha on 2010-04-11
washakie, I have not been having any random crashes on mine, but I am running a 32-bit pae kernel, so that may make the difference.

uname -a says:

Linux 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux

---

