---
title: "Installing on HP Mini 1000"
date: 2008-11-11
forum: Hardware
---

### Post by gotrevgo on 2008-11-11
Hi all,

Sorry if this has been covered but I wasn't able to find anything helpful. Has anyone successfully installed Ubuntu on the new HP Mini 1000? It ships with XP now and will come with a custom version of Ubuntu in the new year but I can't wait to get it. 

I'm using it almost exclusively for writing so my needs are relatively limited but I'd be interested to know if I should expect any problems installing or overall compatibility issues. 

Thanks!

---

### Post by gotrevgo on 2008-11-16
I'll definitely post a more thorough explanation but I installed 8.10 using an external CD and everything just worked. I upgraded the wireless drivers but right after installation everything appeared to be completely supported.

- Audio from internal speaker
- Video in proper resolution
- Wireless
- Keyboard layout
- Function keys (brightness, volume, hibernate)

Suspend:
I set it to suspend when closing the lid and prompt with the reboot / suspend dialog when I press the power button. Pressing the button worked and displayed the dialog but closing the lid only turned the display off. I think that's part of the firmware, I'm not sure. Later I set the power button to suspend the machine, which it also did without issue. This seems to cause the machine to suspend when the lid is closed, though it's not that reliable. It seems to work about 50% of the time. This is the only problem I've really run into, hopefully something can be done to make it sleep every time I close the lid, as I have drained the battery a few times already.

Battery:
This might be flaky, it runs on battery without issue but I'm not sure how reliable the guage is.

I'm working on a more detailed blog post and will link to it here. If anyone would like me to test something in particular just let me know. Ultimately it went perfectly for someone who has decades of experience with the Mac but no knowledge of Linux.

---

### Post by powderific on 2008-11-16
Thanks for the info, how do you like the Mini 1000 so far? Right now I'm debating between it, the Dell Inspiron Mini 9, and the Acer Aspire One. I do have a couple questions, if you don't mind:

What's your battery life like?
Does the wireless work ok with WPA secured networks?
Does it reliably suspend if you just press the power button? Not suspending properly would be a huge deal breaker for me, but I wouldn't mind just pressing the button.

Incidentally, I'm also planning on using whatever I get primarily for writing, so, how has it worked for you thus far?

edit: also, how's the trackpad? Does scrolling and whatnot work well?

---

### Post by bwmcadams on 2008-11-17
> **powderific said:**
> 
What's your battery life like?
Does the wireless work ok with WPA secured networks?
Does it reliably suspend if you just press the power button? Not suspending properly would be a huge deal breaker for me, but I wouldn't mind just pressing the button.

Incidentally, I'm also planning on using whatever I get primarily for writing, so, how has it worked for you thus far?

edit: also, how's the trackpad? Does scrolling and whatnot work well?

I got my Mini last Tuesday and it works fantastically with Ubuntu.  I installed via USB stick, it has been flawless.  Just stay away from Kubuntu - it was a freaking mess and I reOSed and will just have to stick with Gnome for now.

The wireless works great with WPA - I have a WPA2 network at home.  The wireless driver does seem a bit ... flakey. Mostly just that they don't get nearly as good reception as they should, but nothing major.  Seems to be a result of the proprietary broadcom drivers ubuntu installs.  Hoping to find a good answer to this.

When I push the power button (it's actually a switch that you slide) Ubuntu presents me with a menu asking if I'd like to suspend, hibernate, restart, log out or cancel.  Works great, and suspend / resume has always been reliable.

I don't have a good answer on battery life, but the keyboard size is fantastic - something like 90% size versus a real keyboard, and I have fairly large hands which seem perfectly happy touch typing (with an occasional fat fingering of the wrong key).

The mouse works fine - both tap-clicking and scrolling work out of the box on Ubuntu with no tweaking.

---

### Post by powderific on 2008-11-17
Thanks for the great info, bwmcadams!

Bummer about kubuntu being messed up. KDE has been my favorite WM since I first started using linux. Oh well, it isn't a huge deal, especially when the HP seems like such a great notebook in general.

---

### Post by bwmcadams on 2008-11-17
To be fair, based on what I've seen and read it's more an issue of KDE 4.x being really unstable than any slight against the Kubuntu team.  

To clarify, the "deal breaks" I ran into with Kubuntu:

- Graphics "glitching".  
    + KDM on startup, anything outside of the 4:3 portion of it looked tiled and glitchy - hard to explain but you'd understand if you saw it
    + When opening the menu for the first time after logging in, or any panel in the menu, you get "tv static" where the window will be before the window draws.  It happens w/ some apps as well.  Brief, but annoying and demonstrates that Kubuntu is a poor choice at the moment.

- App crashing
    + Randomly, some apps would crash out X completely.  A great example is the Twitter widget for the KDE desktop that shipped w/ Kubuntu.  Reliably, it would load, try to grab my tweets, and crash out the desktop.

- Power management glitches
    + Under Gnome, when I flip the power switch I get a dialog asking what I want to do.  I love this, and since there's a switch rather than a button I can use it as a deliberate action to get a menu.  In Kubuntu/KDE, the laptop IMMEDIATELY shuts down.  I dug into this and it turns out that the power button ACPI action under Ubuntu/Kubuntu hasn't been udpated for KDE 4.  Essentially, it looks and says "If Gnome is running, run it's dialog.  If KDE is running, run it's dialog. Otherwise, call `shutdown now`".  The KDE detection is still looking for KDE 3 - that call doesn't "find" 4.  I found out the right call for 4 and got that to work, but was unable to find a working call to kick up the KDE dialog box.

Overall however, the Mini is fantastic.  I should note I love the build quality, and the murderous, covetous looks I get from my coworkers while I lovingly stroke it, while cackling insanely.

---

### Post by powderific on 2008-11-17
Yeah, it seems like the new kde has been causing problems for many people. Works great in virtual box on my Mac though! I quite like the improvements. That said, X crashing is not something I feel like dealing with.

Glad to hear the Mini is as nice as the review sites say. Hopefully there'll be some way to pick up MIE and any other HP specific stuff once they come out with their own ubuntu version.

---

### Post by davidsiegel on 2008-11-18
I bought the HP mini 1000 a week ago and I can't stop raving about it. Ubuntu works *flawlessly* out of the box. Even suspend and the webcam work! My friend has the Dell Mini 9 - we put them side-by-side and there is no comparison; the HP blows the Dell out of the water in terms of style, keyboard, screen size, and Ubuntu support (he still cannot get Ubuntu on the machine). Best $400 I've ever spent.

---

### Post by yogipsu on 2008-11-19
To echo the earlier comments, Ubuntu installed on the Mini (via USB stick, after some errors with usb-creator) without issue.  I only have two problems, and hopefully they're easy to resolve:

(1) The internal microphone doesn't work.  Even with capture maxed in the volume controls, or even with pulseaudio disabled entirely, I get nothing.  Does anyone's mic work on the Mini 1000?

(2) Does the touchpad support multitouch? I'd like to enable two finger scrolling and two finger tapping, especially given the layout of the touchpad.

Thanks!

---

### Post by swlaird on 2008-11-20
I love my new Mini 1000 (XP, 60GB, 1GB, etc.) but I had a few things I had to do:
1. Could NOT install from external CD/DVD (tried every method). Had to install from USB stick made using System->Administration->Create a USB startup disk on another PC. It's faster than a cd anyway!
2. Applied the screen tweak from the Acer Aspire One community documentation:
[https://help.ubuntu.com/community/AspireOne#Screen%20Tweaks](https://help.ubuntu.com/community/AspireOne#Screen%20Tweaks)
This allows you to move a window out of the screen to reach the buttons at the bottom.
3. Stopped the hard drive clicking using the same docs:
[https://help.ubuntu.com/community/AspireOne#Stop%20hard%20drive%20death%20click](https://help.ubuntu.com/community/AspireOne#Stop%20hard%20drive%20death%20click)
Follow the links from the site above for more solutions. (NOTE: all of these "fixes" can be dangerous.)
4. Applied the video tweaks to stop the video artifacts when using Compiz:
[https://help.ubuntu.com/community/AspireOne#VIDEO%20AND%203D%20PERFORMANCE:%20(Optional](https://help.ubuntu.com/community/AspireOne#VIDEO%20AND%203D%20PERFORMANCE:%20(Optional))
5. 2GB stick of Crucial RAM (Amazon - $29.99) arrives tomorrow. Looks like others have had success.
[http://blog.laptopmag.com/hp-mini-1000-upgrade-opportunities-easy-access-to-ram-and-sim-slot](http://blog.laptopmag.com/hp-mini-1000-upgrade-opportunities-easy-access-to-ram-and-sim-slot)

Other than that, everything worked. A recent Ubuntu upgrade seems to have fixed the audio crackle on shutdown problem I was having.

Screen - 10.2 is much better than 8.9
Touch pad - Works great (now two finger gestures that I've found) but I use a laptop mouse and I can disable the touchpad whild typing.
Keyboard - Fantastic
Speed - Even though sites say it's slower than the Aspire One, I disagree!
Hard Drive - Want a 64 or 128GB SSD but gotta wait until they drop in price (alot!). Wish it was 2.5" instead of 1.8". More options!
SD Slot - worked out of the box. Aspire One would only work if you boot with the SD card in the slot.
Wireless - Worked out of the box, even on wake. (Takes awhile, though. Gotta be patient!)


--
Steve

---

### Post by commandokoj on 2008-11-20
At [MyHPMini.com](http://myhpmini.com/forum/how-to-ubuntu-on-the-mini-t107.html) forum member cmot got it installed...

Said there were no issues at all (same with others that answered above)

[_Install Ubuntu on the Mini_](http://myhpmini.com/forum/how-to-ubuntu-on-the-mini-t107.html)

---

### Post by yogipsu on 2008-11-21
So, I figured out the mic problem.

First, you need to do the following.

```
sudo nano -w /etc/modprobe.d/alsa-base

Add the following:

options snd-hda-intel model=ref

... then reboot.
```

Second, under System->Preferences->Sound, make sure Capture is set to ALSA.

Third, go into Volume Control. Edit its preferences. Make sure you can change the following: (1) IEC958, (2) IEC958 Default PCM, and (3) Input Source [the first one].  Make sure the IEC958 and IEC958 Default PCM boxes are checked, and change the first Input Source to Line.

Then open up Sound Recorder and see if it works!

---

### Post by regu on 2008-11-27
> **yogipsu said:**
> So, I figured out the mic problem.

First, you need to do the following.

```
sudo nano -w /etc/modprobe.d/alsa-base

Add the following:

options snd-hda-intel model=ref

... then reboot.
```

Second, under System->Preferences->Sound, make sure Capture is set to ALSA.

Third, go into Volume Control. Edit its preferences. Make sure you can change the following: (1) IEC958, (2) IEC958 Default PCM, and (3) Input Source [the first one].  Make sure the IEC958 and IEC958 Default PCM boxes are checked, and change the first Input Source to Line.

Then open up Sound Recorder and see if it works!

yogipsu, many thanks for the tip.  I've been trying to fix the internal mic and now it works with your method.  Except I notice that IEC958 and IEC958 Default PCM can be left unchecked.

I still have the following issues and wonder if anyone else have these problems? (I installed intrepid using netboot)

1) can't get the external mic using the combo jack to work yet.

2) screensaver (it only blanks the screen) and sleep doesn't automatically work in battery mode.

3) Wifi using WPA-PSK can't connect with hidden SSID networks.  No problem though if using WEP Passphrase or if the SSID is advertised.

4) if you plug in a SIM card in the slot inside the battery socket, a new pan0 device shows up under ifconfig.  has anyone gotten 3G mobile to work? (assuming it's possible)

aside from these the mini is working great with ubuntu.

---

### Post by kaffaman on 2008-11-29
Hey, guys. I too run Ubuntu 8.10 on HP mini 1000 (STAC92xx audio). Instead of running usual install, i chose alternate CD (command line system), then installed Xorg, wmii and so on. Problem == sound. 
 
When tying to play music / test speakers  i get no errors, but so sound either. 

Yeah, i tweaked/searched a lot ;0)

Here is some info: 

uname -a : 
   Linux mini 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686

1)  options snd-hda-intel model=ref IS added to /etc/modprobe.d/alsa-base

2)  output of "aplay -l" 
    card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
--- should there be "device 0" [STAC92xx Digital] (used to have it before)

3) alsamixer/alsamixergui used to set Master & PCM, nothing is (MM) muted

4) No errors from   "/etc/init.d/alsasound restart" : 
     Shutting down sound driver: done
     Starting sound driver: snd-hda-intel done

5) Output of /etc/init.d/alsa-utils restart  :
 * Shutting down ALSA...                  [ OK ] 
 * Setting up ALSA...                     [ OK ]

6) Output of " lsmod | grep snd " 
   snd_hda_intel         428308  0 
   snd_pcm_oss            46496  0 
   snd_mixer_oss          22912  1 snd_pcm_oss
   snd_pcm                83844  2 snd_hda_intel,snd_pcm_oss
   snd_hwdep              15492  1 snd_hda_intel
   snd_seq_oss            39936  0 
   snd_seq_midi_event     15232  1 snd_seq_oss
   snd_seq                58480  4 snd_seq_oss,snd_seq_midi_event
   snd_timer              29448  2 snd_pcm,snd_seq
   snd_seq_device         15500  2 snd_seq_oss,snd_seq
   snd                    66212  9        snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16776  2 snd_hda_intel,snd_pcm

7) Did try compiling by hand (alsa-driver-1.0.18, alsa-lib-1.0.18, alsa-utils-1.0.18) & running alsaconf, and ./snddevices (makes /dev/snd*) 

8) cat   /etc/rc.local   : 
   rmmod snd_hda_intel
   modprobe snd_hda_intel
   exit 0

9) cat /etc/modprobe.d/sound   : 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

10) Here is the list of installed stuff: aptitude search '~i' | grep alsa
   alsa-base                    
   alsa-oss                        
   alsa-source                
   alsa-tools-gui                  
   alsa-utils                                                  
   alsamixergui                   
   libesd-alsa0                   
   libsdl1.2debian-alsa           

11) cat /etc/modules : 
   loop
   lp
   fuse

12)  cat /etc/modprobe.d/sound 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel


Thanks for your help!

---

### Post by inverseroom on 2008-12-07
Hey all--I'm considering getting a Mini 1000, now that the price has come down by $40.  A couple of questions.

1) I would like to run it with 2gb of memory.  Is there room for another stick, or would I have to replace the 1gb stick with a 2gb one?  (I realize that the Linux version, when it comes out, will have 2gb, but my current laptop is about to die)

2) Is the 6-cell battery available yet, do you know?

3) does anyone have a link to a step-by-step on how to install from a USB drive?

Thanks!

---

### Post by NeverM$4Me on 2008-12-08
> **inverseroom said:**
> Hey all--I'm considering getting a Mini 1000, now that the price has come down by $40.  A couple of questions.

1) I would like to run it with 2gb of memory.  Is there room for another stick, or would I have to replace the 1gb stick with a 2gb one?  (I realize that the Linux version, when it comes out, will have 2gb, but my current laptop is about to die)

Only one RAM slot available. So buying a 2GB stick is your only option.

> **inverseroom said:**
> 2) Is the 6-cell battery available yet, do you know?

AFAIK, it will be available in the 1st quarter of 2009.

> **inverseroom said:**
> 3) does anyone have a link to a step-by-step on how to install from a USB drive?

From ubuntu community doc:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by inverseroom on 2008-12-08
Thanks for all the info!  Is it possible just to use the "make bootable USB drive" command under system>>administration on my present laptop?

---

### Post by eloyhc on 2008-12-13
> **commandokoj said:**
> At [MyHPMini.com](http://myhpmini.com/forum/how-to-ubuntu-on-the-mini-t107.html) forum member cmot got it installed...

Said there were no issues at all (same with others that answered above)

[_Install Ubuntu on the Mini_](http://myhpmini.com/forum/how-to-ubuntu-on-the-mini-t107.html)


He replaced WinXP, does anybody have seen a dual boot Ubuntu/WinXP?

---

### Post by Souness on 2008-12-21
Just got my HP Mini 1000 a few days ago (couldn't wait till x-mas to open it haha). So far I'm loving it.

I got the 16gb SSD, 1GB ram,  8.9 inch screen, bluetooth, webcam with mic. XP works well once I switched everything to be more performance oriented. I feel the SSD works extremely well considering I thought it might be a little sluggish. For me, the $$$ for the 10.2 inch screen didn't sound worth it and I am very happy with the size of the screen. 

First thing I did after getting everything in XP working was to try and install ubuntu 8.10. I created a bootable usb drive using my other ubuntu machine and started the install process. I ran into a problem when there was no resize option for the SSD partitions. After researching a bit, I found out that the option would show up after running chkdisk on XP. After I ran chkdisk, booted into windows, and restarted the installation procedure the option to resize the XP partition on my SSD showed up.

After that, everything installed quickly and easily. Once I booted into the Ubuntu partition, everything worked great and everything was fully functional. I installed skype but haven't messed around with it too much so I'm not sure if I'll have the mic problem. The only other problem I ran into was that the battery gauge doesn't show the remaining time, only the percentage of battery left. Compiz and emerald are working great and I was especially amazed at how well 480P HD movies ran. The sound is also amazingly loud and clear. Everything is running great on 1 GB ram and I can't see myself needing to upgrade to 2GB considering that I don't think I'll be using anywhere near that much memory in the short periods of time that I'll be running the mini.

---

### Post by kitara on 2008-12-23
Hi all. I have (had) a dual boot hp mini setup (1030 NR).  I was unable to install from the memory stick.  I was able to get in, but ubuntu could not see my hard drive.  I tried solutions for partitioning through windows but these also failed.  I eventually had to wipe clean unetbootin (second thing that I had tried) and use wubi to install.  I attributed Wubi install failures (stating that the cd was in use) to having already tried unetbootin first. 

If I had thought that I would be posting, I would have better documented my travails, but I thought I would share. 

Right now I am having to reinstall because I seem to have borked Gnome power manager while trying to install Adobe flash.  :confused:

I will probably let everyone know how it goes.

---

### Post by jswinner on 2008-12-26
Flash to the latest bios, then unetbootin works, with 8.10, after running chkdisk in windows first.  Otherwise it does not report the doze partion size correct and you you cannot shrink it.

Have not checked every piece of HW, but it all seems to "just work".

---

### Post by eloyhc on 2008-12-27
what about the fan?

it never stops!

---

### Post by Souness on 2008-12-30
> **eloyhc said:**
> what about the fan?

it never stops!

I can hardly even hear it. You must be in an absolutely silent room to have it bother you. Mine runs most of the time, if not all of the time also though.

---

### Post by Souness on 2009-01-06
Has anybody figured out why the screensaver goes just to a black screen and doesn't actually start up?

---

### Post by bigav on 2009-01-06
I have the hp 1000 and I installed 8.04 but now the wifi driver is not present, how do I fix this?  Should I install 8.10 would that be the easy way to fix this problem, or do I need to install a driver for the hp mini 1000?  Thanks

---

### Post by bigav on 2009-01-06
I have a hp mini 1000, and I just installed ubuntu 8.04, but now the wireless feature is not working.  How do I fix this problem, should I just install the 8.10, do you think this will fix my problem?    

Thanks

---

### Post by darylkris on 2009-01-07
hi, i just bought an hp mini 1033cl, and i would love to install ubuntu 8.10 on it. everytime i try to install it through unetbootin, the installer wont detect my hard drive, and i can't resize the partition on windows. i'm a novice when it comes to this kind of stuff, so a step by step tutorial would be awesome.. i.e. how to flash bios? run chkdsk? i'm a noob -__-

thanks for any and all help

---

### Post by Souness on 2009-01-09
> **bigav said:**
> I have a hp mini 1000, and I just installed ubuntu 8.04, but now the wireless feature is not working.  How do I fix this problem, should I just install the 8.10, do you think this will fix my problem?    

Thanks

Well, I haven't installed 8.04 but I know for sure that 8.10 has wireless that works without any extra drivers or anything needed.

---

### Post by Souness on 2009-01-09
> **darylkris said:**
> hi, i just bought an hp mini 1033cl, and i would love to install ubuntu 8.10 on it. everytime i try to install it through unetbootin, the installer wont detect my hard drive, and i can't resize the partition on windows. i'm a novice when it comes to this kind of stuff, so a step by step tutorial would be awesome.. i.e. how to flash bios? run chkdsk? i'm a noob -__-

thanks for any and all help

You can check my earlier post, I have covered this problem. I found that unetbootin didn't work for me. What you need to do is download the 8.10 distro and create a livecd. Then, run the livecd and create a bootable usb drive. Follow my instructions for running chkdsk and then you will have the option to resize during the install.

---

### Post by Souness on 2009-01-09
Also, I'm having trouble connecting to the WPA2 AES enterprise connection at work. It just freezes when it tries to connect. Has anybody else had this problem. All other connections (WEP, WPA2) have worked fine but this one seems to freeze the entire system. If anyone can confirm this issue it would be helpful.

---

### Post by stuarto on 2009-01-09
Hi, I've installed intrepid on HP Mini 1000 and wifi works for WEP but not WPA. The network isn't hidden, and it is visible in gnome-network manager, but the WPA authentication never completes. 

The result is the same with both the wl driver and ndiswrapper (I followed the tutorial [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") using both HP and alternate dell 4315 drivers.

I had a crack with wicd without any joy, so I don't think network-manager is to blame. Interestingly the Ubuntu Hardware Testing app reports the chipset as 4312 but lspci -n reports 14e4:4315.

A new version of the broadcom driver ([http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php") was released at the end of December and I tried installing it with no success.

Other than wireless the rest of the hardware seems to work fine.

Right, that's all I know! If anyone has any ideas that would be much appreciated.


Stuart

---

### Post by G-Dub on 2009-01-10
I have installed Xubuntu on the Mini 1000 and it is running quite well! The only thing I cannot get to work is the webcam! I've tried easycam and was unsuccessful. Anybody have an idea?

---

### Post by philwil on 2009-01-16
I have the web cam working with application cheese.  had to change the resolution in cheese preferences to lowest setting.

philwil

---

### Post by G-Dub on 2009-01-19
thanks philwil that worked!

---

### Post by G-Dub on 2009-01-19
> **Souness said:**
> Has anybody figured out why the screensaver goes just to a black screen and doesn't actually start up?

I believe this is a power saving feature. If its plugged in, the screensaver works.

---

### Post by chud67 on 2009-01-20
The Linux version of the HP Mini is out now (and it's Ubuntu!), see [this thread]("http://ubuntuforums.org/showthread.php?t=1045239").

---

### Post by silvari on 2009-01-25
I've got an HP Mini 1030NR (1GB RAM, 16GB SSD, WinXP) purchased at the end of November '08. I was able to shrink the Windows partition and get Ubuntu 8.10 installed (via USB), dual booting with XP, without much hassle.

Upon installing Ubuntu 8.10, my first impression was, "Everything *just works* out-of-the-box! Woo!" 

But I've since discovered the following problems:

1. The WiFi doesn't work when I'm at the office, where WPA2 is in use. At home, I use WPA, and it works fine. Also has worked fine with WEP. I've read elsewhere that the WPA2 issue is due to the Broadcom drivers.

2. There is no driver present / loaded for the Marvell Yukon wired ethernet adapter, which sucks, because then I've got no hope for getting connected when I'm at the office. Unless I boot to XP, in which case both the wireless and wired adapters work fine.

Other than that, have had no issues. Sound worked fine as-is, I didn't have to do any monkeying around, though I haven't done any audio input or recording with it - just playback.

I really love this machine. It's super lightweight but is easy to work with - the keyboard is very easy to use. 

It's just too bad that sometimes I need to boot into Windows to work :-(

---

### Post by spacepluk on 2009-01-25
Hi silvari,
I'm using ethernet although [sometimes it's not detected](http://ubuntuforums.org/showthread.php?t=1047061). Try rebooting until you get it.

Saludosss

---

### Post by Bailywolf on 2009-02-03
*bump*

-B

---

### Post by Redenbacher on 2009-02-26
> **jswinner said:**
> Flash to the latest bios, then unetbootin works, with 8.10, after running chkdisk in windows first.  Otherwise it does not report the doze partion size correct and you you cannot shrink it.

Have not checked every piece of HW, but it all seems to "just work".

I'm trying to install 8.10 on my 1035NR (Love this machine by the way)

With both unetbootin and the USB Flash utility in System -> Administration, the partitioner does not recognize Windows on my system and suggests that I install over the entire partition.

When you say Flash to the latest bios, and unetbootin works after running chkdisk... do you mean using the hard disk self test utility, in the Bios, or using the chkdisk run command in windows?

---

### Post by Redenbacher on 2009-02-27
I've run both the Bios self test and chkdisk in windows, and the partitioner still refuses to read the partition on there.

It shows one single 60GB partition that is currently NTFS format. No options available to resize :(

What happened to the nifty little slider that let me choose the new partition size, so I wouldn't overwrite Windows?

---

### Post by Redenbacher on 2009-02-27
Bump

---

### Post by Redenbacher on 2009-02-28
Bump

---

### Post by Saghaulor on 2009-02-28
You could use clonezilla to backup your windows partition. Then if you accidentally screw anything up, you have a backup to fall back on.

Clonezilla is very easy to use, and very quick and effective.

---

### Post by Saghaulor on 2009-02-28
My Wifi was working just fine, up until a few days ago. Now it seems that the wifi switch is not working properly, as it is glowing amber rather than blue. I've tried to slide it to the left, hoping that it will turn back on, but to no avail.

Any suggestions on how to get this wifi working again?

---

### Post by skibrianski on 2009-03-05
> **Saghaulor said:**
> My Wifi was working just fine, up until a few days ago. Now it seems that the wifi switch is not working properly, as it is glowing amber rather than blue. I've tried to slide it to the left, hoping that it will turn back on, but to no avail.

Any suggestions on how to get this wifi working again?

Saghaulor, I've just had the exact same problem on a brand new machine (bought about 30 hours ago, problem cropped up about 6h ago). Since I had saved a backup of my windows install before installing ubuntu, I restored it and booted to it to see if maybe windows did something fancy and the problem was with ubuntu. Nope. An hour on the phone with HP confirmed that.

In my case, the problem happened like this: First, I tried to connect a BT keyboard, with no luck. Since I had been able to connect a BT mouse and my phone, I thought maybe there was some bad state somewhere and reset would do the trick. So I powered the machine off and removed the power cord and battery, waited 30 seconds, and powered it on again. I'm pretty sure but I don't recall for sure that the wifi was still working at this point so I don't think it was a hardware problem (yet), but instead just me not knowing how to associate this BT keyboard (BT is knew to me). Anyway, when I powered the machine back on, wifi and bluetooth were gone, and have not yet returned.

I'm guessing the problem is that the battery is a little too close to where the wifi/BT chip lives, and that the moderate jostle from the battery cage is enough to pop it out of place. It's remotely possible that the wifi/BT loses some state it needs when the laptop battery goes away, but I'm doubting that theory more and more.

I'm returning my machine to the store I bought it at tomorrow to exchange for an identical one. You might have to ship yours back to HP - the person I spoke with did offer me that option, although it means a week or two without your machine.

I'll update with news of what happens with that one. I plan on giving the battery a few moderate jostles on the way in to make sure the thing won't pop out on me as soon as I get home (hopefully without lossening that connection up!). Meanwhile, Saghaulor, do you have a bluetooth icon on your panel? If you don't, I strongly suspect the problem you're having is the same as mine.

Good luck!

---

### Post by Saghaulor on 2009-03-05
Oddly enough, the wireless card started working all by itself again.

I removed the battery, and returned it, however, that didn't seem to do anything. 

One night it works, the next night it doesn't, then a few nights later it works again. Very strange.

I can't answer regarding bluetooth, as I removed all bluetooth software. I've stripped ubuntu down as much as I could. Basically, I just want the machine to get out to the net, and firefox to run. Obviously security is a must.

I have nine of these; we use them as internet kiosks for my field staff with Verizon's UM175 aircard. But as there is a 5 gig/month bandwidth limit, I like to use my home wifi for downloading, not to mention it's faster.

So, even though I most of these machines rarely use the wifi, it would be nice to have it work when it's supposed to.

---

### Post by skibrianski on 2009-03-05
Saghaulor, do you have this problem on all of your netbooks or just the one? I'm guessing the BT/wifi card is just not seated properly and it seems to randomly work based on where it has most recently been jostled. Have you left windows on any of them? Might be an interesting data point to see if it works under windows (I doubt it - I re-imaged windows on mine and the wifi/BT are still broken, the wifi led still orange instead of blue).

Cheers...

---

### Post by skibrianski on 2009-03-06
> **skibrianski said:**
> I'll update with news of what happens with that one. I plan on giving the battery a few moderate jostles on the way in to make sure the thing won't pop out on me as soon as I get home (hopefully without lossening that connection up!). Meanwhile, Saghaulor, do you have a bluetooth icon on your panel? If you don't, I strongly suspect the problem you're having is the same as mine.

Welp, I'm flummoxed. I exchanged my system for a brand new one at the store, and brought it home. copied my image of ubuntu on, and strated playing around with it. Then I decided to get brave, powered it off, and remove the ac adapter and battery. Waited 30 seconds, and powered it up again. What do you know, the wireless and bluetooth stopped working (an additional note, I didn't mention it the first time, but the MBR seems to have been clobbered both times - I had to boot to USB and then re-run grub-install to fix it).

So my current theory is that this is a software thing, and there is some info on the hard drive that the machine is set to use. I plan on going to the store and testing this tomorrow. If it's not some sort of magic recovery routine, I have to suspect that HP has a serious problem on its hands and didn't test what happens when the wifi/BT chip is removed from power, which would bode quite poorly for people taking netbooks on trips and running out of juice, etc.

Very, very disappointing. The kbd and screen are so right! Sigh.

---

### Post by Dj TweeX on 2009-03-06
Hello All!
I have had my Hp Mini 1030 N since December. i ran the included XP on it for about an hour, installed windows 7 (worked great) then Vista (worked great) then ubuntu. ive bee using ubuntu for about 4 years now & its amazing.

i recentally installed the "HP version of Ubuntu" via the website 
& it works... after about 3 hours of tweaking everything is working. but the spound through the headphones is like that of the sound through the headphones in XP

when i installed 8.10 the sound worked perfectly. so here is my question. does anyone know how i can get my hands on a diffrent driver for sound? the one HP supplied for XP & "MIE" both suck for the headphones.

also the mic works in the "MIE" skype is perfect.
^_^
~~Gabe~~

---

### Post by skibrianski on 2009-03-07
> **skibrianski said:**
> So my current theory is that this is a software thing, and there is some info on the hard drive that the machine is set to use. I plan on going to the store and testing this tomorrow. If it's not some sort of magic recovery routine, I have to suspect that HP has a serious problem on its hands and didn't test what happens when the wifi/BT chip is removed from power, which would bode quite poorly for people taking netbooks on trips and running out of juice, etc.

Ok, this is now officially bizarre. I was sitting in the parking lot by the store preparing to return the unit (re-imaging the drive with windows XP by booting off a flash drive), and what do you know? The blue wifi light came on again. So whatever the heck that problem is, it's sporatic.

So, I've decided to keep this thing and see how it goes. I also noticed that ssh doesn't always work on netbook remix, so I've scrapped that and gone with a full intrepid/x86 install this time (and left 100MB unused at the beginning of the drive in case my theory about what happens when the battery runs out is correct). Perhaps some of my problems were related to UNR? Anyway thanks all and cheers!

---

### Post by edvan on 2009-03-16
hello guys, i got a HP Mini 1000 (1001TU), the one with 60gb HDD and running on XP...

I did a dual boot with Ubuntu 8.10 and it is running great, have not tried the wireless connection as I am running on LAN for the moment...

But I do notice went I shutdown Ubuntu, just before powering off it makes a few cracking noises, not sure if anyone notice it??? anyone know how to resolve?

thanks...

still working on mic and webcam...

---

### Post by skibrianski on 2009-03-16
> **edvan said:**
> But I do notice went I shutdown Ubuntu, just before powering off it makes a few cracking noises, not sure if anyone notice it??? anyone know how to resolve?

still working on mic and webcam...

As for the mic, there are some messages in this thread already, but I haven't tried them. I know the webcam works out of the box with cheese (apt-get install cheese if you don't already have it), but it's so dark that it's hardly useful unless you are outside. I have the crackling noise on reboot too, but I don't think its anything to worry about (unless the noise itself bothers you). Good luck!

---

### Post by dbuurman on 2009-03-16
> **edvan said:**
> hello guys, i got a HP Mini 1000 (1001TU), the one with 60gb HDD and running on XP...

I did a dual boot with Ubuntu 8.10 and it is running great, have not tried the wireless connection as I am running on LAN for the moment...

But I do notice went I shutdown Ubuntu, just before powering off it makes a few cracking noises, not sure if anyone notice it??? anyone know how to resolve?

thanks...

still working on mic and webcam...

Affirmative, i noticed the cracking sound as well. I'll investigate wether it can be re-produced when fiddling with sound settings or loading/unloading the sound module. 

[Webcam works out of the box afaik? ]("https://help.ubuntu.com/community/Webcam")

---

### Post by richardtom on 2009-03-16
anyone noticed the screen getting slowly darker when on battery? constantly having to turn up brightness again and again

---

### Post by edvan on 2009-03-17
> **dbuurman said:**
> Affirmative, i noticed the cracking sound as well. I'll investigate wether it can be re-produced when fiddling with sound settings or loading/unloading the sound module. 

[Webcam works out of the box afaik? ]("https://help.ubuntu.com/community/Webcam")
tested my webcam and it works out of the box... tested with Ekiga... :D

---

### Post by Saghaulor on 2009-03-17
> **skibrianski said:**
> Saghaulor, do you have this problem on all of your netbooks or just the one? I'm guessing the BT/wifi card is just not seated properly and it seems to randomly work based on where it has most recently been jostled. Have you left windows on any of them? Might be an interesting data point to see if it works under windows (I doubt it - I re-imaged windows on mine and the wifi/BT are still broken, the wifi led still orange instead of blue).

Cheers...

Unfortunately, the 8 other netbooks are floating around in the field with my clinical staff. So I don't see them very often. Consequently I can't actually answer your question at this time. I'll let you know more when I know more.

I've reimaged all of them with Ubuntu 8.1, using clonezilla. For most of them, the first time that they were powered on was to format and reimage. So unfortunately, I cannot confirm or deny whether it's an Ubuntu only problem or a hardware failure.

---

### Post by m626rider on 2009-03-17
ahh, do you happen to have the URL for the HP mini ubuntu ISO?

---

### Post by skibrianski on 2009-03-17
Anyone else noticing that the volume when using the headphone jack is dreadfully quiet? I've tried 3 different headsets, and they all have the same problem... Kind of odd considering that the onboard speaker is much more powerful than I would have expected...

---

### Post by skibrianski on 2009-03-17
Thanks for the data point, Saghaulor... I was wondering if the wifi/bt thing happened if you were running windows only, because once it happens booting into windows doesn't fix anything. It's really frustrating, and the only workaround I've found so far is to make sure the battery doesn't get down to zero...

---

### Post by m626rider on 2009-03-17
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68020-1&lc=en&dlc=en&cc=us&lang=en&os=2020&product=3832488](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68020-1&lc=en&dlc=en&cc=us&lang=en&os=2020&product=3832488)

---

### Post by skibrianski on 2009-03-22
I've noticed recently that when unplugging the system from AC power, the system sometimes goes straight into suspend mode, say half of the time... Is anyone else having this problem?

---

### Post by ajkenney on 2009-03-25
> **skibrianski said:**
> I know the webcam works out of the box with cheese (apt-get install cheese if you don't already have it), but it's so dark that it's hardly useful unless you are outside. I have the crackling noise on reboot too, but I don't think its anything to worry about (unless the noise itself bothers you). Good luck!

If you're a bit adventurous, you can get the solution to the dark webcam problem [here]("http://www.youtube.com/watch?v=sc4rZUcUkIc").  It's actually as simple to do as it looks in the video.  I did it with my HP Mini 1000 and I'm very happy with the results.

The noise problem is also present on mine.  As it doesn't happen in Windoze (I have a dual boot), I assume it could be solved with some type of configuration change that mutes the audio during shutdown.  Any of you coding guys got a handle on that yet??

Cheers,

Andy

---

### Post by skibrianski on 2009-03-25
> **m626rider said:**
> [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68020-1&lc=en&dlc=en&cc=us&lang=en&os=2020&product=3832488](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-68020-1&lc=en&dlc=en&cc=us&lang=en&os=2020&product=3832488)

Hmm, unsurprisingly this is just ubuntu netbook remix. I can tell from the installer but didn't go further yet since I need a backup first. m626rider is it customized in any useful fashion?

---

### Post by skibrianski on 2009-03-27
> **skibrianski said:**
> Hmm, unsurprisingly this is just ubuntu netbook remix. I can tell from the installer but didn't go further yet since I need a backup first. m626rider is it customized in any useful fashion?

Wow, HP's remix is much better than the free UNR image... For starters it uses a much better launcher/panel thingee than netbook-launcher, and the theme is pretty sweet too. I'll definitely be playing with this more, if not to just grab some of the artwork to move to my stock ubuntu install :-)

---

### Post by skibrianski on 2009-03-27
Oh, and the crackling sound on reboot problem still happens with HP/UNR, fully updated.

---

### Post by bigbrovar on 2009-03-28
I just installed jaunty Netbook Remix on my hp mini 1000. am pretty much impressed with the looks and how snappy it is. everything worked out of the box including wireless and all the fn keys the only problem am having with it is sound. i have never had a sound problem before hence i don't even know where to start trouble shooting. funny enough sound worked when i tried eeebuntu 1.0 which is based on hardy heron. also i noticed that the jaunty netbook edition doesnt come with the new notification system since the the desktop version. can any confirm if this is the way it was designed or a bug..

---

### Post by Jonothewright on 2009-03-28
I am also thinking of getting one of these minis and putting Ubuntu on it. I would get the 10.1 inch display option if I do and was wondering if anyone knows how Ubuntu works with the 1024x576 resolution. Does it just work or do I need to hack x.org?

Thanks

---

### Post by ajkenney on 2009-03-28
> **Jonothewright said:**
> I am also thinking of getting one of these minis and putting Ubuntu on it. I would get the 10.1 inch display option if I do and was wondering if anyone knows how Ubuntu works with the 1024x576 resolution. Does it just work or do I need to hack x.org?

Thanks

It works just fine on mine.  Ubuntu detected everything as it should be and set itself up.  Only difference I did was to move the bottom menu bar to the left side of the screen.  This gives you a little bit more real estate when working on documents and such.

Cheers!

---

### Post by Ubuntiac on 2009-03-30
> **bigbrovar said:**
> the only problem am having with it is sound

This seems to be a bug with the included version of ALSA as a couple of people have reported getting it working by upgrading such as Gohai at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/"). You might want to subscribe and try the PPA in the comments of the bug report to see if the newer ALSA helps your problem.

---

### Post by bigbrovar on 2009-03-30
@Ubuntiac Thanks mate but am downloaded and installed the mie interface already which not only has a very cool interface... but also worked out of the box on the hp mini.. everything worked without having to tweek plus a faster bootup .. so i guess i would be sticking to it for now.

---

### Post by stuarto on 2009-04-07
> **skibrianski said:**
> 
So my current theory is that this is a software thing, and there is some info on the hard drive that the machine is set to use. I plan on going to the store and testing this tomorrow. If it's not some sort of magic recovery routine, I have to suspect that HP has a serious problem on its hands and didn't test what happens when the wifi/BT chip is removed from power, which would bode quite poorly for people taking netbooks on trips and running out of juice, etc.

skibrianski, I'm having much the same problem as you. After several blissful months with Intrepid on my Mini 1000TU I tried out MIE to fix the infernal microphone skype problem, poleaxed the mbr, and once that had been fixed, the orange light of death appeared, glowing angrily at me. I'm thinking an USB wireless adapter might be the way forward (I'm travelling for a few weeks in couple of days).

Interestingly, the blue light does come on past BIOS, and then abruptly switches off around the time the kernel is loaded, which gives me some hope that the problem is OS-based. But given I am reverted to Intrepid with this problem, when everything was fine before with the same distro makes me think there might be hardware to blame.

That the machine can boot at all feels like victory at this stage.


Stuart

---

### Post by sneakers563 on 2009-04-08
> **swlaird said:**
> 
Touch pad - Works great (now two finger gestures that I've found) but I use a laptop mouse and I can disable the touchpad whild typing.


How did you get two finger gestures enabled?  I can't seem to get them to work (Intrepid on a mini 1000).

---

### Post by skibrianski on 2009-04-23
> **stuarto said:**
> skibrianski, I'm having much the same problem as you. After several blissful months with Intrepid on my Mini 1000TU I tried out MIE to fix the infernal microphone skype problem, poleaxed the mbr, and once that had been fixed, the orange light of death appeared, glowing angrily at me. I'm thinking an USB wireless adapter might be the way forward (I'm travelling for a few weeks in couple of days).

Interestingly, the blue light does come on past BIOS, and then abruptly switches off around the time the kernel is loaded, which gives me some hope that the problem is OS-based. But given I am reverted to Intrepid with this problem, when everything was fine before with the same distro makes me think there might be hardware to blame.

That the machine can boot at all feels like victory at this stage.


Stuart

Stuart, I haven't re-experienced the problem since my initial frustrations. I did a reinstall in the meantime, and one of the things I did is make sure there are 16MB of free space before my boot partition. Since (I believe) something was overwriting grub in the first few sectors of the hard disk with a "standard" DOS/windows MBR (which just skips to the boot code in the active partition), this seems to have done the trick for me. What that has to do with the wireless/bluetooth, I have no idea, but it seems to have worked for me... suggest you try the same -- perhaps you could get away with gparted+grub-install if you don't have time for a full install? Good luck!

---

### Post by Souness on 2009-04-23
Hey guys!!! I've been messing around with Windows 7 so I haven't had Ubuntu on the machine for a while. After seeing 9.04 was out, I just had to jump back in. So far everything looks to be working except sound. I get an error when I try to test out HDA Intel (Alsa) so hopefully an update comes around soon for that. Otherwise function keys, touchpad, bluetooth, wireless, camera all seem to be working. Haven't tried mic yet though.

---

### Post by Souness on 2009-04-23
Just tried using headphones and that seems to work. So it just looks like speaker output is fubared

---

### Post by wilwired on 2009-04-24
First time post, new to the netbook scene. As I know linux at an intermediate level, I'm taking this chance to install it on my netbook to use it on a more regular basis to advance my skills. With that, I have the HP Mini 1030nr and absolutely love it.

I made a flash drive installer, went super smooth and was up and running in no time at all. I then ran into the seemlingly only issue 9.04 seems to have with the 1030nr model, sound via the netbooks speakers. I googled the issue and tried a few things with no luck just yet. I then ran into this on the bug site...
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/25"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/comments/25[/URL]

I will not have a chance to try it till tonight buit I'm curious if anybody has yet? I'm still quite new so those step by step instructions help :)

Any thoughts?

*Update:* Working perfectly now, the above method does indeed work.

---

### Post by mozillar on 2009-04-25
Hi, I posted a workaround that may help [here]("http://ubuntuforums.org/showthread.php?p=7139493").

---

### Post by bigbrovar on 2009-04-25
guys i have a problem with my compaq mini 700 which is essentially the hp mini 1000 with a different name, i am running ubuntu 9,04 netbook remix edition. i have been able to fix most of the problems i had with it safe for the system kernel panics when the lid is closed for a long time. can anyone confirm this or is it just me? i set it not to do anything when the lid is closed from the powermanager tool

---

### Post by mozillar on 2009-04-25
I'd be happy to try to confirm on my HP mini. Couple questions first:

- How long does lid have to be closed before kernel panic occurs?
- Is your Gnome power preference set to "Do nothing" or "Blank screen" on closed lid?

---

### Post by bigbrovar on 2009-04-26
> 

- How long does lid have to be closed before kernel panic occurs?
like 3min i havent really timed it, but it doesnt happen when if i just close and open the lid immediately 

> - Is your Gnome power preference set to "Do nothing" or "Blank screen" on closed lid? my power preference is set to Do nothing

what gives?

---

### Post by mozillar on 2009-04-26
I tried a couple times to reproduce your issue, but no luck.

Is there anything of interest in the logs?
Especially in kern.log, messages, etc at the timestamp the issue occurs.

These can easily be viewed via System..Administration..Log File Viewer

---

### Post by bigbrovar on 2009-04-26
>  mozillar  	
Re: Installing on HP Mini 1000
I tried a couple times to reproduce your issue, but no luck.

Is there anything of interest in the logs?
Especially in kern.log, messages, etc at the timestamp the issue occurs.

These can easily be viewed via System..Administration..Log File Viewer 
Thanks mate seem to happen when the netbook is on battery, but i have changed my Power Preference when i close the lid from do nothing to leave blank and there has been no more panic since. Thanks for following me up on this really appreciate :)

---

### Post by Downtuned on 2009-04-28
> **kaffaman said:**
> Hey, guys. I too run Ubuntu 8.10 on HP mini 1000 (STAC92xx audio). Instead of running usual install, i chose alternate CD (command line system), then installed Xorg, wmii and so on. Problem == sound. 
 
When tying to play music / test speakers  i get no errors, but so sound either. 

Yeah, i tweaked/searched a lot ;0)


Thanks for your help!
Did you ever get your sound working?, I installed ubuntu 9.04 last night on my hp mini 1035NR and everything works perfectly except the sound, it seems I get no sound output :/ on the volume control, I'm a total noob to linux but I love ubuntu so far and it's perfect for my needs, so if I could get this issue resolved it would be awesome, anyone knows a fix?

---

### Post by mozillar on 2009-04-28
Yep, I posted a workaround that will help [here]("http://ubuntuforums.org/showthread.php?p=7139493").

To implement, you will need to be comfortable with using Synaptic & an editor as root.

---

### Post by bigbrovar on 2009-05-06
am having flaky performance with networking on my compaq mini 700 (which is just the hp mini 1000 with another name) while both wireless and ethernet work out of the box. i have noticed that i cant easily switch from wireless to wired connection without having to restart the system. every attempt to bring up the wired interface which is seen as eth0 fails

```
ifconfig eth0
eth0: error fetching interface information: Device not found

```
```

sudo ifup eth0
Ignoring unknown interface eth0=eth0.

```

restarting networking, udev, all doesnt work.. i would have to reboot the machine before the ethernet interface start working .. anybody experience this? am thinking of switching to wicd if that would solve the problem or is this a known problem with a work around?

---

### Post by Saghaulor on 2009-05-06
> **bigbrovar said:**
> am having flaky performance with networking on my compaq mini 700 (which is just the hp mini 1000 with another name) while both wireless and ethernet work out of the box. i have noticed that i cant easily switch from wireless to wired connection without having to restart the system. every attempt to bring up the wired interface which is seen as eth0 fails

```
ifconfig eth0
eth0: error fetching interface information: Device not found

```
```

sudo ifup eth0
Ignoring unknown interface eth0=eth0.

```

restarting networking, udev, all doesnt work.. i would have to reboot the machine before the ethernet interface start working .. anybody experience this? am thinking of switching to wicd if that would solve the problem or is this a known problem with a work around?

Are you sure the interface is named "eth0"? I've had it happen where it was called that, and then renamed to eth1. So I'm ifconfig up/down'n an interface that isn't even there anymore.

Did you just "ifconfig" to see what interfaces there are?

---

### Post by rjackson1969 on 2009-05-06
I have an HP mini 1035. Recently upgraded from xubuntu 8.10 to xubuntu 9.04. Just did a partial upgrade that Ubuntu released for this this morning. WHAMO... It doesn't see my wireless anymore. 9.04 has been a nightmare thus far starting with blacked out video issues after upgrade, then doing a fresh install to around that which gave me no sound and now a partial upgrade that destroyed my wireless internet connection. What gives?

I'm new to linux and really want to make a go of this and 8.10 worked great but is this something I should expect each time my OS advises me to upgrade to the latest greatest?

---

### Post by Saghaulor on 2009-05-06
> **rjackson1969 said:**
> I have an HP mini 1035. Recently upgraded from xubuntu 8.10 to xubuntu 9.04. Just did a partial upgrade that Ubuntu released for this this morning. WHAMO... It doesn't see my wireless anymore. 9.04 has been a nightmare thus far starting with blacked out video issues after upgrade, then doing a fresh install to around that which gave me no sound and now a partial upgrade that destroyed my wireless internet connection. What gives?

I'm new to linux and really want to make a go of this and 8.10 worked great but is this something I should expect each time my OS advises me to upgrade to the latest greatest?

I did a clean install with 9.04 UNR, everything seems to be working fine. Perhaps it was the upgrade that fritzd your settings.

---

### Post by rjackson1969 on 2009-05-06
Yeah, I'm toiling in anger right now but have pretty much resided to convincing myself that I'm going to be doing yet another fresh install for the next few hours.

---

### Post by Saghaulor on 2009-05-06
> **rjackson1969 said:**
> Yeah, I'm toiling in anger right now but have pretty much resided to convincing myself that I'm going to be doing yet another fresh install for the next few hours.

I prefer fresh installs for that very reason. That and this release offers ext4, which seems to add much needed speed to the boot process.

I just copy my data to a backup partition, and whamo, start from scratch. Less headaches I think. It seems like more work, but then again, look at what you're going through now.

Less work to do it right the first time. 

I never upgraded Windows either. Always did a fresh install. To much to worry about in an upgrade.

---

### Post by rjackson1969 on 2009-05-06
> **Saghaulor said:**
> I prefer fresh installs for that very reason. That and this release offers ext4, which seems to add much needed speed to the boot process.

I just copy my data to a backup partition, and whamo, start from scratch. Less headaches I think. It seems like more work, but then again, look at what you're going through now.

Less work to do it right the first time. 

I never upgraded Windows either. Always did a fresh install. To much to worry about in an upgrade.

Very true. But then again, Windows may upgrade in 4 years vs. Unbuntu's every 6 months. lol

---

### Post by Saghaulor on 2009-05-06
> **rjackson1969 said:**
> Very true. But then again, Windows may upgrade in 4 years vs. Unbuntu's every 6 months. lol

Yeah, there is that. You could stick with and LTS release, unless you want the latest and greatest.

I try not to change versions unless there is significant reason to. Ext4 and a streamlined boot is a very good reason for me.

---

### Post by spacepluk on 2009-05-06
> **bigbrovar said:**
> am having flaky performance with networking on my compaq mini 700 (which is just the hp mini 1000 with another name) while both wireless and ethernet work out of the box. i have noticed that i cant easily switch from wireless to wired connection without having to restart the system. every attempt to bring up the wired interface which is seen as eth0 fails

```
ifconfig eth0
eth0: error fetching interface information: Device not found

```
```

sudo ifup eth0
Ignoring unknown interface eth0=eth0.

```

restarting networking, udev, all doesnt work.. i would have to reboot the machine before the ethernet interface start working .. anybody experience this? am thinking of switching to wicd if that would solve the problem or is this a known problem with a work around?


Hi bigbrovar,
To fix the ethernet problem, just add this to your kernel line:

```
acpi_os_name=Linux
```

---

### Post by bigbrovar on 2009-05-07
> **Saghaulor said:**
> Are you sure the interface is named "eth0"? I've had it happen where it was called that, and then renamed to eth1. So I'm ifconfig up/down'n an interface that isn't even there anymore.

Did you just "ifconfig" to see what interfaces there are?
actually the udev sees the wireless interface as eth1 instead of wlan0 and the Ethernet interface is seen as eth0. i will try changing the udev rules to see if that will help. 

 
> Hi bigbrovar,
To fix the Ethernet problem, just add this to your kernel line:

Code:




acpi_os_name=Linux



Thanks mate .. that seem to do the trick. i rebooted and am about to disconnect from the wired interface and connect back without having to reboot. you dont know how much of a pain the problem was.. i owe you a beer ( or your favourite beverage :) )

edit Think i spoke too soon. adding the kernel line sure improves things abit. but i still have to start the system with the network cable plugged in for ethernet to work. if i started with system with just wireless. there is no way of getting it to work with wired connection till i reboot. however once wired connection is up. i can switch disable it and use wireless and switch back without any foss which wasnt the case before. so a little progress there ..

---

### Post by rjackson1969 on 2009-05-10
> **Saghaulor said:**
> Yeah, there is that. You could stick with and LTS release, unless you want the latest and greatest.

I try not to change versions unless there is significant reason to. Ext4 and a streamlined boot is a very good reason for me.

The reinstall anew went alright. Still no sound but that seems to be the only issue for me now.

---

### Post by Saghaulor on 2009-05-11
> **rjackson1969 said:**
> The reinstall anew went alright. Still no sound but that seems to be the only issue for me now.

I've noticed the sound issue as well. I'm still trying to figure it out. It seems to recognize the audio chipset, but it isn't playing well with it.

---

### Post by termleech on 2009-05-11
[http://www.codealpha.net/193/jaunty-getting-the-sound-working-on-the-hp-mini-1000-or-1120nr/](http://www.codealpha.net/193/jaunty-getting-the-sound-working-on-the-hp-mini-1000-or-1120nr/)

That should get your sound working in Jaunty.  I've used it on both the kernel that came with jaunty and the new -12 kernel and it works great.

---

### Post by Harman Smith on 2009-05-19
I'm having a ridiculous time getting the internal microphone to work on my HP Mini 1120 NR. I just order and received it over the weekend, it is the quick-ship 10.1 inch configuration. I installed Ubuntu Netbook Remix of 9.04. ALSA is updated to 1.0.19 to get the speakers to work. Still the internal mic is unresponsive. I have followed every guide that this forum thread links to an then some. Especially the following:

> **yogipsu said:**
> So, I figured out the mic problem.

First, you need to do the following.

```
sudo nano -w /etc/modprobe.d/alsa-base

Add the following:

options snd-hda-intel model=ref

... then reboot.
```

Second, under System->Preferences->Sound, make sure Capture is set to ALSA.

Third, go into Volume Control. Edit its preferences. Make sure you can change the following: (1) IEC958, (2) IEC958 Default PCM, and (3) Input Source [the first one].  Make sure the IEC958 and IEC958 Default PCM boxes are checked, and change the first Input Source to Line.

Then open up Sound Recorder and see if it works!

I tried to follow that post many times, but it simply caused my speakers to stop working. Even if it is making my mic work, which I'm not sure of, it breaks the speakers and is unacceptable.

If anyone has gotten 9.04 to work, I would appreciate any advice on the matter. I'm going abroad for a couple weeks on Sunday and would like to have everything working by then. I've used Ubuntu before, but honestly not in years(OS X since then), I wasn't a power user either. That said, I'm not afraid to use sudo or anything in the terminal, I'll do anything to get this to work as long as it doesn't break another area.

Thanks for any help in advance.

PS: I don't know how to do it, but if i could get my hands on the driver version of the mic for HP's MIE edition of Ubuntu, would that work? Or is that just some ALSA version?

---

### Post by Harman Smith on 2009-05-20
Bump and Update.

After runnning the system testing application, this is the information displayed in the .xml file about my audio capture device: > STAC92xx **Analog ALSA Capture Device**
**Property**	Value
**info.category**	              alsa
**info.subsystem**	              sound
**info.product**	              STAC92xx Analog ALSA Capture Device
**info.parent**	              /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
**info.capabilities**	      alsa access_control
**info.udi**	              /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0
**info.callouts.add**	     hal-acl-tool --add-device
**info.callouts.remove**	        hal-acl-tool --remove-device
**linux.device_file**	        /dev/snd/pcmC0D0c
**linux.hotplug_type**	        2
**linux.subsystem**	                sound
**linux.sysfs_path**	        /sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c[B]
access_control.type[/B]	        sound
**access_control.file**	        /dev/snd/pcmC0D0c
**alsa.device_file**	        /dev/snd/pcmC0D0c
**alsa.originating_device**	        /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
**alsa.card_id**	                HDA Intel
**alsa.pcm_class**	                generic
**alsa.device**	                0[B]
alsa.type[/B]	                capture
**alsa.card**	                0
**alsa.device_id**	                STAC92xx Analog 

Still looking for solutions.

---

### Post by eddieroger on 2009-06-03
Just posting to say thanks for this thread and to subscribe to updates. This certainly wasn't the easiest install I've done, but not the hardest, either. Thanks for all the research and stuff!

---

### Post by skibrianski on 2009-07-14
Anyone have any ideas on how to apply the bios upgrade on linux? HP sent me an email that I need to upgrade, but on the wizard it sends me to the only available bios firmware upgrades are for windows, even when I select linux or HP MI edition as my OS. The one time I don't backup windows before installing my os, arg...

Surely there is a better way to install this then to send for the windows restore CD, and then run the firmware updater after a full re-install of windows and restore my linux data? Any ideas? Thanks!

---

### Post by Saghaulor on 2009-07-15
It unlikely that you can install the bios update via Linux. Perhaps in the future as support increases OEM's like HP will provide support for such.

You can try running the update through WINE, but I'm guessing it will not work.

Also, you could try running it through a virtual machine.

But, I worry that this is legit. I  have never heard of an OEM emailing bios updates.

You should got to the OEM site and verify that there is indeed a bios update for your computer.

---

### Post by skibrianski on 2009-07-22
I'm sure it's legit. When I first bought it I had a problem and called up, during which time I gave them an email address. What they emailed me was a link to the HP site that said there are important upgrades available. Something to do with the battery. The HP site had a variety of download options, including ones that appeared to be for linux (but were windows executables). I guess I'll just wait on the windows CD... Cheers

---

### Post by PrivatePickle on 2009-07-22
If you extract the file it contains two other files, biosflash.img and BiosUpdate.exe.  I used Imagewriter to write biosflash.img to a flash drive then restarted and booted to the flash drive.  Bios updated with no problems so far.

---

### Post by kle on 2009-07-25
Hi
I am new to this very nice thread, which I have read. But I did not find a comprehensible reply to whoever it was who wrote that he was unable to dual boot because the live CD did not give the option to resize the windows partition. Admittedly, somebody mentioned running chdsk from windows, but I did not get it. Could somebody please walk me through the steps to take.

---

### Post by kle on 2009-07-25
> **kle said:**
> Hi
I am new to this very nice thread, which I have read. But I did not find a comprehensible reply to whoever it was who wrote that he was unable to dual boot because the live CD did not give the option to resize the windows partition. Admittedly, somebody mentioned running chdsk from windows, but I did not get it. Could somebody please walk me through the steps to take.

Sorry guys and gals,for troubling you. I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1207776](http://ubuntuforums.org/showthread.php?t=1207776)

I am quoting this guy (thanks, AeroRG!), because what he wrote should be published in big letters all over the place:

"You need to boot into windows, go to start>run and type cmd
then type "chkdsk c: /f" withoutquotes, that's assuming the hdd you want to fix is the C drive.
It will say you need to reboot, type y and then hit enter.
The next time you boot windows the process will begin, and depending on how much stuff you have in you hdd and the speed of your computer, of course, is the time it will take to fix the problem."

That's it. And then, when windows started again, I chose "turn off" and "restart", and at restart of PC, F9 for boot options. And this time around, the live CD gave me all the usual resize options for partitioning. 

Now my little HP mini is copying my beloved Kubuntu KDE 3.5 8.04, and I am anxiously wondering whether I will get sound, etc. 

This all goes to show that some of us are actually more at home in (k)ubuntu than in Windows :-))

---

### Post by dbuurman on 2009-09-04
Guys, fyi:

After dist-upgrading yesterday to a new kernel i got my sound back! :) If anyone's interested, i could have a look at the version of alsa & kernel i'm running now.

---

