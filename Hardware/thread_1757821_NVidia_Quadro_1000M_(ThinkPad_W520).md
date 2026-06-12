---
title: "NVidia Quadro 1000M (ThinkPad W520)"
date: 2011-05-13
forum: Hardware
---

### Post by breenmachine on 2011-05-13
I've been trying for the last couple days to get the NVidia drivers working on this new laptop with no luck. Originally when I tried to enable the proprietary drivers through the GUI, it said it was available but not activated or something. The strangest thing is, when I boot from USB, I get a Unity interface working 100%, I'm assuming this means it is using the proper drivers since I can't get Unity after I install...

I started by running ```
sudo nvidia-xconfig
``` to get an X11 config file that made use of the drivers. Unfortunately, when trying to startx I would then get an error complaining that the nvidia kernel module couldn't be loaded.

I did ```
locate nvidia.ko
``` to find the location of the kernel module, it was at ```
/var/lib/dkms/nvidia-current/2.70.41.06/build/nvidia.ko
``` I then created a symbolic link in the appropriate modules directory ```
ln -s /var/lib/dkms/nvidia-current/2.70.41.06/build/nvidia.ko /lib/modules/2.6.38-8-generic/kernel/drivers/video/nvidia/nvidia.ko
``` and finally ran ```
depmod -a
``` so that the module could be loaded. X was now loading the module but gave the error "(EE) No devices detected" so in the Device section of xorg.conf I added the line ```
BusId "PCI:1:0:0"
```.

Now I'm at the point where the kernel module is being loaded but it still won't work. I get the following 
```

(--) NVIDIA(0): Connected display device(s) on Quadro 1000M at PCI:1:0:0
(--) NVIDIA(0): none
(EE) NVIDIA(0): No display devices found for this X screen
(EE) Screen(s) found, but none have a usable configuration

```

I followed the advice in this thread [http://ubuntuforums.org/showthread.php?p=10809006&posted=1#post10809006](http://ubuntuforums.org/showthread.php?p=10809006&posted=1#post10809006) and it allows X to start with no errors, I even get the login sound, but the screen is still completely black.

Does anyone have any advice?

---

### Post by elmar555 on 2011-05-14
I got the exact same laptop (i7 2820, nvidia quadro 1000M) as you and the same problems. Installed Ubuntu for the first time... unity wouldn't start saying the Nvidia driver is installed but not activated (played around with settings and f***** it up beyond repair). Reinstalled Ubuntu and magically unity started working. 
The only problem is that it crashes quite a bit. Hibernate or suspend crashes the system.. to point where you have to turn it on and off (not sure if it's video card related). Half of the time when scrolling down websites the top dashboard gets printed in the middle of the screen.

Think the drivers are a work in progress... painful.

---

### Post by breenmachine on 2011-05-14
Well that's pretty unfortunate. I tried a re-install with no success. I'm going to download the alternate installation media and try again I guess.

I'll post back with any progress. I'm pretty much out of ideas, I've tried quite a few things and it's to the point where I'm not even getting any error messages to help with debugging, just a black screen.

---

### Post by breenmachine on 2011-05-14
Just an update, if I remove the lines pertaining to what was recommended in [http://ubuntuforums.org/showthread.php?p=10809006&posted=1#post10809006](http://ubuntuforums.org/showthread.php?p=10809006&posted=1#post10809006) then reboot with an external monitor attached, everything seems to work fine with the proprietary NVidia drivers.

This seems to suggest that the NVidia drivers are having a hard time with my display, but using the EDID isn't working as a solution. Not sure what else to do.

---

### Post by breenmachine on 2011-05-14
The source of the problem was with NVidia Optimus. Had to go to the BIOS and disable Optimus completely and set the card to run always in Discrete mode. The OS detection in Optimus doesn't seem to work, it wasn't until I completely disabled it that things started working. Hopefully battery life doesn't suffer too much.

Here's a quick tutorial of what I did to get a fresh install working after this discovery and only using Ubuntu packages to do so (I hate installing things from outside the package manager).

1) Disable Optimus in the BIOS, set the card to run in Discrete mode

2) Install Ubuntu

4) Activate the NVidia proprietary driver under "Additional Drivers"

5) Reboot

6) Run nvidia-xconfig.

7) Edit /etc/X11/xorg.conf, add the following to the "Device" section:
```

BusId "PCI:1:0:0"

```

8) Blacklist the nouveau driver by adding the following to /etc/modprobe.d/blacklist.conf
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```

9) Make the nvidia kernel driver loadable by using a symbolic link as follows:
```

sudo ln -s /var/lib/dkms/nvidia-current/2.70.41.06/build/nvidia.ko /lib/modules/2.6.38-8-generic/kernel/drivers/video/nvidia/nvidia.ko

sudo depmod -aq

```

10) Reboot!

Now it should be working. Unfortunately the ubuntu "additional drivers" GUI will still report the driver as "Available but not in use" this is however false. You'll know you're using the right driver because a big NVidia logo flashes on the screen just before login (and nvidia-settings is fully functional).

Hope this helps my fellow W520 users, now I can finally enjoy my new computer.

---

### Post by BriceHulse on 2011-05-14
Thank you so much for this information. Do you think that this would work the same way for the 2000M also?

---

### Post by breenmachine on 2011-05-15
I think it should, especially if it is NVidia Optimus that is the problem. Let me know how it goes for you, I'll check back on this thread and try and help you out if you get stuck.

---

### Post by ajay_vishvanathan on 2011-05-17
can someone please make this simple enough for a layman to understand? im a newbie to linux help..

---

### Post by Willendorfer on 2011-05-18
I have a new Thinkpad W520 with an Nvidia Quadro 2000 graphics card.  I am an Ubuntu newby, migrating from Mac.  I went through all the steps Breenmachine recommends, to the letter.  When I reboot, I don't get to the desktop: instead, it goes to a black screen with a bunch of "*Starting ..." and "*Stopping ..." messages, and just hangs.  

According to the Ubuntu website, Lenovo is supposed to have a special Ubuntu distribution iso that actually works on the Thinkpad W520.  Has nobody tried this?

---

### Post by breenmachine on 2011-05-18
When you get the black screen, press ctrl-alt-f2, that should present you with a prompt to log in. Log in and type:
```
cat /var/log/Xorg.0.log
```

Post the output here. It sounds like the kernel module still isn't getting loaded for you. Probably because something went wrong at this step:

```

sudo ln -s /var/lib/dkms/nvidia-current/2.70.41.06/build/nvidia.ko /lib/modules/2.6.38-8-generic/kernel/drivers/video/nvidia/nvidia.ko

sudo depmod -aq

```

---

### Post by Willendorfer on 2011-05-24
I am able to run Ubuntu 11.04 (in classic desktop) without the nvidia graphics driver.  I'm reluctant to try something that will break the OS and force me to reinstall everything.  If you can give me some instructions that are guaranteed to work, or at least are recoverable from, then I will try it.

---

### Post by malupel on 2011-05-28
i just installed Ubuntu 11.04 on my W520 without problems. everything works fine, without any further configuration. (i just have  some strange problems with usb/esata and usb3 hdd's, sometimess there are not recognized automaticly. i did not figured out yet.) 

I did it the following way:

- Disable nvidia graphics cards in bios, set display to integrated graphic.
- install ubuntu, install all updates with the updatemanager. 
- now set the display to discrete graphic in the bios and start ubuntu. this  works for me.
- now start the additional drivers tool (system/administration/additional drivers) and add the recommended nvidia driver.
- restart ubuntu and be happy

---

### Post by bro on 2011-05-28
To safe battery I usually choose integrated in the bios. However, you might be able to (partly) solf this problem with bumblebee. Bumblebee is a work in progress to support Optimus for linux. 

So far I got it to install fine, but I can't get it to shut down the nvidia card completely when it isn't using it, so it is still draining the battery. 

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

---

### Post by apetrynet on 2011-06-03
> **breenmachine said:**
> The source of the problem was with NVidia Optimus. Had to go to the BIOS and disable Optimus completely and set the card to run always in Discrete mode. The OS detection in Optimus doesn't seem to work, it wasn't until I completely disabled it that things started working. Hopefully battery life doesn't suffer too much.

Here's a quick tutorial of what I did to get a fresh install working after this discovery and only using Ubuntu packages to do so (I hate installing things from outside the package manager).

1) Disable Optimus in the BIOS, set the card to run in Discrete mode

2) Install Ubuntu

4) Activate the NVidia proprietary driver under "Additional Drivers"

5) Reboot

6) Run nvidia-xconfig.

7) Edit /etc/X11/xorg.conf, add the following to the "Device" section:
```

BusId "PCI:1:0:0"

```8) Blacklist the nouveau driver by adding the following to /etc/modprobe.d/blacklist.conf
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```9) Make the nvidia kernel driver loadable by using a symbolic link as follows:
```

sudo ln -s /var/lib/dkms/nvidia-current/2.70.41.06/build/nvidia.ko /lib/modules/2.6.38-8-generic/kernel/drivers/video/nvidia/nvidia.ko

sudo depmod -aq

```10) Reboot!

Now it should be working. Unfortunately the ubuntu "additional drivers" GUI will still report the driver as "Available but not in use" this is however false. You'll know you're using the right driver because a big NVidia logo flashes on the screen just before login (and nvidia-settings is fully functional).

Hope this helps my fellow W520 users, now I can finally enjoy my new computer.

Hi!

Thanks for the tutorial.
I had a problem with playing flash video in full screen after following it though. I solved this by commenting out the 
```
 blacklist nvidiafb 
```Does anyone have problems with or any idea of why fading to "authorising dialogues" (gksudo) is choppy?

The full screen video is still choppy. I thought it worked this morning, but it's still choppy when I tested it again now. 
Anyone have the same problem?

OK!! This time I think I solved it.. Please excuse my noobness.
I removed the symlink and the playback worked fine.


Thanks again,
-Daniel

---

### Post by da7oom on 2011-06-03
> **apetrynet said:**
> Hi!

Thanks for the tutorial.
I had a problem with playing flash video in full screen after following it though. I solved this by commenting out the 
```
 blacklist nvidiafb 
```Does anyone have problems with or any idea of why fading to "authorising dialogues" (gksudo) is choppy?

The full screen video is still choppy. I thought it worked this morning, but it's still choppy when I tested it again now. 
Anyone have the same problem?

OK!! This time I think I solved it.. Please excuse my noobness.
I removed the symlink and the playback worked fine.


Thanks again,
-Daniel

do u recommended me to go for w520 ?

is this mean now ubuntu working fine for you ?

---

### Post by apetrynet on 2011-06-04
Hey!

It works fine for me now. There is a slight lag sometimes while the GPU ramps up to full throttle. You can force it to always be at full, but that drains the battery. Please note that I've only had this machine for a week so I haven't tested everything yet.
I like the machine. It feels strudy and has two wonderful BIOS fetures which helped me go for the w520. You can wsap the Fn and Ctrl keys on the left side of the keyboard, and you can switch off the optimus system.

I had partial success with the bumblebee scripts, but the OpenGl performance was way slower then with Descrete only setup.

Good luck with your choise,
-Daniel

---

### Post by gilesp on 2011-06-06
Daniel (apetrynet), 

are you running 64 bit Ubuntu?  If so, are you using the nVidia binary driver?  I am running 64 bit 11.04 and getting lockups when I unplug the AC adapter, and when I resume from suspend it only succeeds maybe 1/2 the time. 

In contrast, when I tried the 32 bit version everything worked fine.  Also, when I had the display set to 'integrated' in the BIOS, everything worked fine (but I couldn't do multi-head). 

If you are running x86_64 and the above is working fine for you, I'm intensely curious what version of the driver you're using, what your xorg.conf settings are, and anything else special around your configuration that might be relevant (using the standard .deb packaged driver version, or one downloaded from nVidia's site? etc).  I'm trying to figure out if my w520 is just a dud, or if others have similar issues to my own [-o<

Thanks much,

Peter

---

### Post by apetrynet on 2011-06-07
Hey Peter!

I'm running ubuntu 11.04 64bit and the latest drivers form the repository. BIOS set to descrete only.
I've had no trouble with the suspending or hibernating this far. I have also had success with pluging/unplugging the AC.

BUT....

I'm sad to say that my problem with choppy full screen playback in flash turned up again. I tried setting the Nvidia power settings to max performance with no luck. I don't understand why this bug comes and goes, but I haven't had the time to dig into it yet. Perhaps it has to do with suspending? 

When it comes to OpenGL performance it seems to work fine. It runs blender and glxgears without problems.
Mplayer with fullHD also works, but it sometimes says that my machine is too slow so I guess theres still a few hickups.
I don't have the machine with me now, but can post the xorg.conf later.

It seems that my problems are all 2D related.. Don't know why there should be a difference though..

Please post success stories ;)

-Daniel

---

### Post by rationalstorm on 2011-06-11
I had trouble booting my W520 with the Nvidia module enabled. Things worked fine with the Intel card activated, but as soon as the Nvidia card was used the system would freeze when booting. Sometimes, it would boot, but most of the time it wouldn't. There is a separate issue that crashes the system when ACPI calls are made. This happens when you use the brightness controls, but also seems to happen (in some configurations) during boot when GDM  ist started. Adding **acpi=off** in grub as a workaround until this is fixed lets me boot reliably.

---

### Post by VValdo on 2011-06-12
Just got my machine.  I started up w/the default bios settings and got some notice about not being able to run unity.  So it ran the old interface... sans any kind of acceleration (compiz-- dropshadows, animations etc)

I went back and turned on discrete in the bios, rebooted to the nvidia logo and everything was good-- until I realized I couldn't change the brightness or the volume.

So I tried a few boots and killing xorg.conf and got it back to intel, which is fine for now.  Except I kinda want some compiz goodness.

(ha- I just realized I'm running w/o any xorg.conf AT ALL... must be using defaults.)  Can someone who's got the integrated gpu working w/that stuff be so good as to post:

BIOS settings
xorg.conf

Or, if someone knows how to get nvidia's driver going w/o these volume/brightness headaches, I'd appreciate the above as well..

thanks!

W

---

### Post by sentraser165 on 2011-06-12
> **VValdo said:**
>  (ha- I just realized I'm running w/o any xorg.conf AT ALL... must be using defaults.)  Can someone who's got the integrated gpu working w/that stuff be so good as to post:

BIOS settings
xorg.conf

Or, if someone knows how to get nvidia's driver going w/o these volume/brightness headaches, I'd appreciate the above as well..

thanks!

W

+1. Thanks!

---

### Post by VValdo on 2011-06-13
> **sentraser165 said:**
> +1. Thanks!

Heh.  I think you're going to be happy. :guitar:

Try this:

```
sudo apt-get --purge remove nvidia-current
sudo apt-get --purge remove nvidia-settings
sudo reboot
```

Discussion:

I noticed in /var/log/Xorg.0.log that GLX was failing because it was trying to load the nvidia driver still- suggesting to me that some sort of autodetect when I first installed the OS (with default BIOS) told xorg to use nvidia for GLX.  Meanwhile I'm using the intel driver... so there was a failure I guess.

SO... I figured I'd forcibly remove everything nvidia (although not nvidia-common) and see what would happen.  And now it works.  I have drop shadows and animations and everything using the integrated intel driver.

The result is that not only do I have GLX w/drop shadows and animations, but this horrendous subliminal flicker I was experiencing that made my eyes hurt is also GONE.

This will be my solution until such a time as the nvidia driver doesn't interfere with changing the volume and brightness.

Incidentally, for anyone who may be reading in the future, no xorg.conf is needed in /etc/X11 to fix this.

W

---

### Post by VValdo on 2011-06-13
Also, if you're experiencing a stuttering system, try this:

```
echo 1 > /sys/module/i915/parameters/semaphores

```
as root.  Just another [tip]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065") i found.  hopefully this will be fixed in a newer kernel...

---

### Post by apetrynet on 2011-06-15
Hey Y'all!

Anyone had the chance to check out the new binaries form NVIDIA? (275.9.7)
[http://www.nvidia.co.uk/object/linux-display-amd64-275.09.07-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-275.09.07-driver-uk.html)

I don't have a working online connection at home so I can't check if it fixed my main issues; beeing choppy fullscreen playback on websites as vimeo and youtube (after resume from suspend)

What I did to install successfully(?) breaks down to this:
1. hit Ctrl+Alt+F1
2. sudo tellinit 3
3. sudo dpgk -r nvidia-current
4. sudo chmod -x NVIDIA[TAB].bin
5. sudo ./NVIDIA[TAB].bin
6. Follow onscreen directions.

I messed up a few times forgetting to uninstall the old drivers and had some errors linking to old so's, but just continued hitting ok until it (the driver installation) finished and ran it again.

Please let me know if any of you gain some knowledge using this new driver.

-Daniel

PS! Perhaps the "owner" of this thread should remove the [SOLVED] brackets?

---

### Post by apetrynet on 2011-06-16
> **VValdo said:**
> Also, if you're experiencing a stuttering system, try this:

```
echo 1 > /sys/module/i915/parameters/semaphores

```as root.  Just another [tip]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/761065") i found.  hopefully this will be fixed in a newer kernel...

On my machine (lenovo w520.. doh) there is no /sys/module/i915/parameters/semaphores. Is this a 32bit thing?

---

### Post by VValdo on 2011-06-16
> **apetrynet said:**
> On my machine (lenovo w520.. doh) there is no /sys/module/i915/parameters/semaphores. Is this a 32bit thing?

No I have a w520 as well.. you're running 64-bit ubuntu natty?  Kernel is:

Linux laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by apetrynet on 2011-06-16
Hey!

Yes, i'm running 64bit Natty.
I don't have my machine with me now and I'm without net in my home at the moment so I can't post my uname -a

Did you create this semaphore file or is it supposed to be there? 
I'm currently using the newest NVIDIA binary (275.9.7) manually installed. Perhaps this has something to do with it?

=D

---

### Post by VValdo on 2011-06-16
It was there already... after my system crashed (?) last night (it was blank and really hot this morning) I'm looking into a newer kernel.  Trying [this one]("http://duopetalflower.blogspot.com/2011/06/custom-kernel-26391-ubuntu-amd64.html")... so far it works well/fast but no wireless so I'm looking into that.

---

### Post by apetrynet on 2011-06-17
Hey! 
Finally got internet at home again!

No improvement using the newest driver so I reverted to the nvidia-current. Still can't find the /sys/module/i915 folder or any semaphores file anywhere on my machin[FONT=monospace]e.
I have the exact same kernel as you had VValdo.
uname -a: 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Anyone else have trouble finding this file or with choppy fullscreen playback on vimeo (after suspend)??

-D
[/FONT]

---

### Post by VValdo on 2011-06-17
There's a newer kernel on apt-get.. My guess is that if you use .39 the stuttering will be fixed...

---

### Post by apetrynet on 2011-06-17
> **VValdo said:**
> There's a newer kernel on apt-get.. My guess is that if you use .39 the stuttering will be fixed...

Tried apt-get upgrade but no kernel update. How do I get a hold of this?

Thanks!

I did a quick search and found it. Works like a charm!! Thank you so much!
Followed this link: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/)

-Daniel

---

### Post by gatman3 on 2011-06-23
Has anyone been able to get the W520 to boot with the proprietary nvidia driver WITHOUT disabling ACPI (kernel parameter "acpi=off")?  If so, can you share your recipe?

I am running kernel 2.6.39-0 and nvidia driver 270.41.19 (not the latest), and the machine runs fine with acpi=off.  However, with ACPI disabled the kernel also shuts down all but one CPU core (yuck).  Maybe there's some other way around that?

---

### Post by apetrynet on 2011-06-23
> **gatman3 said:**
> Has anyone been able to get the W520 to boot with the proprietary nvidia driver WITHOUT disabling ACPI (kernel parameter "acpi=off")?  If so, can you share your recipe?

I am running kernel 2.6.39-0 and nvidia driver 270.41.19 (not the latest), and the machine runs fine with acpi=off.  However, with ACPI disabled the kernel also shuts down all but one CPU core (yuck).  Maybe there's some other way around that?

Hey!

My charming laptop running bleeding edge kernel turned out to be a dud.. again. 
Fed up with this problem I installed 10.10. This is the certified version of ubuntu for the w520 after all. What a difference! It's so much more snappy. I ran into a few hicukps, but all of them are now solved (I hope..)

First I had to fix suspend with this link: [http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html](http://jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html)

Then two finger scroll with this: [http://ubuntuforums.org/showthread.php?t=1603657](http://ubuntuforums.org/showthread.php?t=1603657)

Then the return of choppy video after suspend fixed with this: [http://ubuntuforums.org/showthread.php?t=1632254&page=2](http://ubuntuforums.org/showthread.php?t=1632254&page=2)

I know it's not the best indicator, but glxgears: 51309 frames in 5.0 seconds = 10261.796 FPS
In Natty i barely got 5k

Good luck!
-Daniel

---

### Post by gatman3 on 2011-06-23
Daniel - Thanks for the info and especially the prompt reply.  You've given me some hope.  I'll give the 10.10 release a shot plus the workarounds you cited.  Now that you mention it, I remember seeing that "ubuntu certified" listing for the W520 with 10.10.  I should have remembered that; for some reason I guess we always think the latest is the best.  Oh well, I'll post my results in a few days.  Regards - Greg

---

### Post by apetrynet on 2011-06-23
Your very welcome Greg!

I think the reason I went for Natty was the bumblebee (Optimus support on linux) project. It only ran on Natty I think. It turned out not quite doing it for me though. The image quality wasn't that great and the performance was limited. It's a great tool if you mostly run less gpu intensive stuff.

I'll continue checking the development, but am really happy with 10.10 Nvidia only setup. I still get a decent battery life.

Hope you'll enjoy your machine soon,
-Daniel

---

### Post by VValdo on 2011-06-24
I'm still sticking with 11.04 but -- and this is with Integrated Intel driver -- I'm getting lockups about once a day.

I do hope this isn't a hardware issue.  Can anyone else confirm?

natty 11.04

Linux laptop 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

xserver-xorg-video-intel 2:2.14.0-4ubuntu7.1

---

### Post by gatman3 on 2011-06-24
VValdo, I was getting occasional lockups too, maybe once per day.

However, I seem to have solved my problems today.  The magic recipe is... running 32-bit Ubuntu, plus updating the BIOS to version 1.25.  Sad, but true, the 32-bit version runs beautifully while 64-bit is a disaster.  I pretty much blew my whole day today trying out the 64-bit versions of Ubuntu 10.10 and 11.04 (again), and with no success at all.  10.10 was especially bad for me, so I'm completely baffled as to why apetrynet (Daniel) has had such good success with it.  Of course, I didn't try it after the BIOS update, so maybe he has a newer BIOS?  In any case, with 10.10 the install quietly died in the middle which I didn't realize until my first boot, then it hung the first time I booted it up, I finally got it booted and then I had 2 or 3 software update/reboot cycles, then it seemed to work OK with integrated graphics but switching to nvidia really screwed it up.  Lots of times it would boot and sit there giving me a flashing cursor forever.  Eventually I got it booted, somehow, and it ran super unbelievably slow.  I finally gave up.

Then I checked out the BIOS updates on the Lenovo web page.  Turns out my machine was several BIOS updates behind from the factory.  The newest BIOS (at the time I'm writing this) is version 1.25 released on 16-June-2011.  It's a bit hard to find on Lenovo's web page, so here's the link:

[http://support.lenovo.com/en_US/downloads/detail.page?DocID=DS018887](http://support.lenovo.com/en_US/downloads/detail.page?DocID=DS018887)

and here's the changelog:

[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj05uc.txt](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj05uc.txt)

The changelog lists several interesting items, such as these from the 1.24 update:

> - (Fix) Fixed an issue where the computer might not be booted from the hard
         disk with Linux installed if there was no active partition there.
 - (Fix) Fixed an issue where the computer with large-capacity memory installed
         might fail to resume normal operation from standby/sleep state.

(The update process is a bit terrifying, by the way.  You burn a CD with their .iso image, boot to it, then get past several terrifying warning pages about not unplugging the machine or removing the CD during the update.  Then you start the update and it just sits for like 6 or 8 minutes, occasionally hitting the CD drive, occasionally just sitting like it's hung.  Finally you get a really weird message directing you to either reboot with the CD in to complete the process or, optionally, remove the CD and start up normally.  Huh?  I left the CD in, rebooted and it briefly showed a message that it was finishing the update, then it booted up normally.  Really scary, but it worked.  Proceed at your own risk).

However, after simply updating the BIOS my 64-bit install of 11.04 still didn't work.  In fact, something about the BIOS update broke my NVidia boot altogether, and now it would just hang after logging in (I use KDE).

Then I installed Ubuntu 11.04 32-bit.  All I can say, is that everything just works.  I have had to do no hacks.  Suspend works without the hack that apetrynet cited.  The open-source Nouveau driver works.  The NVidia proprietary driver works.  Everything just works.

I'm happy now.

---

### Post by VValdo on 2011-06-25
Hmm..  That's a great tale-- thanks and congrats on getting it working.

I've got the .24 firmware and running 64-bit linux and the ONLY problem I'm having is this 1ce a day freeze.  Well, that and bluetooht always turning on when I boot but that's fixable.

I'm running integrated driver... I haven't had the freeze in > 24 hours so I'm gonna wait one kernel/driver revision ccle and see if that fixes anything...  if not... I dunno what to do...  I'm really not looking forward to having to reinstall...

---

### Post by apetrynet on 2011-06-27
Just wanted to shoot in that my BIOS version is OOooollld! 1.21 dated 03/30/2011. Even though the words "never change a winning team" repeats in my head, I can feel the tingeling sensation of wanting to upgrade my BIOS.
hmmm. I'll let you know if I do.

-D

---

### Post by gatman3 on 2011-06-27
Update from my side...  After three days running 32-bit 11.04 everything is still running great with a couple minor exceptions.  I have noticed that I am seeing the problem with stuttering video playback after suspend.  I tried the workaround at the link that you cited, but it didn't work for me.  Not that big of a deal to me, but I gotta strive for perfection.

The only other quirk I've seen is that when I'm running the proprietary nvidia graphics with dual monitors, the KDE desktop effects (compiz?) get disabled whenever the monitors power down due to inactivity.  When I get some time I'll look for a workaround for that.

Otherwise it's working great.

---

### Post by apetrynet on 2011-06-27
> **gatman3 said:**
> Update from my side...  After three days running 32-bit 11.04 everything is still running great with a couple minor exceptions.  I have noticed that I am seeing the problem with stuttering video playback after suspend.  I tried the workaround at the link that you cited, but it didn't work for me.  Not that big of a deal to me, but I gotta strive for perfection.

The only other quirk I've seen is that when I'm running the proprietary nvidia graphics with dual monitors, the KDE desktop effects (compiz?) get disabled whenever the monitors power down due to inactivity.  When I get some time I'll look for a workaround for that.

Otherwise it's working great.


Hey!

Did you make sure the script shutting down cpu's is executable?

---

### Post by gatman3 on 2011-06-27
I just got it working.  The script was executable; that wasn't the problem.  The other thread suggests that you only need to disable the odd numbered CPUs (i.e. the hyperthreaded ones).  But for some reason I need to disable all CPUs 1 through 7, not just the odd numbered ones.  Once I did that I got rid of the video stuttering after suspend.  Woo hoo!

Now I just need a fix for my compiz getting disabled in nvidia mode after my monitors power off.  I'll post if I figure that out.

Great machine.  Thanks for your help! - Greg

---

### Post by lpearce on 2011-08-17
Hello all-
I'm considering purchasing a ThinkPad W520 and would like to know if anyone has gotten the discrete graphics card with the Nvidia driver working in 64 bit linux without disabling ACPI.  If so, I'd like to know the following version numbers:
1. BIOS
2. Ubuntu
3. Kernel
4. Nvidia driver
Also, I'd like to know if it's working with problems that can be "lived with"- that is, they don't prevent the computer from operating.  (ie, not returning from suspend or hibernate, or choppy playback after suspend, etc.)
If you could help, I'd much appreciate it.  Thanks!

---

### Post by wastvedt on 2011-08-17
lpearce-
Mine is working just fine, though I haven't tested extensively. Let me know if there's a particular problem you're worried about. I haven't manually disabled any ACPI stuff. How do I know if that's running? Here's what I have:

Ubuntu 11.04 - 64 bit
W520 - Quadro 1000M, quad core
BIOS - not sure, just updated to latest version a week ago
NVidia driver - 270.41.06
Kernel - 2.6.38-8-generic

I can use either discrete or integrated graphics (not both yet). I have suspend and hibernate working just fine. Occasionally gtk-window-decorator stops running - not sure why - but I just restart it. The battery meter seems to have problems with its predictions. Overall pretty minor.

Trygve

---

### Post by Ansible on 2011-11-06
> **lpearce said:**
> Hello all-
I'm considering purchasing a ThinkPad W520 and would like to know if anyone has gotten the discrete graphics card with the Nvidia driver working in 64 bit linux without disabling ACPI.  If so, I'd like to know the following version numbers:
1. BIOS
2. Ubuntu
3. Kernel
4. Nvidia driver
Also, I'd like to know if it's working with problems that can be "lived with"- that is, they don't prevent the computer from operating.  (ie, not returning from suspend or hibernate, or choppy playback after suspend, etc.)
If you could help, I'd much appreciate it.  Thanks!

Just got 3D working today.  

1. BIOS 1.25
2. Ubuntu 11.10 64-bit
3. Kernel 3.0.0-12-generic
4. nvidia 280.13

Changed the optimus setting to discrete in the BIOS and now 3D works.  I haven't made any other changes in the BIOS.  Unity was working just fine before that, I just couldn't run any openGL programs.  My W520 has the quadro 1000m.

---

### Post by di3gopa on 2012-02-04
Using Bumblebee and it works great on my w520! -> [http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html#comment-form](http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html#comment-form)

---

### Post by VValdo on 2012-02-04
> **di3gopa said:**
> Using Bumblebee and it works great on my w520! -> [http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html#comment-form](http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html#comment-form)

The link says:

" Now you can enjoy Unity 3d, in fact Ubuntu boots right into it when it was restarted."

What about unity 3d doesn't work with intel?

---

### Post by di3gopa on 2012-02-10
> **VValdo said:**
> The link says:

" Now you can enjoy Unity 3d, in fact Ubuntu boots right into it when it was restarted."

What about unity 3d doesn't work with intel?

3D unity it is working for me with intel graphics, the problem i am having with bumblebee is that i cant use external monitors, i am thinking about switch to 32 bits + pae kernel + nvidia drivers

---

### Post by test-bot on 2012-02-11
> **Ansible said:**
> Just got 3D working today.  

1. BIOS 1.25
2. Ubuntu 11.10 64-bit
3. Kernel 3.0.0-12-generic
4. nvidia 280.13

Changed the optimus setting to discrete in the BIOS and now 3D works.  I haven't made any other changes in the BIOS.  Unity was working just fine before that, I just couldn't run any openGL programs.  My W520 has the quadro 1000m.

do mind posting how you installed 280.13? i'll try to find it later but i figure it's worth asking if it can save some time. 

Thanks!

---

### Post by Ansible on 2012-02-11
> **test-bot said:**
> do mind posting how you installed 280.13? i'll try to find it later but i figure it's worth asking if it can save some time. 

Thanks!

Sorry but I don't actually remember!  It was probably a matter of selecting the driver in the 'additional driver' utility.

---

### Post by dieter-erich on 2012-05-24
Hi guys,
I am having the same problem with the W520 graphics. I followed the procedure posted by breenmachine of May 14, 2011 but did change the bios settings only after having already installed Wubi 10.04 64bit. When I let it search for hardware drivers it does not find anything. Does anybody know whether this has to do with the 64 bit version or with the installation already present when I changed the bios settings?
Any idea of how to proceed?
Thank, D-E
 
P.S. I apologize for having opened a new thread with this some days ago. I only found out now that this problem was well known.

---

### Post by Kirk Schnable on 2012-07-30
I have also run into this problem on Xubuntu 12.04 LTS on my ThinkPad W520 with Quardo 2000M graphics.  I will keep everyone posted on any fixes I might find in my own digging...

After following the instructions provided, my computer boots into a TTY with no graphical interface loading.

Kirk

---

