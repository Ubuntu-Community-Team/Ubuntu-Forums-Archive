---
title: "Averatec 2370 / 2300 Guide"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by dragonfyre13 on 2006-11-27
[SIZE=6]Avertec 2370 and Everex StepNote ST5340T Compatability Guide[/SIZE]

Thanks to NickB, lawr_rawr, lythandrel, dragon76, and all the others who continually help people out in this thread, and with this guide.

I suppose this is just a thread to help others who get this great peice of equipment. I have most of the functionality working great, and I will update this as I get more working. I'm also including information about the laptop in here that will help others with drivers and such.

This is focused on Gutsy Gibbon, since that is what I am using, 64 bit should be covered soon, and should be about the same configuration as detailed here.

[SIZE=4]Unsolved:[/SIZE]   ](*,) 
Intermittent Wireless Issues

[SIZE=4]Works In Progress:[/SIZE]   :-k 
CPU Scaling Button (Thanks NickB) (Need to test this on Gutsy)

[SIZE=4]Completed:[/SIZE]   :cool: 
Video Card Drivers
Suspend To Disk (Hibernate)
Suspend to Ram (Suspend)
Wireless with Network Manager and Encryption (WPA and WEP)
ExpressCard Recognition
Dual Core Recgonition
Desktop Effects (Compiz, etc.)

-----------------------------------------------------------------

[SIZE=5]_Working by Default_[/SIZE]
Wireless with Network Manager and Encryption (WPA and WEP)
ExpressCard Recognition
Dual Core Recgonition
Suspend To Disk (Hibernate)
Suspend to Ram (Suspend)

[SIZE=5]_Proprietary Nvidia Drivers_[/SIZE]
This is fairly simple. Just select Restricted Drivers Manager in System->Administration, and check the box to enable these.

Reboot. (Yes, reboot. You don't have to, it's just the easiest way.)

If your resolution is borked (mine was, it sets itself to 1024x768 ) open up System->Administration->Screens And Graphics. Get quite familiar with this application. You will be in it a few times.

You will have to "Fiddle" a bit. Basically, you may have to reboot and delete your xorg.conf files from recovery mode (from the commandline: sudo rm /etc/X11/xorg.conf*) a few times to get this right. The goal is to set your settings with the LCD 1280x800 (make sure to check the widescreen option when you select the screen type) with a refresh rate of 51 khz and a resolution of 1280x800.

After you get that set, you just need to log out and back in again.

YAY! Have a cookie.

[SIZE=5]_Desktop Effects_[/SIZE]

This is enabled by default. However, to get the true functionality, you will need to install the configuration package.

```
sudo apt-get install compizconfig-settings-manager
```

Then, just execute the command:

```
ccsm
```

To change your settings.

[SIZE=5]_A Quick Aside..._[/SIZE]

First, I wanted to say that Gutsy Gibbon fixes a lot out of the box. One of the reasons that this thread was here was because the rt73 driver was so hard to install and configure. This thread at least got you off the ground on that. Now it works by default out of the box. That is a huge win. While we are still tracking down issues with wireless, I think this is a huge improvement.

Second, I haven't put this entirely through it's paces yet. I'm trying, but I always need help from people who use it on the forums, and every comment counts. Even a "This guide covers everything" to a "X feature doesn't work". I can be aware of what I need to focus on to write it into this guide.

Just a short thanks again. Most of the original information, and much of the support for this laptop was off of the Ubuntu Boards, and from the Ubuntu IRC channel. Thanks to everyone that helped, including FrodoB, Kingsqueak on IRC, and others. Also, some of the info is off the Averatec Unofficial Forums. They aren't a great resource, but still, I thought I would mention them. Sorry if I forgot you. I know I mistreated you. Have a cookie.


[SIZE=5]_Power Save Button_[/SIZE]
[SIZE=4]Thanks to NickB for this. I'm testing this now, and it's really good. Nick, have a cookie.[/SIZE]

If you want to use the "S" button to put your laptop into powersaving mode, go to the following post, and install the attached Deb file for either 64 or 32 bit versions of Ubuntu (all architectures, we think. If it doesn't work on one, just post here.) 

[http://ubuntuforums.org/showpost.php?p=1893382&postcount=21](http://ubuntuforums.org/showpost.php?p=1893382&postcount=21)
(There is a source file attached also for other Distros to port the app, or for you to compile it yourself)

Then follow the directions:

From the README:
[I]In order to use the tray icon notifier in a GNOME desktop, open
System->Preferences->Sessions, select the Startup Programs tab,
click the Add button and type powersave-trayicon into the text
entry box and click OK. The next time you start your GNOME
session the tray icon will be active.[/I]

(Got a little Techie in you? He explains a bit about why he did it this way here: [http://www.ubuntuforums.org/showpost.php?p=1868590&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1868590&postcount=12) )

Now, give a cookie to NickB. Yes, alright, you can have one too.


[SIZE=5]_An Aside to Those Using Other Distributions_[/SIZE]

Hello, and welcome. We greet you from ubuntu-land. Let me say that this is neither a crappy, or a kiddie distribution, and that I have tried all of the top 10 Distributions on DistroWatch (and many that weren't) and I keep coming back to this for various reasons, and have stuck with it for my main OS since Warty Warthog (the first release) was released. We will welcome you to decide to join, but otherwise here's some information that you will likely find useful.

The driver for wireless is RT73 from Ralink. You need that driver. It has some peculiarities but the main thing is to make sure that you have the other drivers blacklisted, and don't plan on using a graphical tool. If you do need a graphical tool, there is one hidden in this thread, that is accessible from the commandline. However, if you need NM working with it, and it doesn't, try the serialmonkey drivers, or if that fails, go to Ndiswrapper.

Suspend works better generally with an external program (there are a few), or using a Suspend2 patched kernel.

Almost always, the CVS versions of drivers have fixes for this laptop in them. The serialmonkey drivers are one instance. Try it out. If it doesn't work, you can remove it.

If you have questions, post them. I'm not an Ubuntu Nazi, and I don't think people here are. We're a good support structure for the hardware, and if you have questions about it, the thread is pretty active. So post and ask. Almost all of the solutions are distro agnostic.

---

### Post by dragonfyre13 on 2006-11-29
OK, got WEP working, and updated the above to reflect the changes.

---

### Post by dragonfyre13 on 2006-12-01
Having issues with Full Screen OpenGL? (games, etc)

It's a bug in the NVIDIA 9629 drivers. You should either roll back the drivers (that has issues with the GeForce Go 6100 card in this laptop) or you can use the next version, at the link that was so graciously provided to us below. I will be sure to keep you up to date on when these hit the repository so that you don't have to jump through these hoops.

All you have to do is run the NVIDIA-Linux-x86-1.0-9631-pkg1.run file, after killing GDM (sudo /etc/init.d/gdm stop) and removing the nvidia glx package from above (apt-get remove nvidia-glx) and you're golden.

You should restart the computer, or start gdm again. (sudo /etc/init.d/gdm start)

After the new drivers are in the repository, you just install the nvidia-glx package, and run the command above for installation, but pass a "--uninstall" command to it.

---

### Post by dragonfyre13 on 2006-12-01
Getting closer to Suspend2 integration. I have everything working on my laptop, now I'm installing a seperate Ubuntu installation to make things nice and simple for those of you who don't have days to slave over it. ^_^

---

### Post by deadlydeathcone on 2006-12-04
> **dragonfyre13 said:**
> 
[SIZE="5"]_Suspend To Disk (Hibernate)_[/SIZE]

This is partly working out of the box, but it takes forever to come back from hibernation, and doesn't have any sort of indication that it is coming back. Getting it to go faster and use a splash is a work in progress. I'm focusing on Suspend2 patched kernels to accomplish this.

I've owned an Averatec with finicky hibernation before, and the old tricks seem applicable here. "apt-get install uswsusp" enables compression and a splash indicator (or a psychedelic mess, depending upon what drivers you use), and using the /etc/default/acpi-support that I attached should get things up to speed.

As far as video goes, the bugs in the 9626 and beta drivers have all been fixed with the just-released [9631]("http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html"). Also, after using both for a while  Beryl is much less buggy and resource demanding than Compiz on this machine, although both are blazing fast even with an integrated Geforce 6100.

Anyways, thanks for the guide. For one thing, I wouldn't even have known that stable native rt73 drivers existed without it. ](*,)

---

### Post by dragonfyre13 on 2006-12-05
Wasn't it evil finding that? ^_^

If you have something working, I wouldn't switch though. The rt73 drivers are in beta status, though they are official, and can be very hard to setup if you don't follow the guide EXACTLY. 

I do prefer Beryl to Compiz also, mainly for the reasons that you stated. Thanks for the acpi file, I'll take a look next time I have a chance. I'm actually really close to getting "suspend to ram" working, mainly by majorly messing with a lot of stuff. I'm running edgy, which broke nearly all suspend to ram stuff, in all laptops from what I hear.

Either way, nice to know someone actually read it. ^_^

---

### Post by victorxg on 2006-12-07
Hello, I just want to say though I'm not a Ubuntu user, I'm a SUSE user, this thread has convinced me to get the 2370. I've been looking for a replacement for my ibook that doesn't cost too much. I have a question though, has anyone tried replacing the wifi card with a different one?

---

### Post by dragonfyre13 on 2006-12-07
> **victorxg said:**
> Hello, I just want to say though I'm not a Ubuntu user, I'm a SUSE user, this thread has convinced me to get the 2370. I've been looking for a replacement for my ibook that doesn't cost too much. I have a question though, has anyone tried replacing the wifi card with a different one?
Good to know it helped someone. Actually, you shouldn't try to replace the card with something else. It's a usb wifi card, since the laptop doesn't have a standard pci interface. It uses PCI-E instead, which is new enough (on laptops) that there aren't mini cards for it. You can pick up a Express Card for wifi, and that makes things TONS easier, but they run about 70-80 bucks. Like I said, it's a new technology.

Good to see other Distros here. Let me know if there is anything that I can do to improve my tutorial for SUSE as well. I'd like it to be fairly standard across distros.

P.S. I think SUSE has rt73 drivers already packaged for it too.

---

### Post by Joshua on 2006-12-09
Has anyone tried this with Edgy for AMD64 yet?  I can't get the wireless drivers to build.

---

### Post by NickB on 2006-12-10
I am running Edgy amd64 on this laptop.  Download the network drivers from cvs:

cvs -d:pserver:anonymous@rt2400.cvs.sourceforge.net:/cvsroot/rt2400 login
cvs -z3 -d:pserver:anonymous@66.35.250.89:/cvsroot/rt2400 co -P source

Go to the rt73 directory and make, make install.  Copy the rt73.bin file as noted above, but DO NOT create/copy the rt73sta.dat, as it will cause a kernel Oops.  You don't need it anyway.

I could not get this to work with NetworkManager; in /etc/network/interfaces, you need to have something like this:

auto rausb0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid whatever
wireless-key blahblah...

Anyway, the pre-up line is most important.  Won't work without it.

Hope that helps,
Nick

---

### Post by Joshua on 2006-12-10
NickB, what kinds of options did you use when you ran the Live CD?

---

### Post by NickB on 2006-12-10
If you want to use the "S" button to put your laptop into powersaving mode, use the following scripts:

/etc/acpi/averatec-powersave.sh```

#!/bin/sh

CPU_MAX_FREQ=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq`
CPU_MIN_FREQ=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq`

if [ "$1" = "on" ]; then
        echo $CPU_MIN_FREQ > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
else
        echo $CPU_MAX_FREQ > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
fi
```
(make sure you do a "chmod +x /etc/acpi/averatec-powersave.sh")

/etc/acpi/events/averatec-powersave-off:```

event=processor P001 00000080 00000000
action=/etc/acpi/averatec-powersave.sh off
```
/etc/acpi/events/averatec-powersave-on```

event=processor P001 00000080 00000008
action=/etc/acpi/averatec-powersave.sh on
```
The reason I'm changing the scaling_max_freq instead of scaling_governor is because this is primarily being controlled by the powernowd, which may be customized to set scaling_governor to something other than "ondemand" (e.g. performance).  Setting the maximum frequency to the CPU's minimum will ensure maximum power saving no matter what.

Hope that helps someone.

Nick

---

### Post by NickB on 2006-12-10
> **Joshua said:**
> NickB, what kinds of options did you use when you ran the Live CD?
I used a wired network with the Live CD.  The wireless drivers that come with it did not work at all for me.

EDIT: Unless you mean in general, in which case I only needed noapic.

Nick

---

### Post by Joshua on 2006-12-10
I was getting at the noapic option, and any resolution settings that might fit better for a WXGA screen.  From what I can tell there is no vga setting that would be specifically for 1280 x 800.  I booted with the noapic option (only way I could get it to work as well) and the splash screen/progress bar wasn't working properly.  So I thought maybe there would be a better way to set the resolution.

Do you know what that noapic option does?  Is it something that I would want to try and activate after installation?

Also, I assume you mean that the wireless didn't work until you installed everything and downloaded the drivers you mention in the earlier post.

---

### Post by NickB on 2006-12-10
The X server being used is probably the vesa server, and there is no 1280x800 vesa mode that I know of (I'm pretty sure WXGA is not an "official" mode).  Just use it to get everything installed.  Once you have your laptop up and running after installation, follow the instructions at the top of the thread to get the nvidia driver working.

The noapic option disables the APIC (Advanced Programmable Interrupt Controller), with which linux usually doesn't work right on laptops, and instead uses the legacy interrupt controller.

Nick

---

### Post by Joshua on 2006-12-11
[QUOTE=dragonfyre13;1814992]```
sudo apt-get install linux-headers-`uname -r`  
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

Should the line above be:
```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```

---

### Post by dragonfyre13 on 2006-12-14
> **Joshua said:**
> [QUOTE=dragonfyre13;1814992]```
sudo apt-get install linux-headers-`uname -r`  
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

Should the line above be:
```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```
Honestly I'm not sure. I know that the one I have up there works, but can anyone confirm if the Header's work also?

---

### Post by dragonfyre13 on 2006-12-14
> **Joshua said:**
> I was getting at the noapic option, and any resolution settings that might fit better for a WXGA screen.  From what I can tell there is no vga setting that would be specifically for 1280 x 800.  I booted with the noapic option (only way I could get it to work as well) and the splash screen/progress bar wasn't working properly.  So I thought maybe there would be a better way to set the resolution.

Do you know what that noapic option does?  Is it something that I would want to try and activate after installation?

Also, I assume you mean that the wireless didn't work until you installed everything and downloaded the drivers you mention in the earlier post.
You're correct. There isn't a VESA option for 1280 x 800. However, if you get through installation, you just use the nvidia driver.

If you want to use just the live CD, specify the nv driver in xorg.conf. Then hit ctrl+alt+backspace to restart your xserver. It will use the nv driver, which does have a nice resolution for the laptop. No hardware accelleration, but still.

---

### Post by dragonfyre13 on 2006-12-14
> **NickB said:**
> If you want to use the "S" button to put your laptop into powersaving mode, use the following scripts:

/etc/acpi/averatec-powersave.sh```

#!/bin/sh

CPU_MAX_FREQ=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq`
CPU_MIN_FREQ=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq`

if [ "$1" = "on" ]; then
        echo $CPU_MIN_FREQ > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
else
        echo $CPU_MAX_FREQ > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
fi
```
(make sure you do a "chmod +x /etc/acpi/averatec-powersave.sh")

/etc/acpi/events/averatec-powersave-off:```

event=processor P001 00000080 00000000
action=/etc/acpi/averatec-powersave.sh off
```
/etc/acpi/events/averatec-powersave-on```

event=processor P001 00000080 00000008
action=/etc/acpi/averatec-powersave.sh on
```
The reason I'm changing the scaling_max_freq instead of scaling_governor is because this is primarily being controlled by the powernowd, which may be customized to set scaling_governor to something other than "ondemand" (e.g. performance).  Setting the maximum frequency to the CPU's minimum will ensure maximum power saving no matter what.

Hope that helps someone.

Nick
You mind if I use this? I'm putting it up there now, if you do just reply to the thread.

---

### Post by NickB on 2006-12-15
> **dragonfyre13 said:**
> You mind if I use this? I'm putting it up there now, if you do just reply to the thread.
No problem... that's what it's there for! 8)

I also wrote a tray app in python that will monitor this.  I'm putting some finishing touches on it, but I will post it when I'm satisfied with it :)

Nick

---

### Post by NickB on 2006-12-16
Here is a .deb that implements the complete power save function (using the S button).  It includes a python program that will run in the system tray to provide an indicator when in powersave mode.  In order to use this, you will need the python-notify package.  All other packages needed are provided with a standard ubuntu-desktop installation.

Note that this replaces the files mentioned in the previous post in /etc/acpi, so you do not need to manually create those files.

Also included is a tarball of the source needed to build the package.  Any comments/suggestions/fixes are welcome.

From the README:
In order to use the tray icon notifier in a GNOME desktop, open
System->Preferences->Sessions, select the Startup Programs tab,
click the Add button and type powersave-trayicon into the text
entry box and click OK.  The next time you start your GNOME
session the tray icon will be active.


Thanks,
Nick

P.S. The original files I uploaded were missing the necessary dbus configuration file; the corrected versions are now attached.

---

### Post by dragonfyre13 on 2006-12-19
Any chance you could re-upload the tar file with a copy of a license? (GPL is a preference) I just want to make sure that everything is set for people. I'm going to post something on the averatec boards, so I want to make sure we are ready for it.

---

### Post by NickB on 2006-12-19
> **dragonfyre13 said:**
> Any chance you could re-upload the tar file with a copy of a license? (GPL is a preference) I just want to make sure that everything is set for people. I'm going to post something on the averatec boards, so I want to make sure we are ready for it.
Indeed; apparently the copyright file went missing from the debian directory; I've also added COPYING to the package source directory as well.  I'm updating the file in the original post.

Nick

---

### Post by dragonfyre13 on 2006-12-21
Thanks a bunch. I appreciate it. I'll post this on a few boards that were asking about Linux on the 2370, and make sure I reference you as the developer, and point them to this thread.

I'm on vacation right now, but I'll be sure to do that after Christmas.

In case I didn't say it already, you have my appreciation for the scripts, and for your work on it. I'm sure you have everyone elses too. ^_^

---

### Post by JonGoldberg on 2006-12-23
The URI for the wireless driver has changed - the new one is:
[http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

---

### Post by JonGoldberg on 2006-12-24
After two weeks of owning a 2370, I'm finally getting to set it up for Ubuntu...
A few thoughts:
- The Synaptics touchpad gets misidentified as a Wacom tablet.  It's fine for pointing, but scrollbars don't work, nor does multi-finger tapping, or the ability to turn off tapping!  The directions I found at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) solved all my problems.

- Running sudo dpkg-reconfigure xserver-xorg seemed unnecessarily complicated.  Could I have gotten the same effect from simply editing my xorg.conf to have 24-bit depth and change the video driver to "nv"?

- Perhaps on a related note, my Averatec is showing 1280x800, but only at 50Hz.  Windows reports 60Hz.  I'm about to try modelines, but maybe someone can post their xorg.conf that has 1280x800 @60Hz working, preferably without modelines?

---

### Post by dragonfyre13 on 2006-12-26
I'll take a look at the touchpad. Honestly I hadn't noticed, but I will check it out and put it on the main post a bit later.

As for your second question, yep, that does the same thing. I believe you can set monitor refresh in there too, so it's easy to do that. Mainly, the reason I had people run the command was because it's a nice wizard/gui interface that asks questions instead of editing a file. This is oriented towards people fairly new to ubuntu, because if you know the file to edit, and you've done it before, generally you can figure it out.

P.S. if you want the proprietary nvidia driver, you have to change nv to nvidia. If you run nvidia-glx-config then you don't have to, because it does it for you.

As for the 60hz, I'll check that out too. I didn't notice that either. Does it make a big difference in something? I didn't notice ghosting in games, and everything looks fine otherwise.

---

### Post by JonGoldberg on 2006-12-26
> **dragonfyre13 said:**
> 
As for the 60hz, I'll check that out too. I didn't notice that either. Does it make a big difference in something? I didn't notice ghosting in games, and everything looks fine otherwise.

I haven't had enough time to play around with games, etc; I'm also not convinced I set my xorg.conf up right, so maybe yours is different.  Since changing my video settings though, I get a weird static-y effect on the Ubuntu logo during shutdown.

You'll probably also want to update the URI for the wireless driver (see my earlier post).

Thank you SO MUCH for putting all this together - I wouldn't have bought this lovely little laptop without seeing this.

---

### Post by NickB on 2006-12-27
> **JonGoldberg said:**
> Since changing my video settings though, I get a weird static-y effect on the Ubuntu logo during shutdown.
I have the same problem.  Same if you switch to a text VT after running X.  If you figure out a solution for this, please post.

Thanks,
Nick

---

### Post by cameroni2003 on 2006-12-27
I'm curious to see if anyone has gotten WPA to work.  I cannot seem to get it working

---

### Post by dragonfyre13 on 2006-12-28
> **JonGoldberg said:**
> The URI for the wireless driver has changed - the new one is:
[http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

Thanks for that. I've updated the link.

---

### Post by dragonfyre13 on 2006-12-28
> **cameroni2003 said:**
> I'm curious to see if anyone has gotten WPA to work.  I cannot seem to get it working

If you get on IRC, they can help you setup Ndiswrapper. That's the only way I know to get WPA working. I haven't actually tried it yet, so it very well may just be a few tweaks of the RT73 driver.

---

### Post by dragonfyre13 on 2006-12-28
> **NickB said:**
> I have the same problem.  Same if you switch to a text VT after running X.  If you figure out a solution for this, please post.


I get it too. I think it's something with the Nvidia driver. It started happening immediately after that, but that was about the time that I started patching my kernel for suspend2 to check it out, so I didn't know which caused it. Now I do.

I'll check a few things out, and see what I can find. It's annoying, and crappy asthetics, but it's not functionality, so I can't put it that high on the priority chain.

---

### Post by dragonfyre13 on 2006-12-28
> **JonGoldberg said:**
> I haven't had enough time to play around with games, etc; I'm also not convinced I set my xorg.conf up right, so maybe yours is different.  Since changing my video settings though, I get a weird static-y effect on the Ubuntu logo during shutdown.

You'll probably also want to update the URI for the wireless driver (see my earlier post).

Thank you SO MUCH for putting all this together - I wouldn't have bought this lovely little laptop without seeing this.

It's great to hear feedback like that. I like doing this, and I like helping out others with linux if I can. If I can make the linux experience even a little bit better, I'm happy.

I'll post my Xorg.conf when I have a chance. Anyone else that checks these boards feel free to do the same. Especially if you aren't having the scanlines effect that we are. 

P.S. The effect (I think) comes from improper refresh rates. Perhaps the shutdown doesn't like the refresh rate, and bugs up. It isn't the same as the settings from Xorg.conf though.

---

### Post by NickB on 2006-12-28
> **dragonfyre13 said:**
> It's annoying, and crappy asthetics, but it's not functionality
Try working on the console for an extended period of time :p 

Nick

---

### Post by mrajaa on 2006-12-28
I love this thread.  A person interested in installing ubuntu linux on the Averatec 2370 does not have to look any further than this thread.  

It has made my investment in the Averatec totally worthwhile and also made it look Super Cool.  Thanks to all the contributors to this thread and especially drangonfyre.

-Raj

---

### Post by Joshua on 2006-12-29
This is in reference to another thread I have going, but I thought maybe someone on this one would have a quick answer.

Has anyone gotten encrypted DVDs to play on this laptop with Edgy for AMD64?

I've done this on other computers with no problems (with the 32-bit OS), but I can't get it to work on the Averatec.  I had considered re-installing Ubuntu, thinking that during my initial phase of figuring out how things worked, I may have done something that prevents DVD playback.  But I don't want to do a re-install unless I'm sure someone else has been able to get it to work.

The other thread is:
[http://www.ubuntuforums.org/showthread.php?t=322537](http://www.ubuntuforums.org/showthread.php?t=322537)

---

### Post by NickB on 2006-12-29
> **Joshua said:**
> Has anyone gotten encrypted DVDs to play on this laptop with Edgy for AMD64?
```

sudo apt-get install libdvdread3
sudo apt-get install build-essential
sudo /usr/share/doc/libdvdread3/install-css.sh
```
**DISCLAIMER: It may be illegal in your country to install libdvdcss2.  Use at your own risk!**

HTH,
Nick

---

### Post by Joshua on 2006-12-29
Yes, that was my original process for getting it to work, but it still wouldn't play DVDs.  It would show the unencrypted warnings at the beginning, but then it would stop and give an error indicating that I didn't have libdvdcss2 installed.  Since then, I have tried all sorts of other things.  I'll try to do it that way again tonight, and keep an eye out for any errors, but has anyone else actually gotten it to work with the 64-bit OS?

NickB, you run a 64-bit OS, right?  And that process worked for you?

There's no reason that the DVD drive would be preventing this is there?  I did check (under Windows) to see that a region code was set.  I think it said "1" for US.  But that's the only thing I could think of.

I couldn't find any settings in Xine or Totem to specify the location of libdvdcss2, and besides, the feedback from running ```
$sudo xine --verbose
``` makes it look like it's decrypting stuff.

---

### Post by NickB on 2006-12-29
> **Joshua said:**
> Yes, that was my original process for getting it to work, but it still wouldn't play DVDs.  It would show the unencrypted warnings at the beginning, but then it would stop and give an error indicating that I didn't have libdvdcss2 installed.
That was my exact experience until I installed libdvdread, and it gave me instructions upon installation to run /usr/share/doc/libdvdread3/install-css.sh.  I had build-essential already installed, so that command alone cleared everything right up.  This should probably be on ubuntuguide.org somewhere, but it's not :???: 

BTW, I installed xine-ui before doing this, since I'm pretty sure a DVD sink for gstreamer isn't in edgy (that I noticed, I could be wrong).  But anyway if you want to use totem, totem-xine works much better on DVDs even if you get the right sink installed.

> **Joshua said:**
> NickB, you run a 64-bit OS, right?  And that process worked for you?
Yep, Edgy amd64.  I've gotten xine, mplayer and vlc all to play DVDs, though it might interest you to know that I can get both xine and vlc to crash on one DVD I have, while mplayer will happily play it.  This might be due to the fact that I use Christian Marillat's respository for all things mplayer related.  Unfortunately I don't have a version of mplayer with DVD navigation, so doing anything other than playing the main title track can be tricky if you don't know how the disc is laid out.

Overall my experience is that mplayer is a better tool for playing video, if you can master the command line, but xine has very accurate closed-caption decoding, so I use that more often.  If you want a full featured GUI that's easy to use, then vlc all the way.  All 3 are going to depend on you getting libdvdcss2 installed properly, though.

Nick

---

### Post by lythandrel on 2006-12-29
dragonfyre, I followed all your directions and I am GRATEFUL for them, but I added the link for the nvidia drivers (the albertomilone site) and I get the following error.

Failed to fetch [http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/Packages.gz](http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/Packages.gz)  404 Not Found

I did cut and paste the link you gave, so the slash in between 32 bit and binary is a regex thing..  Anyhow, if you can check this and/or update the link, I'd be ecstatic, since there was some oddity with reconfiguring xorg (but at least everything works)

Thanks in advance..

---

### Post by NickB on 2006-12-30
For beryl, check out this page:

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA)

And skip to the section marked "Adding Beryl Repository."

Nick

---

### Post by bigbridges06 on 2007-01-01
Hey guys. I have been playing with Linux for around 6 months. I'm not exactly a newbie, but i'm no where near a techie. Anyway, I recently purchased the Averatec 2300 series on the after Thanksgiving OfficeMax sale and am very interested in putting Ubuntu on it. I downloaded Edgy Eft, both versions. My first question is which version do I need to install. My next question is does anybody know why both versions of Edgy Eft keep pauses when I go to partition my drives? I let them sit over night and they still did nothing. I know this is probably obvious what my specs are, but here they are just in case: Windows XP Media Center SP2, Averatec 2300 series, AMD Turion(tm) 64x2 Mobile technology TL-50, 1.61 GHz, 960 MB RAM.
One Last Thing: thanks so much, you'll are doing some wonderful work with this laptop and Ubuntu linux-the OS of the free world and the next generation.

---

### Post by dragonfyre13 on 2007-01-02
> **bigbridges06 said:**
> Hey guys. I have been playing with Linux for around 6 months. I'm not exactly a newbie, but i'm no where near a techie. Anyway, I recently purchased the Averatec 2300 series on the after Thanksgiving OfficeMax sale and am very interested in putting Ubuntu on it. I downloaded Edgy Eft, both versions. My first question is which version do I need to install. My next question is does anybody know why both versions of Edgy Eft keep pauses when I go to partition my drives? I let them sit over night and they still did nothing. I know this is probably obvious what my specs are, but here they are just in case: Windows XP Media Center SP2, Averatec 2300 series, AMD Turion(tm) 64x2 Mobile technology TL-50, 1.61 GHz, 960 MB RAM.
One Last Thing: thanks so much, you'll are doing some wonderful work with this laptop and Ubuntu linux-the OS of the free world and the next generation.


Welcome! Glad to have you here, and glad to see you taking a liking to such a great OS!

As for your questions, I would say it's an issue with the disk first. I didn't have any issue repartitioning. However, tell us what you are trying to do, and I'll see if I can help. For example, I know I had some difficulty shrinking an NTFS partition on another laptop I have with roughly the same specs. This one, I blew away all partitions to use Ubuntu, so I wouldn't know. Are you trying to shrink any partitions?

Also, the 32 bit version is easier for me, because it causes less issues. However, NickB can give you a rating of the 64 bit version if you want. I don't know that much about it.

P.S. Got the same laptop at the same sale. Kinda why I started the thread. I figured people would need a nice guide for this great laptop.

---

### Post by dragonfyre13 on 2007-01-02
> **lythandrel said:**
> dragonfyre, I followed all your directions and I am GRATEFUL for them, but I added the link for the nvidia drivers (the albertomilone site) and I get the following error.

Failed to fetch [http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/Packages.gz](http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/Packages.gz)  404 Not Found

I did cut and paste the link you gave, so the slash in between 32 bit and binary is a regex thing..  Anyhow, if you can check this and/or update the link, I'd be ecstatic, since there was some oddity with reconfiguring xorg (but at least everything works)

Thanks in advance..
I'll look into it. I'm getting the same error now, but I know that one has some issues with going down every once in a while. I'm looking for a good replacement if anyone wants to suggest one.

---

### Post by NickB on 2007-01-02
> **dragonfyre13 said:**
> Also, the 32 bit version is easier for me, because it causes less issues. However, NickB can give you a rating of the 64 bit version if you want. I don't know that much about it.
You know you want to run the 64-bit version because you want to be super cool :cool: 

Seriously, you can run just about anything on 64-bit that you can run on 32-bit, though it may take some effort.  The only thing that you really can't get in 64-bit land is a java plugin for your 64-bit Firefox.  There are ways to get yourself a 32-bit Firefox running in a 64-bit environment, but this will mean installing it manually one way or another.  But that's a different thread.

Your relative newness to the scene means that installing the 32-bit distro will probably be more successful for you and give you some confidence.  If you are really interested in running 64-bit and want the challenge of learning the system (because you WILL need a bit of knowledge to get some things going), I suggest you still go through an entire 32-bit install to learn what you'll need to do to get your system running.  Take notes.  Then, when you're confident you have a system running that you like, start over with the amd64 flavor.

This thread will probably work for 99.99% of the people out there, even in 64-bit land.  If it doesn't work, then you can always go back to 32-bit, for which you have a documented procedure to get you back to where you started.  You did take notes, right? ;) 

Good luck,
Nick

---

### Post by dragonfyre13 on 2007-01-02
> **NickB said:**
> You know you want to run the 64-bit version because you want to be super cool

Oh, Oh!!! I want to be Super Cool!

Seriously, I've shrunk the 32bit partition to make room for a 64bit (smaller, but there) partition. There is enough hub-ub about the 64 bit version that I need to check it out. Besides, everything will be 64 bit by 2008 anyway. ([http://www.dragonfyre13.com/blog/index.php/2006/12/28/6/](http://www.dragonfyre13.com/blog/index.php/2006/12/28/6/)) so I should look into it.

If you afraid of the Java limitation, seriously, don't be. There is plenty of help as far as that is concerned. Also, since Java went FOSS recently, that will be fixed in short order.

I did have a question though. The 64 bit repositories are different aren't they? I would think they would have to be. If they are, and someone feels like finding some repositories that are comparable, I'd be happy to put them side by side with the 32 bit ones.

---

### Post by NickB on 2007-01-02
> **dragonfyre13 said:**
> I did have a question though. The 64 bit repositories are different aren't they? I would think they would have to be. If they are, and someone feels like finding some repositories that are comparable, I'd be happy to put them side by side with the 32 bit ones.
I'm fairly certain all the repositories you posted have amd64 binaries as well.  That is, I don't recall having to google for them.

Nick

---

### Post by dragonfyre13 on 2007-01-03
Cool. So it's not even as complicated as I thought. Neat.

Just as a question, does anyone think I should change the installation of the NVidia drivers to the method using envy?

---

### Post by bigbridges06 on 2007-01-03
Thanks for the intro and help guys. I was recently trying to patch some 3rd party themes in Windows and that crashed it. Well, I thought i might call the Averatec company support. I did. I figured I might to reformat and guess what the guy told me. The only way to reformat was to use the pre-installed Phoenix software. Averatec doesn't even offer a buyable reformat CD. You have to pay Phoenix $40 to use their software. I don't mind paying for certain software. But the fact is I should at least receive a reformat CD or free software for the price I paid for my laptop. Anyway I reformated and now the Desktop CD doesn't freeze on the partition manager. However, when I tell it to manually shrink the Windows partition to make room, it tells me that it cannot. Has anyone had this trouble? What should I do? Is there another partitioner that could solve my problem? Sorry, my reply is long and little off topic, but I thought ya'll might understand my frustration. Thanks :)

---

### Post by lythandrel on 2007-01-03
> **dragonfyre13 said:**
> I'll look into it. I'm getting the same error now, but I know that one has some issues with going down every once in a while. I'm looking for a good replacement if anyone wants to suggest one.

The odd thing I'm noticing about the albertomilone repository is the fact that the parent domain, [www.albertomilonecom](www.albertomilonecom) is up, however, the repository gives a 404.  Perhaps it's time to poke the maintainer to see if he changed things around?  If I do so, it'll have the subtlety of a 5000lb anvil, and you might be more coercive with making the point that you've authored a rather complete howto for us averatec 2370 lovers which points to his repository in order for you not to have to seek out an alternative repository after all the hard work you've done.
](*,)

---

### Post by NickB on 2007-01-04
bigbridges06,

Try this thread: [http://www.averatecforums.com/showthread.php?t=5703](http://www.averatecforums.com/showthread.php?t=5703)

Nick

---

### Post by dragonfyre13 on 2007-01-04
> **bigbridges06 said:**
> Thanks for the intro and help guys... Anyway I reformated and now the Desktop CD doesn't freeze on the partition manager. However, when I tell it to manually shrink the Windows partition to make room, it tells me that it cannot. Has anyone had this trouble? What should I do? Is there another partitioner that could solve my problem? Sorry, my reply is long and little off topic, but I thought ya'll might understand my frustration. Thanks :)

That's fine. First thing to do is boot into windows, and run "chkdsk /f" from the command prompt. Then reboot. TWICE.

That will clear any bad blocks out of the ntfs partition.

Try the partition manager again.

If it doesn't work (It didn't for me) I've always had to use Acronis Disk Director to resize the NTFS partition. ](*,) 

The command that is failing is "ntfsresize", so if you look for help elsewhere, this should point you in the right direction.

Look for an external disk to resize the NTFS partition. There are a few trials out there that will allow you to shrink them, and you can try those to see if they work. That's what I reccommend. Normally, I would say don't go proporietary, but while linux has made advances in this area that make most things easy, for some reason I can never get this to work.


I'm not sure, but this trial may allow you to resize, just not create large partitions.
[http://www.acronis.com/homecomputing/download/diskdirector/](http://www.acronis.com/homecomputing/download/diskdirector/)

Oh, and I have to say, buy it if you like it. I did, and I'm extatic with the purchase.

---

### Post by dragonfyre13 on 2007-01-04
> **lythandrel said:**
> The odd thing I'm noticing about the albertomilone repository is the fact that the parent domain, [www.albertomilonecom](www.albertomilonecom) is up, however, the repository gives a 404.  Perhaps it's time to poke the maintainer to see if he changed things around?  If I do so, it'll have the subtlety of a 5000lb anvil, and you might be more coercive with making the point that you've authored a rather complete howto for us averatec 2370 lovers which points to his repository in order for you not to have to seek out an alternative repository after all the hard work you've done.
](*,)

You know, I think I'll do that. He seems pretty helpful in other areas, including the envy script (he wrote it), so I might go do that. Thanks!

---

### Post by Joshua on 2007-01-04
Has anyone gotten the microphone to work under Linux?

Also, I got my DVD playing to work.  I don't know what the problem was.  It may have been the order that I installed everything, but I'm not sure.  Anyway, I was introduced to VLC during the whole process, and it looks to me like it will play wmv files out of the box even though I'm using the AMD64 kernel.  How is that possible?

---

### Post by lythandrel on 2007-01-07
I haven't tried this yet, but looks like the albertomilone repositories for his videop drivers may have been moved alone.  he even has a wholw howto.  Here it is.

[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.de](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.de)

The unfortunate thing is that his directions are a bit on the complex side.  Your howto was beautifully simple.  I know no one wants to edit their howto after
they've made a complete and simple one

I do believe the next link is the one directly to the driver.


[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb)

---

### Post by lythandrel on 2007-01-07
> 

P.S. The original files I uploaded were missing the necessary dbus configuration file; the corrected versions are now attached.


Small problem with the files included.  It's not a problem for me, I'm use to compiling stuff, but the .deb you provided was a 64 bit, no 32 bit.  Could you please add that for the relative n00bs?

---

### Post by deadlydeathcone on 2007-01-07
> **lythandrel said:**
> Could you please add that for the relative n00bs?

It was the first thing I did after I downloaded it, so it's no problem.


Thanks for the app, nickb!

---

### Post by NickB on 2007-01-08
Thanks for uploading a i386 package.  It should be architecture independent; I didn't really think about that at the time.  I will probabably do that for the next version, which will see some minor changes soon.

Nick

---

### Post by dragonfyre13 on 2007-01-08
> **lythandrel said:**
> 
I do believe the next link is the one directly to the driver.


[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb)

I'll likely go with Envy as the main way of installing the drivers. It's just easier, and simpler for new people. Now I just have to go modify the HowTo.

Also, as for the above quote, it pointed to the legacy driver, not the highest version driver. That's OK, it's not in operation anymore anyway.

I did see what you were talking about, and I'll try to simplify it when I have a chance.

---

### Post by dustmote on 2007-01-09
I've been searching forums (because I know the answer is out there somewhere) and I haven't found an answer to this question yet. Help would be appreciated.

I've had my Averatec 2370 running with the "acpi=off" option at boot since install. It won't boot without that option. It hangs on:
```
[ *some numbers* ] io scheduler cfq registered (default)
```

Any ideas on how to get around this? I need to boot with acpi support for obvious reasons, and without it I can't use the Power Save Button.

Aside from this problem your thread has been a lifesaver! Thanks!

---

### Post by lythandrel on 2007-01-09
> **dustmote said:**
> I've had my Averatec 2370 running with the "acpi=off" option at boot since install. It won't boot without that option. It hangs on:
```
[ *some numbers* ] io scheduler cfq registered (default)
```

Any ideas on how to get around this? I need to boot with acpi support for obvious reasons, and without it I can't use the Power Save Button. 

Hrm.... this is a bit odd.  acpi has been working quite well out of the box with mine.  wonder if there's more than one spec for the 2370's.  Follow the howto and things should go fine.

---

### Post by dustmote on 2007-01-09
Here is a reiteration of my recurrent problem of boot-hangs. My Averatec 2370 hangs at boot of the livecd just after the following line:
```
[ *some numbers* ] ata2: SATA max UDMA/133 cmd 0xD400 ctl 0xD082 bmdma 0xD008 irq 20
1
_
```
The "1" at the very end of that line wordwraps around to begin the next line, and the cursor just blinks one line down from that. My boot parameters are the almost the default livecd boot parameters without two things. I have removed "quiet" and "spash" (so that I could see where it's hanging). That's all. I can make the computer boot if I add the "acpi=off" option. Obviously though, I'll need acpi down the road, so this isn't a good solution. I'll be checking around these forums to find the answer.

Any help would be appreciated.

_____________________
another thing ... **wireless drivers**
i've followed your instructions perfectly, and i can't get the wireless drivers to compile, nor can i get them to compile following the *slightly* different instructions in the readme file they come with... are these wireless drivers no good with the amd64 build of ubuntu?

---

### Post by NickB on 2007-01-10
I was able to get the LiveCD to boot with only the "noapic" option; I didn't need acpi=off (I don't think it would boot if I did that anyway).

As far as the wireless drivers for amd64, they work fine (more or less) for me, see my post [http://www.ubuntuforums.org/showpost.php?p=1868533&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1868533&postcount=10)

Nick

---

### Post by dustmote on 2007-01-10
Well, I assumed "noapic" and "acpi=off" were the same thing because I've been misreading "noapic" as "noapci" all this time. I guess I need to read up more on the basics. :) Thanks. As for the wireless drivers, I can't get them to compile. I'm getting tons of warnings and then it quits with an error (which the faq said was a no-no) and doesn't make any *.ko files.> **NickB said:**
> Go to the rt73 directory and make, make install.  Copy the rt73.bin file as noted above, but DO NOT create/copy the rt73sta.dat, as it will cause a kernel Oops.  You don't need it anyway.I can't do the all-important "make"


------ update
I tried "noapic" and the system booted like a charm. I went to /boot/grub to change menu.lst and my system log spewed some error into my terminal window about "Disabling IRQ #7" which I've never seen before. It doesn't seem fatal. I found a page containing information about amd64 boot options ([http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt](http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt)) and found this:> noapic	 Don't use the IO-APIC.
acpi=off	Don't enable ACPII'm not sure what all that means, but if apic is part of acpi then "acpi=off" must certainly be a more severe control. I'm also wondering about...> acpi=noirq	Don't route interrupts...but I haven't tried it yet. There isn't any risk of damaging my hardware by playing around with this stuff, is there?

---

### Post by NickB on 2007-01-10
> **dustmote said:**
> As for the wireless drivers, I can't get them to compile. I'm getting tons of warnings and then it quits with an error (which the faq said was a no-no) and doesn't make any *.ko files.I can't do the all-important "make"
Make sure you have build-essential and linux-headers-2.6.17-10 (assuming the stock kernel) installed.

> **dustmote said:**
> I tried "noapic" and the system booted like a charm. I went to /boot/grub to change menu.lst and my system log spewed some error into my terminal window about "Disabling IRQ #7" which I've never seen before. It doesn't seem fatal.
Yes, I had this problem, and it's annoying because it will run up the CPU to 100% while it's polling until it gives up.  The problem is a bad USB driver being loaded; I don't remember which one it was, but I'll check my settings when I'm in front of my laptop and let you know how to fix it.

> **dustmote said:**
> There isn't any risk of damaging my hardware by playing around with this stuff, is there?
Probably not, but there is always a chance you could damage your hardware with the wrong boot option.

Nick

---

### Post by NickB on 2007-01-10
> **NickB said:**
> The problem is a bad USB driver being loaded; I don't remember which one it was, but I'll check my settings when I'm in front of my laptop and let you know how to fix it.
OK. the offending module is ohci_hcd.  First, edit /etc/modprobe.d/blacklist and add:

blacklist ohci_hcd

Next, execute the following commands:

sudo rmmod -a ohci_hcd
sudo update-initramfs -u

That should keep it from appearing the next time you boot.

Nick

---

### Post by dustmote on 2007-01-10
yay! thanks for your useful posts :) ...i'm running a battery calibration at the moment, but i'll try your solutions and tell you my results with this post later...


---update
Ok.
I followed all your instructions, checked and rechecked. I *cannot* get the wireless drivers to compile and produce the *.ko file(s) without error. Also, after following your instructions about the USB I now have no mouse whatsoever (probably just have to run **dpkg-reconfigure xserver-xorg** i hope). Woo!

---

### Post by dustmote on 2007-01-12
*doubleposting for the purpose of bumping topic

So, now I'm down to two issues. Thanks to all of your generous help, I've gotten it to this:
(1) I have no USB because I blacklisted the driver NickB said was causing the IRQ Polling mishap (and he seems to be right, but now I have no USB).
(2) I *still* can't compile the RT73 drivers. Here is a printout of what happens when I "make" them:
```
user@computer:/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
In file included from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:17: error: conflicting types for ‘atomic_t’
include/asm/atomic.h:18: error: previous declaration of ‘atomic_t’ was here
include/asm-i386/atomic.h:46: error: conflicting types for ‘atomic_add’
include/asm/atomic.h:47: error: previous definition of ‘atomic_add’ was here
include/asm-i386/atomic.h:61: error: conflicting types for ‘atomic_sub’
include/asm/atomic.h:62: error: previous definition of ‘atomic_sub’ was here
include/asm-i386/atomic.h:78: error: conflicting types for ‘atomic_sub_and_test’
include/asm/atomic.h:79: error: previous definition of ‘atomic_sub_and_test’ was here
include/asm-i386/atomic.h:95: error: conflicting types for ‘atomic_inc’
include/asm/atomic.h:96: error: previous definition of ‘atomic_inc’ was here
include/asm-i386/atomic.h:109: error: conflicting types for ‘atomic_dec’
include/asm/atomic.h:110: error: previous definition of ‘atomic_dec’ was here
include/asm-i386/atomic.h:125: error: conflicting types for ‘atomic_dec_and_test’
include/asm/atomic.h:126: error: previous definition of ‘atomic_dec_and_test’ was here
include/asm-i386/atomic.h:144: error: conflicting types for ‘atomic_inc_and_test’
include/asm/atomic.h:145: error: previous definition of ‘atomic_inc_and_test’ was here
include/asm-i386/atomic.h:164: error: conflicting types for ‘atomic_add_negative’
include/asm/atomic.h:165: error: previous definition of ‘atomic_add_negative’ was here
include/asm-i386/atomic.h:182: error: conflicting types for ‘atomic_add_return’
include/asm/atomic.h:183: error: previous definition of ‘atomic_add_return’ was here
include/asm-i386/atomic.h:208: error: conflicting types for ‘atomic_sub_return’
include/asm/atomic.h:193: error: previous definition of ‘atomic_sub_return’ was here
In file included from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99,
                 from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm-i386/atomic.h:248:1: warning: "atomic_set_mask" redefined
In file included from include/asm/spinlock.h:4,
                 from include/linux/spinlock.h:86,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:44,
                 from include/linux/module.h:9,
                 from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:63,
                 from /mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
include/asm/atomic.h:418:1: warning: this is the location of the previous definition
/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/mnt/osshare/linux/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
```
Now unless I am expected to go through and fix all those programming errors myself, I'd like to know how you all got around this problem (or what it is I'm doing wrong).

Thanks everyone!

---

### Post by NickB on 2007-01-12
dustmote,

I was under the impression that you were on amd64, but your compiler output shows references to i386 headers.  I'm not sure what to make of that.  It doesn't look like you are compiling from cvs, but from a download; I used source from cvs, so I can't comment on what the differences might be.

As for the USB, see if you have ANY usb drivers loaded (use lsmod), such as ehci_hcd or uhci_hcd.  The correct driver should have been automatically detected; I'm not sure why removing ohci_hcd, which is a legacy (USB 1.1) driver has caused you problems.

Nick

---

### Post by dustmote on 2007-01-12
NickB,

As far as I know, I am running on amd64. I torrented and then installed Ubuntu using the following image: **ubuntu-6.10-desktop-amd64.iso**. I assumed that by default it would set me up with an amd64 system. Am I incorrect? That being said, how do I determine what headers I am using, and furthermore, obtain the *correct* ones.

Also, I did download the source from the RaLinkTech website. I don't have cvs installed, nor do I know how to install it because I don't know which repository in my sources.list file it would download from (if any) or what the package is called. I'm afraid to just download random packages like "sudo apt-get install concurrent-versions-system" or "sudo apt-get cvs" one of which probably is the correct one, but then again it may not be.

For now, I'll try what you instructed about the USB drivers. For future reference, how did you determine that ohci_hcd was the faulty driver in the first place?

Thanks again.
dustmote


**---update**
lsmod turned up the following:
```
ehci_hcd               40456  0 
usbcore               167840  2 ehci_hcd
```
i'm assuming usbcore is used whenever usb ports are present, but ehci_hcd is one of the usb drivers that you mentioned... but my usb ports still seem inactive

---

### Post by NickB on 2007-01-12
> **dustmote said:**
> As far as I know, I am running on amd64. I torrented and then installed Ubuntu using the following image: **ubuntu-6.10-desktop-amd64.iso**.
I'm going to have to sit down through the process again from scratch to see if there is anything I did special with the sources.  There may perhaps be an arch flag in the Makefile that is directing the compiler to build an i386 version instead of amd64.

> **dustmote said:**
> I'm afraid to just download random packages like "sudo apt-get install concurrent-versions-system" or "sudo apt-get cvs" one of which probably is the correct one, but then again it may not be.
You want cvs; but I will check out the source tarball to see if it is usable for me if you don't want to go through the trouble of setting up cvs.

> **dustmote said:**
> For future reference, how did you determine that ohci_hcd was the faulty driver in the first place?
Deduction.  It didn't seem likely that ohci_hcd would be the proper driver for this laptop.  You could remove it without any problems, meaning there are no other dependencies on this module, which would be the case if your other USB devices were using it.  Additionally, it was polling the wrong IRQ.  I'm not sure this is related to the problem of your mouse not working; did you make any other changes to your xorg.conf file?

Nick

---

### Post by dustmote on 2007-01-12
> **NickB said:**
> I'm not sure this is related to the problem of your mouse not working; did you make any other changes to your xorg.conf file?I ran through "sudo dpkg-reconfigure xserver-xorg" once as directed by the faq. I chose autodetection as much as I could. I did this *after* removing the driver and blacklisting it, so that the new xorg.conf would work the best. Obviously I was wrong. I'll go look over it and check. Maybe it's still using the old driver, but since it can't find it it's just giving up? I don't know how these things work yet.

---

### Post by NickB on 2007-01-12
For your rt73 build, edit the file rt_config.h and find the line:

#include <asm-i386/atomic.h>

and change to:

#include <asm-x86_64/atomic.h>

That will get your module built.

As for the mouse problems, here's what I've got in xorg.conf:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```and later:```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
```
Nick

---

### Post by dustmote on 2007-01-13
ok nickb. you've been a HUGE help to me so far...

**wireless:**
your suggestion about changing the include line to match my architecture obviously did the trick right away... the drivers compiled without a problem and i've been able to get the device working for the most part.. i can't thoroughly test it though because (a) when i had connection manager installed i realized my only test network was WPA and that's a pain to set up and (b) something in connection manager's startup scripts caused my bootup to hang, requiring ctrl-alt-del to unhang and continue booting...

the verdict? i uninstalled connection manager and all the things that i installed because it depended on them... the card itself is functioning, although i won't be using it for awhile... knowing i got it working for the most part (even if i can't use it atm) is good enough for me i guess, since ultimately i'll still be able to use the laptop effectively without it..

**mouse:**
my xorg.conf is *identical* to yours (as you posted it) and still no usbmouse... it's a logitech trackball.. might'n that have anything to do with these issues? i hope not... anyway, that's the important one at the moment...


everything else that i've wanted to get working with this system is working as of right now, and i've learned a ton about how to tiptoe around linux, accidentally screw things up, and then recover the system.... thanks a ton :)

---

### Post by NickB on 2007-01-13
> **dustmote said:**
> my xorg.conf is *identical* to yours (as you posted it) and still no usbmouse... it's a logitech trackball.. might'n that have anything to do with these issues? i hope not... anyway, that's the important one at the moment...
OK, I didn't realize you were talking about an external mouse. That changes things somewhat. Wait until the system comes up before plugging in the trackball. After you plug it in, look at the end of the output generated from the dmesg command. If you see text about a new usb device, then you know it's being recognized, so then it becomes an xorg.conf issue, which is beyond the scope of this thread :)

Nick

---

### Post by dustmote on 2007-01-13
NickB,

I originally booted with "acpi=off" and my trackball worked fine, but I switched over to "noapic" at your recommendation which fixed all sorts of power management things and broke the trackball driver or something. That is when I had the IRQ polling problems and the trackball would quit when I received that "Disabling IRQ #7" message. Then I disabled the legacy driver at your recommendation and now there is no trackball at all, but it fixed the IRQ problems.

Sorry if I didn't make these things clear before.

Anyway, those are the reasons why I think problem is not xorg.conf related. That said, I tried what you suggested about dmesg (which I don't know how to use very well and the man page didn't tell me anything really useful).

I booted the computer. Did dmesg. Copied its output into gedit. Plugged in the mouse. Waited a minute. Did dmesg. Copied its output into another gedit tab. They were the same.

This is proving to be quite a hassle, isn't it?
Here are all the lines from that output which have "usb" in them or seem to related to lines having "usb" in them. I've read through them and they don't reveal much information to me.```
[   18.920795] usbcore: registered new driver usbfs
[   18.921630] usbcore: registered new driver hub
[   19.421955] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   19.422139] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   19.422224] ehci_hcd 0000:00:0b.1: debug port 1
[   19.422274] ehci_hcd 0000:00:0b.1: irq 14, io mem 0xfe2dfc00
[   19.422319] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.422433] usb usb1: configuration #1 chosen from 1 choice
[   19.422492] hub 1-0:1.0: USB hub found
[   19.422534] hub 1-0:1.0: 6 ports detected
[   19.769683] usb 1-6: new high speed USB device using ehci_hcd and address 2
[   20.044077] usb 1-6: configuration #1 chosen from 1 choice
[   31.020946] rtusb init ====>
[   31.021036] idVendor = 0xdb0, idProduct = 0x6877 
[   31.021437] usbcore: registered new driver rt73
[   43.098532] rausb0: no IPv6 routers present
```Obviously I may have missed some things. Thanks again NickB!

dustmote


**---update**
sound comes out of both my headphones and the laptop speakers...
doesn't it usually stop playing from the laptop speakers when you plug in headphones?

---

### Post by jsweds on 2007-01-15
> **dustmote said:**
> 
**---update**
sound comes out of both my headphones and the laptop speakers...
doesn't it usually stop playing from the laptop speakers when you plug in headphones?

On this laptop, the speakers need to be controlled by software.  I've read about someone uninstalling the sound drivers in Windows and the speakers would not shut off when the headphones were plugged in.  Unfortunately, I don't know how to deal with this and came here looking to see if anyone had the answer.

Also, has anyone been able to get WPA wireless networks to work?

---

### Post by NickB on 2007-01-15
> **dustmote said:**
> I booted the computer. Did dmesg. Copied its output into gedit. Plugged in the mouse. Waited a minute. Did dmesg. Copied its output into another gedit tab. They were the same.
That is a problem.  I've never had a problem using USB devices since removing the ohci controller.  Not that it ever worked for me before that anyway.  Weird; I don't know what to tell you.
> **dustmote said:**
> sound comes out of both my headphones and the laptop speakers...
doesn't it usually stop playing from the laptop speakers when you plug in headphones?
There is special software running in windows that monitors headphones being inserted into the jack. The ALSA driver doesn't currently send these events to the ACPI manager or dbus, though it would be nice if there was a way to monitor it so you could mute the speakers.  You can do this manually using alsamixer, a command line utility; you will see a mixer for "Front Speakers" and you can mute it when you have headphones in.

Nick

---

### Post by NickB on 2007-01-15
My "Powersaver mode" package in [http://www.ubuntuforums.org/showpost.php?p=1893382&postcount=21](http://www.ubuntuforums.org/showpost.php?p=1893382&postcount=21) has been updated to version 0.2.  This should stop the tray monitor from responding to an AC event, and I've changed the arch to all, so i386 or amd64 can use the same package.

Nick

---

### Post by dustmote on 2007-01-16
> **NickB said:**
> That is a problem.  I've never had a problem using USB devices since removing the ohci controller.  Not that it ever worked for me before that anyway.  Weird; I don't know what to tell you.I tried that again, this time without blacklisting ohci_hcd, and did that thing with dmesg before it disabled IRQ #7 and got it to show some difference in he output.```
[   74.062649] Bluetooth: RFCOMM socket layer initialized
[   74.062673] Bluetooth: RFCOMM TTY layer initialized
[   74.062677] Bluetooth: RFCOMM ver 1.7
```Was the end of the output before, and then I plugged in the mouse and tried it again.```
[   74.062677] Bluetooth: RFCOMM ver 1.7
[  115.733939] ohci_hcd 0000:00:0b.0: wakeup
[  116.125884] usb 2-2: new low speed USB device using ohci_hcd and address 2
[  116.335557] usb 2-2: configuration #1 chosen from 1 choice
[  116.504944] usbcore: registered new driver hiddev
[  116.516565] input: Logitech Trackball as /class/input/input3
[  116.516659] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:0b.0-2
[  116.516674] usbcore: registered new driver usbhid
[  116.516678] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
```YAY! The mouse works! Now, this didn't work at all the first time (when ohci_hcd was disabled). This leads me to believe that either (a) ohci is necessary or (b) the other drivers aren't stepping up when we disable ohci.

The only problem, as I see it, is the irq thing, where irq #7 gets disabled after awhile. I'm going to to breakfast and see if it's disabled when i get back.

**update**
Predictably, the IRQ 7 disabled message was on all my terminal windows when I got back. Did dmesg. This is what I got.```

[ 1609.045904] irq 7: nobody cared (try booting with the "irqpoll" option)
[ 1609.045910] 
[ 1609.045912] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[ 1609.045937]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff880bebb8>{:usbcore:usb_hcd_irq+40}
[ 1609.045979]        <ffffffff802b6190>{__do_IRQ+224} <ffffffff802737e2>{do_IRQ+66}
[ 1609.045993]        <ffffffff80271f00>{default_idle+0} <ffffffff80265d08>{ret_from_intr+0} <EOI>
[ 1609.046007]        <ffffffff80232690>{unix_poll+0} <ffffffff80271f29>{default_idle+41}
[ 1609.046026]        <ffffffff8024ecfe>{cpu_idle+158} <ffffffff8027d34d>{start_secondary+1165}
[ 1609.046058] handlers:
[ 1609.046060] [<ffffffff880beb90>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 1609.046082] Disabling IRQ #7
[ 2341.894846] usb 2-2: USB disconnect, address 2
[ 2344.504540] ohci_hcd 0000:00:0b.0: IRQ INTR_SF lossage
[ 2344.682530] ohci_hcd 0000:00:0b.0: bad entry 1fdf0001
```

---

### Post by dustmote on 2007-01-16
> **NickB said:**
> You can do this manually using alsamixer, a command line utility; you will see a mixer for "Front Speakers" and you can mute it when you have headphones in.Now sound doesn't come out of my headphone jack. Ever. It's listed as "off" in alsamixer. How come everything I do in linux breaks something else?

---

### Post by NickB on 2007-01-17
> **dustmote said:**
> Now sound doesn't come out of my headphone jack. Ever. It's listed as "off" in alsamixer. How come everything I do in linux breaks something else?
Mine was like that; it was really just muted, and you can mute/unmute it the same way you do with the speakers.  And to be fair, this laptop is an engineering disaster.  How it even got UL approval is beyond me.  I'm just happy linux runs on it as well as it does.

Nick

---

### Post by jabeez on 2007-01-17
Ok, I got this laptop a bit ago and am having a ridiculously hard time getting the damn graphic driver working. I specifically sought a laptop with nvidia graphics because all past experience with linux said ATI=Bad, Nvidia=Not as bad. Lo and behold my first nvidia chip and it's been more of a PITA than any of my ATI installs. The method at the beginning doesn't work because that source gives a 404 not found every time. I've tried many others including envy and NOTHING will work. Whatta joke, any help?????

---

### Post by Joshua on 2007-01-17
Sorry to ask this again, but I never got a response the first time.  I've gotten the microphone to work under Windows, but I'm having trouble under Ubuntu.  Anyone have any ideas?

---

### Post by lythandrel on 2007-01-17
Any luck with the albertomilone repository?
 I woud love to get all the entire howto workig lon a char.

---

### Post by jabeez on 2007-01-18
No luck yet, still 404 not found, and every time I try the regular glx from the repos they don't work so at this point I'm at a standstill and irritated,

---

### Post by NickB on 2007-01-18
Have you tried the process at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ?

Nick

---

### Post by jabeez on 2007-01-18
Yeah I tried pretty much every method I could find on the forums, but I finally found an updated repository ([http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)) and it worked like a charm. Thanks for the guide, I went on to get pretty much everything else working great. I do have a question about Beryl though, I installed it and it doesn't seem to do anything? I open the configuration manager and change stuff but nothing happens. I'm running Kubuntu, does that make a difference? Anywho, thanks again.........

---

### Post by lythandrel on 2007-01-19
> **jabeez said:**
> Yeah I tried pretty much every method I could find on the forums, but I finally found an updated repository ([http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)) and it worked like a charm. Thanks for the guide, I went on to get pretty much everything else working great. I do have a question about Beryl though, I installed it and it doesn't seem to do anything? I open the configuration manager and change stuff but nothing happens. I'm running Kubuntu, does that make a difference? Anywho, thanks again.........

Jabeez - thank you for your diligence.  I work a long day, so most of my looking for repositories doesn't happen until the weekends.  You've just saved me (and many others) a LOT of time.  Just need to get the howto updated with those repositories and all of us 2370 owners are all set.  :)

---

### Post by dustmote on 2007-01-19
> **NickB said:**
> Mine was like that; it was really just muted, and you can mute/unmute it the same way you do with the speakers.  And to be fair, this laptop is an engineering disaster.  How it even got UL approval is beyond me.  I'm just happy linux runs on it as well as it does.

Nick

I'm not sure I know what UL approval is, but it seems about right that things with this laptop are a little screwy. Everything works in windows though, so I guess I'll just use that for the things I can't get working in linux.

----
That nVIDIA repo that kept giving people a 404 is easy to get around (this is what I did when I encountered the same problem). When you find old faqs or consistently get 404s with a repository it's probably best to check the top domain in the url for it. If the top domain is still good, and they still have a repository running the almost ALWAYS have links to it. All I did was go to albertomilone.com and buzz around looking for the repo link. Just a little extra hunting, and you can get that stuff.

---

### Post by NickB on 2007-01-20
OK, I've got the ohci_hcd module working correctly.  Apparently the ehci_hcd won't handle USB 1.1 devices, only 2.0 devices.  First, take ohci_hcd out of your /etc/modprobe.d/blacklist file.  Then, make sure these options are on your /boot/grub/menu.lst on the kopt_2_6 line:

noapic acpi_irq_balance acpi_isa_irq=7

Finally, run update-grub (as root or using sudo).  Then reboot.  I hope that works for you, it was a real pain to find this solution!!

Nick

---

### Post by dustmote on 2007-01-22
that worked like a charm... thanks nickb .. everything works on my system for the most part... i never got the headphone jack working, but that's ok because my desk looks nicer without the speakers on it... also wireless doesn't work, but that's just because i'm waiting for the connection manager to ge better at wpa :D

so thanks!

---

### Post by lythandrel on 2007-01-26
Quick word of advice for all.  PLEASE use the proprietary nvidia drivers.  All the odd glitches I've had with the xorg nv driver have disappeared.  It's a beautiful thing.  Dragonfyre, you may want to try putting this link in your howto, since the link for them you have is null.  You can still import the gpg keys from there.  It's also a hell of a lot faster.

In /etc/apt/sources.list add the following line.

```
#NVIDIA Proprietary Drivers
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```

Unlike deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/
it does not give a 404, and changing this should make an easier experience for all attempting to use the howto or do further upgrades later on.

**Dragonfyre**, thank you AGAIN for all the time you put in, it has made the install go a lot easier, for all of us who own this lovely little machine.

Cam..

---

### Post by NickB on 2007-01-26
> **lythandrel said:**
> In /etc/apt/sources.list add the following line.

```
#NVIDIA Proprietary Drivers
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```
And if you choose to run amd64 instead of i386, just replace the "32" with "64" and it'll work for you, too.

Nick

---

### Post by jabeez on 2007-01-27
So anyone have any ideas if something needs to be tweaked for Beryl on Kubuntu? I installed it as per this guide and I've got the theme manager and beryl settings, they just don't seem to do anything??? Is there something more you have to do to turn it on?

---

### Post by dragonfyre13 on 2007-01-29
> **lythandrel said:**
> Quick word of advice for all.  PLEASE use the proprietary nvidia drivers.  All the odd glitches I've had with the xorg nv driver have disappeared.  It's a beautiful thing.  Dragonfyre, you may want to try putting this link in your howto, since the link for them you have is null.  You can still import the gpg keys from there.  It's also a hell of a lot faster.

In /etc/apt/sources.list add the following line.

```
#NVIDIA Proprietary Drivers
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```

Unlike deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/
it does not give a 404, and changing this should make an easier experience for all attempting to use the howto or do further upgrades later on.

**Dragonfyre**, thank you AGAIN for all the time you put in, it has made the install go a lot easier, for all of us who own this lovely little machine.

Cam..

Thanks for recognising me. Just trying to do my part. I updated the Howto as per your request.

Sorry all for not being as active as I had been. I'm actually running into wireless issues, if you can believe it, but it isn't with the laptop. It's with the router. Apparently the Linux based OpenWRT doesn't give a DHCP lease to ANY of my Linux PCs. It works fine with the one windows test box I have though.


EDIT: Got another router. Working great now! Should be getting on more often, and figuring out the few remaining issues.

---

### Post by dragonfyre13 on 2007-01-29
> **jabeez said:**
> So anyone have any ideas if something needs to be tweaked for Beryl on Kubuntu? I installed it as per this guide and I've got the theme manager and beryl settings, they just don't seem to do anything??? Is there something more you have to do to turn it on?

Right click on the ruby in the task bar, and select to use the window manager Beryl. You aren't using it yet is likely the issue.

---

### Post by bigbridges06 on 2007-01-29
Hey Guys. Sorry it's been a while, but I wanted to let ya'll in on some amazing things that I have found. I currently have come across the Linux distro: PCLinuxOS. Sorry if that offends any of ya. LOL. Anyway, for the not as educated Linux user as myself, It has been quite easy to set up. Everything loads from the LiveCD. There are only two issues that I have come across. The first one, I could connect to my WPA protected wireless network quite easily. The only thing I had to do was using the already installed ndiswrapper and change the driver to my windows driver on the windows partition. My problem is that I have to do this every time I restart the computer. It's not hard nor long of a proccess; just an inconvenience. The other is that my soundcard works fine; it's just that whenever I plug in the headphones or try to mute it, it doesn't mute or send the music to the headphones. It simply plays the sound from the laptop speakers. Any assistance would be greatly appreciated. Thanks guys.

---

### Post by dragonfyre13 on 2007-02-02
> **bigbridges06 said:**
> Hey Guys. Sorry it's been a while, but I wanted to let ya'll in on some amazing things that I have found. I currently have come across the Linux distro: PCLinuxOS. Sorry if that offends any of ya. LOL. Anyway, for the not as educated Linux user as myself, It has been quite easy to set up. Everything loads from the LiveCD. There are only two issues that I have come across. The first one, I could connect to my WPA protected wireless network quite easily. The only thing I had to do was using the already installed ndiswrapper and change the driver to my windows driver on the windows partition. My problem is that I have to do this every time I restart the computer. It's not hard nor long of a proccess; just an inconvenience. The other is that my soundcard works fine; it's just that whenever I plug in the headphones or try to mute it, it doesn't mute or send the music to the headphones. It simply plays the sound from the laptop speakers. Any assistance would be greatly appreciated. Thanks guys.

Well, normally I would say go to the PCLinuxOS forums for it, but what I would try is to make sure your headphones are not muted. (use alsamixer)

Second, you will need to describe the issue with ndiswrapper.You are trying to point it to the windows drive. Do you have to manually mount the windows drive on boot? What happens when you boot it up? Do you have to re-identify the driver?

---

### Post by bigbridges06 on 2007-02-03
Hey dragonfyre,
       Thanks for the advice on the first issue with the sound; however, not 10 minutes after I got through writing the post, I toyed with it and essentially did what you wrote. I just didn't that I was doing it.
       As to the second issue: It boots fine and loads the desktop fine. However, everytime I reboot I must respecify where the driver is. I think that the OS is automatically loading another driver for it  because it keeps telling me "Are you sure you want to use the ndiswrapper driver instead?" and I tell it yes. After I respecify the driver, it works fine. Its just that I have to do it every reboot. I may have to blacklist that other driver, but I don't how. I'll try the PCLinuxOS site as well.
Thanks ya'll

---

### Post by mrajaa on 2007-02-09
I followed the tips on this thread and have got almost everything working.  There are a couple of things that have been bothering me and make me boot into the windows partition.  I would love to have these fixed and forget windows forever.

I have the 64 bit version of ubuntu installed along with firefox 64.  To get the flash plugin working, I used nspluginwrapper following these instructionsl: 

[http://plugindoc.mozdev.org/linux-amd64.html](http://plugindoc.mozdev.org/linux-amd64.html)

So now I can watch flash videos and games. I next wanted to install the realplayer plugin to listen to embedded realplayer music from sites such as [http://www.musicindiaonline.com/music/cl/11/](http://www.musicindiaonline.com/music/cl/11/)

But after installed the realplayer plugin using nspluginwrapper, I am still unable to get the freaking music to play.  My realplayer plugin version  is recognized as 6 although I installed version 10, and I keep getting the message "Error: Methods Missing".  Has anybody come across this problem and know a work around (mplayer plugin doesnt work either)?   Thanks .

-raj

---

### Post by jabeez on 2007-02-11
Anyone install the latest kernel update? I've had adepts notifier staring at me for a couple days but I'm a bit leary of updating and breaking stuff since as of right now everything is working and working well, I'm really digging this lil laptop Kubuntu-fied. Anyone else run Kubuntu? I'm not sure how to lock a version to get rid of the update notifier. Cheers!

---

### Post by dragonfyre13 on 2007-02-15
Nick,

I get this output when starting your app. I haven't been able to use the laptop for a while due to wireless issues (router stuff) so this is pretty well changed since last time. A bunch of stuff changed on the system, and then I noticed there was no tray icon. Here's the output:
```

Traceback (most recent call last):
  File "/usr/bin/powersave-trayicon", line 89, in ?
    base.SetState(file('/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq').read() != file('/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq').read(), False)
IOError: [Errno 2] No such file or directory: '/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq'

```

---

### Post by NickB on 2007-02-16
> **dragonfyre13 said:**
> Nick,

I get this output when starting your app. I haven't been able to use the laptop for a while due to wireless issues (router stuff) so this is pretty well changed since last time. A bunch of stuff changed on the system, and then I noticed there was no tray icon. 

Did you upgrade the kernel?  It may be that the path to the cpu frequency controls in /sys changed.  Or maybe /sys isn't mounted at all.

Let me know which it looks like.

Thanks,
Nick

---

### Post by dragonfyre13 on 2007-02-16
> **NickB said:**
> Did you upgrade the kernel?  It may be that the path to the cpu frequency controls in /sys changed.  Or maybe /sys isn't mounted at all.

Let me know which it looks like.

Thanks,
Nick

Well, I know sys has mounted fine. I did upgrade the kernel, but I removed, and reinstalled your package, and it didn't help. What info would I be looking for to tell you if the frequency controls in sys have changed?

---

### Post by NickB on 2007-02-17
dragonfyre,

You're specifically looking for /sys/devices/system/cpu/cpu0/cpufreq where all the frequency information is set/read.  For what it's worth, I just upgraded, and besides losing the nvidia driver, everything seems to be working fine, but I am on amd64 and IIRC you are on i386.

You're not using xen, are you?  Or some other kernel that doesn't have cpu frequency scaling compiled in?  That would explain it.

Nick

---

### Post by Joshua on 2007-02-17
> **jabeez said:**
> Anyone install the latest kernel update? I've had adepts notifier staring at me for a couple days but I'm a bit leary of updating and breaking stuff since as of right now everything is working and working well, I'm really digging this lil laptop Kubuntu-fied. Anyone else run Kubuntu? I'm not sure how to lock a version to get rid of the update notifier. Cheers!

I know this is old, and I hope this hasn't already been answered, but I couldn't find an answer, and I think it's kind of important for this laptop.  I upgraded and now I've got both the 2.6.17-10 and 2.6.17-11 kernels in my GRUB menu, but when I boot into the 2.6.17-11 kernel I loose the proprietary nVidia drivers and the wireless functions.  This is easy to overcome by selecting the 2.6.17-10 kernel at boot (or setting it to the default, or removing the newer one), but there should be a more proper way of overcoming this to use the new kernel, right?

I assume I'd need to recompile the wireless drivers for the new kernel, but how would that affect the old kernel?  And do I need to uninstall what I've got before doing anything?  Also, Alberto Milone's repository instructions say that you need to re-install the nvidia drivers when you upgrade the kernel, but I've done that and I still get an "API mismatch" error.  Something about the kernel module version not matching the driver version...  Anyway, it looks to me like maybe the problem is that Mr. Milone hasn't yet included a required package that matches the new kernel - or something.  I'm not a linux guru so take all that with a grain of salt.

Anyway, with all the non-out-of-the-box configuration that can go into this laptop to get things working (especially with the wireless drivers) it would be nice if someone updated these instructions to describe how to maintain it with normal updates.

---

### Post by NickB on 2007-02-18
> **Joshua said:**
> when I boot into the 2.6.17-11 kernel I loose the proprietary nVidia drivers and the wireless functions.  This is easy to overcome by selecting the 2.6.17-10 kernel at boot (or setting it to the default, or removing the newer one), but there should be a more proper way of overcoming this to use the new kernel, right?
As of yesterday the updated nVidia driver hadn't shown up yet, but the envy script available from the same site works great.  That's what I used.

> **Joshua said:**
> I assume I'd need to recompile the wireless drivers for the new kernel, but how would that affect the old kernel?  And do I need to uninstall what I've got before doing anything?
Yes on 1, no on 2.  Compiling against the new kernel and installing it in the appropriate /lib/modules directory won't impact the old kernel.

> **Joshua said:**
> Also, Alberto Milone's repository instructions say that you need to re-install the nvidia drivers when you upgrade the kernel, but I've done that and I still get an "API mismatch" error.  Something about the kernel module version not matching the driver version...
Correct... the drivers on his site have not been compiled against the new kernel yet.  As mentioned above, try the envy package he put together.  I use it to get and build the driver, but I don't let it touch my xorg.conf.

Hope that helps,
Nick

---

### Post by dragonfyre13 on 2007-02-19
> **NickB said:**
> Correct... the drivers on his site have not been compiled against the new kernel yet.  As mentioned above, try the envy package he put together.  I use it to get and build the driver, but I don't let it touch my xorg.conf.

Actually, I'm thinking I'll update the tutorial to use envy, as it seems easier, and more up to date. Also there are so many issues with this repository, it seems the better way to go. Opinions?

---

### Post by NickB on 2007-02-19
I thought the envy script was extremely easy to use and the installation went flawlessly.  I don't know how well the xorg.conf modification that it does works for new users, since I already had a config I was happy with, but I bet it uses the nVidia utility to do it.

The script is pretty up to date (only a week or so old since last update).  I am personally going to use it as the preferred method to update to the latest drivers rather than depending on someone to package it, and I'm pretty sure a newbie would have NO problems following the simple menu.  Just make sure you note to run it from the console and not from within X.

Nick

---

### Post by pjones0404 on 2007-02-20
I would first like to say that this thread is amazing. I really appreciate all the hardwork you guys have done to make my life easier w/ my new laptop.  =D> 

I have a few questions about the nvidia driver and the effect it has on my kernel. i followed the instructions here and when i update to the new driver it creates a new kernel listing in grub. when selecting this new listing i have the new nvidia driver, but i lose the wireless card driver (i do understand why) and i also lose the dual core functionality in the system monitor app. 

when i restarted x after installing the driver i get an xserver error and can not get a display in the old kernel w/ out running reconfigure xserver-xorg and choosing the nv driver. the new kernel boots fine w/ the new driver but i have the issue w/ dual core support i mentioned before. 

should i be using the new kernel now? i don't know much about this as you can probably tell.

i am also having an issue w/ beryl as well. when i install it and open an application i do not have the ability to move the windows around the screen or resize them. in fact the max/min/close icons in the upper right corner are missing all together. this is not that important just throwing it out there in case it is an easy fix.

thanks again for all you do.  :KS

---

### Post by dragonfyre13 on 2007-02-20
> **pjones0404 said:**
> 
i am also having an issue w/ beryl as well. when i install it and open an application i do not have the ability to move the windows around the screen or resize them. in fact the max/min/close icons in the upper right corner are missing all together. this is not that important just throwing it out there in case it is an easy fix.

thanks again for all you do.  :KS

I **JUST, JUST** went through this issue with a new ubuntu setup I'm helping a co-worker friend out with.

Emerald isn't working. You need to add something to the XORG.Conf file under the device section. Lemme get back to you in a few with what it was. I need to SSH in over lunch anyway to fix an issue he's having with beryl not handling his screensaver right. (locks up when the screensaver comes on. It's an OpenGL screensaver, so I think that is what is causing it.)

---

### Post by dragonfyre13 on 2007-02-20
> **pjones0404 said:**
> I would first like to say that this thread is amazing. I really appreciate all the hardwork you guys have done to make my life easier w/ my new laptop.  =D> 

Hehe. Always good to meet a fan... ^_^

Thanks for the compliment. I'm sure Nick appreciates it too. He's helped out as much as I have.

> **pjones0404 said:**
> 
I have a few questions about the nvidia driver and the effect it has on my kernel. i followed the instructions here and when i update to the new driver it creates a new kernel listing in grub. when selecting this new listing i have the new nvidia driver, but i lose the wireless card driver (i do understand why) and i also lose the dual core functionality in the system monitor app. 

when i restarted x after installing the driver i get an xserver error and can not get a display in the old kernel w/ out running reconfigure xserver-xorg and choosing the nv driver. the new kernel boots fine w/ the new driver but i have the issue w/ dual core support i mentioned before. 

should i be using the new kernel now? i don't know much about this as you can probably tell.

It looks like it installed a new kernel too. That's not supposed to happen. If it installed the i386 kernel versus the generic, it doesn't have smp support, and thus no dual CPUs. Also, after a kernel update, sometimes it breaks the Nvidia driver (anyone want to offer input into why, and how this can be fixed?)

Reinstall the nvidia driver (apt-get remove, then apt-get install again) and then restart gdm (sudo /etc/init.d/gdm restart) Make sure it edits Xorg for you (it should be an option during installation.)

search synaptic for the linux kernel, and make sure you have the generic kernel selected, and remove anything with 386, 486, 686, or k7 in it as far as kernels go. Reboot. You may have to install the nvidia drivers again.

Also, follow the HOWTO specifically. Your wireless shouldn't break if you install it from source like in the HOWTO when you install the graphics drivers.

---

### Post by dragonfyre13 on 2007-02-20
> **dragonfyre13 said:**
> I **JUST, JUST** went through this issue with a new ubuntu setup I'm helping a co-worker friend out with.

Emerald isn't working. You need to add something to the XORG.Conf file under the device section. Lemme get back to you in a few with what it was. I need to SSH in over lunch anyway to fix an issue he's having with beryl not handling his screensaver right. (locks up when the screensaver comes on. It's an OpenGL screensaver, so I think that is what is causing it.)

OK, I got it. Add these lines to the device section underneath everything else that is there:

```
Option "AllowGLXWithComposite" "true"
Option "AddARGBGLXVisuals" "True"
```

That should fix your issue. Also, make sure that triple buffer is not enabled, We also ran into an issue (granted, he had twinview enabled) where any OpenGL apps would majorly freeze the system with beryl and triplebuffer enabled.

The default on this is disabled, so if you don't see anything about triplebuffer in xorg.conf, you're fine. If you do, put a # sign in front of it to comment it out.

---

### Post by dragonfyre13 on 2007-02-20
> **dragonfyre13 said:**
> OK, I got it. Add these lines to the device section underneath everything else that is there:

```
Option "AllowGLXWithComposite" "true"
Option "AddARGBGLXVisuals" "True"
```

That should fix your issue. Also, make sure that triple buffer is not enabled, We also ran into an issue (granted, he had twinview enabled) where any OpenGL apps would majorly freeze the system with beryl and triplebuffer enabled.

The default on this is disabled, so if you don't see anything about triplebuffer in xorg.conf, you're fine. If you do, put a # sign in front of it to comment it out.

Also, check this out.

Option "UseEvents" "True"

Supposedly it's supposed to fix things if you are running into massive CPU usage sometimes, and very little at other times, while doing the same thing.

I'm blogging about it right now. [http://www.dragonfyre13.com/blog](http://www.dragonfyre13.com/blog)

---

### Post by dragonfyre13 on 2007-02-21
> **dragonfyre13 said:**
> 
Supposedly it's supposed to fix things if you are running into massive CPU usage sometimes, and very little at other times, while doing the same thing.

Hmm, seems it may not improve things as much as I had hoped. More info at the blog.

---

### Post by pjones0404 on 2007-02-25
i am having some serious issues setting up the wireless on this notebook. :confused: i have followed the steps in this thread but i am still having issues. i am currently connecting to my home network using a wireless bridge and it works fine. 

here is my output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=11 MHz  Bit Rate=1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=46/100  Signal level:-82 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

here is netstat -rn :

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 rausb0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 rausb0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0


any help that you could provide would be greatly appreciated.

---

### Post by dragonfyre13 on 2007-02-26
> **pjones0404 said:**
>  any help that you could provide would be greatly appreciated.

Can you do the following for me?

paste the output of these files:

/etc/Wireless/RT73STA/rt73sta.dat
/etc/network/interfaces

Then execute these commands, and copy the output here:

ls /lib/modules/`uname -r`/extra
ls /etc/Wireless/RT73STA


Also, let me know what kind of encryption, if any, is on your wireless network. Can you see any networks when using the connection manager application? 

Make sure when you are first testing this, that wireless encrytion is off. That means no WEP or WPA. Then, once that is working introduce encryption, after setting up connection manager. It shouldn't have any problems handling it once setup, but it makes it much easier to troubleshoot if there is no encryption when trying it.

---

### Post by pjones0404 on 2007-02-27
Here is the output that you had requested.

[COLOR="Red"] /etc/Wireless/RT73STA/rt73sta.dat[/COLOR]

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
NetworkType=Infra

[COLOR="Red"]
 /etc/network/interfaces[/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp  

auto rausb0
iface rausb0 inet dhcp
wireless-essid home
wireless-key 0123456789

[COLOR="Red"]
ls /lib/modules/`uname -r`/extra[/COLOR]
rt73.ko
[COLOR="Red"]
ls /etc/Wireless/RT73STA[/COLOR]
rt73.bin  rt73sta.dat


After some troubleshooting on my own i have came to the conclusion that i **can** connect to unsecured networks around me but not to my network that is using WEP. in fact it will auto connect to the unsecured networks. i have tried to run the following:

sudo iwconfig rausb0 essid home key 0123456789

 it shows the correct essid when i run iwconfig again but i can not browse nor ping at all. I have tried entering the network settings under system-admin-network to input the wep info and also edited the /etc/networks/interfaces manually and entered the info needed but neither work. 


Not sure if this helps but this is the output from sudo ifup rausb0 **after** running sudo iwconfig rausb0 essid home key 0123456789 **and** sudo ifdown rausb0. it looks like the dhcp is not working, but other laptops are connected to my network using dhcp. 

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device rausb0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.
There is already a pid file /var/run/dhclient.rausb0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:13:d3:82:57:c9
Sending on   LPF/rausb0/00:13:d3:82:57:c9
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


In regards to the connection manager listed in step 10 of the walk through. i am having issues w/ that as well. i can install the .deb package and that is fine, once i open the application i see the networks that are available but i can not click on "setup network" or "connect". The refresh, preferences, and quit are "clickable" but nothing else.

i am currently posting this using the unsecured network in my area so i know that the driver for the card is working i just cant seem to determine what is causing the issue w/ my network. 


thanks for the help.   :)

---

### Post by dragonfyre13 on 2007-02-27
> **pjones0404 said:**
> 
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device rausb0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.

This shows that there is an issue with it trying to perform these actions while it is down. I have the answer for this somewhere, but I'll need to do some digging.

It looks like you are working all except for WEP, which is good. That means that drivers are installed correctly, and you are 95% of the way there. We just have to get WEP working which generally is just a configuration option that needs to be changed.



> **pjones0404 said:**
> In regards to the connection manager listed in step 10 of the walk through. i am having issues w/ that as well. i can install the .deb package and that is fine, once i open the application i see the networks that are available but i can not click on "setup network" or "connect". The refresh, preferences, and quit are "clickable" but nothing else.

This is something that I would post in that forum. Let's get your WEP working first, and then you should post a bit of info there, and resolve the issue with them. Likely there is an issue with the current setup, and this will be fixed when we fix WEP, but if not, they have thier own support thread.



At this point, you have your wireless card working. You also have your drivers, and installation done correctly, and everything seems to be setup correctly. You just need to tweak configuration, something I'll revisit when I have a bit more time. Right now I'm at work, so I'll deal with this in a bit.

---

### Post by mrajaa on 2007-02-27
Does anybody know what modifications are needed to the xorg.conf file to get dual monitors working for this laptop.  I was planning to connect to a LCD monitor and have the desktop pan both the laptop screen and the monitor.

Thanks in advance.

---

### Post by dragonfyre13 on 2007-02-28
> **mrajaa said:**
> Does anybody know what modifications are needed to the xorg.conf file to get dual monitors working for this laptop.  I was planning to connect to a LCD monitor and have the desktop pan both the laptop screen and the monitor.

Thanks in advance.

You are looking for enabling twinview. You could simply use Xinerama, which is arguably easier to setup, but I would definately suggest twinview, as you lose the xrandr extension if you use xinerama.

Also, you can enable something like twinview on demand or something. Maybe it's called autoconf. I don't remember. Basically, it automatically configures twinview when you plug in.

---

### Post by glenn69 on 2007-02-28
I have been running ubuntu on my 2370 laptop for about a month.  I set the wireless up as rausb0 as directed in the tutorial.  It has run fine.

Today, however, it just wasn't there anymore.  iwconfig showed no wireless adapters.  iwconfig rausb0 gives an error stating that the device does not exist.

How do i figure out what happened?
Is there a log file or something that will tell me what happened?

Thanks

---

### Post by dragonfyre13 on 2007-03-01
> **glenn69 said:**
> I have been running ubuntu on my 2370 laptop for about a month.  I set the wireless up as rausb0 as directed in the tutorial.  It has run fine.

Today, however, it just wasn't there anymore.  iwconfig showed no wireless adapters.  iwconfig rausb0 gives an error stating that the device does not exist.

How do i figure out what happened?
Is there a log file or something that will tell me what happened?

Thanks

The absolute first thing: Look on the front left, and make sure the switch is all the way to the right. This turns off your wireless card if it is to the left, and causes the issue you are talking about.

Second, reboot.
Third, post back here with how things went.

---

### Post by glenn69 on 2007-03-03
Yes, I did check that already.  The blue indicator light that shows that the wireless adapter is enabled is also lit.  So, that is not the problem.

What next ...

---

### Post by deadlydeathcone on 2007-03-08
I just wanted to add that I've been testing Suspend2 on this lappy, and suspend to ram amazingly enough works perfectly, although hibernation seems a bit iffy. I also recompiled and the DSDT to check for errors, and it turns out that there's a rather large one concerning syntax that seems to be causing havok. What it affects, though, I can''t tell.

Out of curiosity: has anyone tried this with Feisty yet? Mainly I'm curious if the included rt73 drivers are at all functional yet, as that the one thing I've been holding out on.

---

### Post by dragonfyre13 on 2007-03-09
> **deadlydeathcone said:**
> I just wanted to add that I've been testing Suspend2 on this lappy, and suspend to ram amazingly enough works perfectly, although hibernation seems a bit iffy. I also recompiled and the DSDT to check for errors, and it turns out that there's a rather large one concerning syntax that seems to be causing havok. What it affects, though, I can''t tell.

Out of curiosity: has anyone tried this with Feisty yet? Mainly I'm curious if the included rt73 drivers are at all functional yet, as that the one thing I've been holding out on.

I've actually got a suspend2 custom version of the kernel too, and had great experiences with suspend2ram. Like you said, suspend2disk is very bad though.

It isn't something for the faint of heart, but if you want to try something else that possibly breaks the system, and/or really want to play with suspends, it's a neat little modification that can do wonders.

---

### Post by dragonfyre13 on 2007-03-11
> **glenn69 said:**
> Yes, I did check that already.  The blue indicator light that shows that the wireless adapter is enabled is also lit.  So, that is not the problem.

What next ...

OK, just had the same issue. Apparently there is something with the newest kernel that breaks things with the driver. Let me know if anyone encounters this also.

Just do a make && make install in the src directory of RT73. It will rebuild and reinstall it. Then everything should be golden.

---

### Post by pwithem on 2007-03-29
Having trouble with the wireless setup.  I followed the directions and for the most part, everything worked fine.  But, when i do iwconfig, I get link quality = 0/100, although the other stuff checks out.  

Further, when I use the Wireless Assistant Wireless LAN manager, it can't connect, even though the network is not protected.   It has no problem seeing several local wireless networks.  I do a dmesg, and I for the last several lines, i get:

[17179749.940000] IPv6 over IPv4 tunneling driver
[17179760.576000] rausb0: no IPv6 routers present
[17179773.364000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17181385.952000] eth0: link up.
[17181385.956000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17181396.740000] eth0: no IPv6 routers present
[17181747.252000] eth0: no IPv6 routers present
[17181794.608000] rt73 driver version - 1.0.3.6
[17181804.944000] rausb0: no IPv6 routers present

what do it do?  thanks...

---

### Post by NickB on 2007-03-31
> **deadlydeathcone said:**
> Out of curiosity: has anyone tried this with Feisty yet? Mainly I'm curious if the included rt73 drivers are at all functional yet, as that the one thing I've been holding out on.
Yes, it more or less works, but cpu scaling is broken.  gaim is wonky.  sometimes the wireless interface doesn't come up, and you have to restart networking.  but it's usable.

IMO there's no reason to jump the gun and use the beta.  there's nothing significantly better that I've seen over edgy, if you have everything running.

Nick

---

### Post by NickB on 2007-04-08
Here are a few tips if you want to try upgrading to Feisty:

1. Remove any nvidia drivers you downloaded and/or compiled from non-ubuntu sources.  The nvidia driver that comes with Feisty is current and works well.

2. Remove any boot options, such as noapic and the irq routing options I mentioned earlier in this thread, if you're using them.  CPU scaling, for example, won't work with the noapic option, which is no longer required for kernel 2.6.20.

3. I haven't gotten any of the wireless drivers in the mainline kernel to work, but the latest sources from the CVS repository of the manufacturer work OK.  On amd64, at least, restarting the networking service is required after booting in order to get them to work.  NetworkManager doesn't work for amd64 either, so you have to manually configure in /etc/network/interfaces.  I have no idea about i386.

Good luck, YMMV and all that.  I'm also using the included version of beryl and it seems to work fine as well.  I haven't gotten anything significant working with kvm, but it seems like it would work if you knew what you were doing :)

Nick

---

### Post by decoherence on 2007-04-16
> wget [http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

this gives me 404 not found. the new location, at least where i got it from,

[http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

---

### Post by dragonfyre13 on 2007-04-17
> **decoherence said:**
> this gives me 404 not found. the new location, at least where i got it from,

[http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

Thanks. Updated to the new URL.

---

### Post by dragonfyre13 on 2007-04-17
> **NickB said:**
> Here are a few tips if you want to try upgrading to Feisty:

1. Remove any nvidia drivers you downloaded and/or compiled from non-ubuntu sources.  The nvidia driver that comes with Feisty is current and works well.

2. Remove any boot options, such as noapic and the irq routing options I mentioned earlier in this thread, if you're using them.  CPU scaling, for example, won't work with the noapic option, which is no longer required for kernel 2.6.20.

3. I haven't gotten any of the wireless drivers in the mainline kernel to work, but the latest sources from the CVS repository of the manufacturer work OK.  On amd64, at least, restarting the networking service is required after booting in order to get them to work.  NetworkManager doesn't work for amd64 either, so you have to manually configure in /etc/network/interfaces.  I have no idea about i386.

Good luck, YMMV and all that.  I'm also using the included version of beryl and it seems to work fine as well.  I haven't gotten anything significant working with kvm, but it seems like it would work if you knew what you were doing :)

Nick

I am working on getting a fiesty version of the guide, hopefully a few days after the release of 7.04 so that others can work with this on the newest version. Right now of course, I'm working on the wireless drivers and trying to get the 32 bit version up and working reliably. After I get 32 bit working better, I figure you can take it for the 64 bit stuff.

---

### Post by decoherence on 2007-04-21
> I am working on getting a fiesty version of the guide

Thanks for keeping this up, dragonfyre! I'm looking forward to the new guide.

---

### Post by decoherence on 2007-04-21
In Feisty (using kernel 2.6.20-15-generic) I had to make the following change to the ralink driver source to get it to compile

Line 2065 of the file ./RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c reads

> 	netdev->get_wireless_stats = rt73_get_wireless_stats;

change it to

> netdev->get_stats = rt73_get_wireless_stats;

due to a change in kernel headers

---

### Post by pjones0404 on 2007-04-21
i appreciate all of your hard work. i am looking forward to the guide for feisty as i dont think i will upgrade until i know that the wireles will work.

---

### Post by decoherence on 2007-04-22
I have the wireless working. I followed his current instructions verbatim, plus the one change I mention to the driver source code above, which you'd do just before typing "make" in dragonfyre's wireless instructions. It's working fine. I don't bother with NetworkManager, though. I'm not touching that thing until it's had another year's worth of development.

---

### Post by NickB on 2007-04-22
> **decoherence said:**
> In Feisty (using kernel 2.6.20-15-generic) I had to make the following change to the ralink driver source to get it to compile
Hm, I did NOT have to make that change, but that may be because I am pulling directly from CVS.

As far as NetworkManager, don't bother.  I've wasted far too much time with the ralink mods to add the driver to wpasupplicant and NetworkManager just to not have it work that it's simply not worth the trouble.  I was able to get WPA (PSK) working great, though, following the instructions in the source directory.

As a tip, you can put all the iwpriv commands that are required directly in your /etc/network/interfaces file using something like this:

auto rausb0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up iwpriv rausb0 set NetworkType=Infra
pre-up iwpriv rausb0 set AuthMode=WPAPSK
pre-up iwpriv rausb0 set EncrypType=TKIP
pre-up iwpriv rausb0 set SSID="YOURSSID"
pre-up iwpriv rausb0 set WPAPSK="your passphrase"
pre-up iwpriv rausb0 set SSID="YOURSSID"

As the docs say, yes, you DO need the SSID line twice.

Good luck!
Nick

---

### Post by decoherence on 2007-04-27
Indeed, I did not get mine from CVS but from the link posted in the guide, version 1.0.3.6. Hopefully ralink will update their page soon.

---

### Post by dragonfyre13 on 2007-05-03
Just as a quick update on the fiesty guide, I'm trying to get wireless working in a way that won't require you to pull from CVS, and won't require you to change source. If anyone has a package for the ralink driver that they want to upload, that would help considerably.

Also, since one of the things fiesty changed was hibernate and sleep, I need to get that working reliably, (which shouldn't be to hard. After that is done, the guide is set to be uploaded.

---

### Post by NickB on 2007-05-05
Hibernate seems to work perfectly out of the box, if a little slow, but much faster than under Edgy.  I have never gotten sleep (S3) to work with this laptop under linux.

---

### Post by AJimenez on 2007-05-11
Hello DragonFyre, I'm still looking for such WEP wireless configuration without any results. Mine is the same problem Wireless and all 95% done, but apparently is the WEP security wich is not working yet.
Furthermore, I have a big issue, with my averatec, it freezes without any reason, I tried the MemTest,wich is Ok, and still looking for more info, I'm rather a newbie, but I really want to get trough this problem and don't give it up.
Now, I'm working with the acpi=off but, i guess this is not the best option to solve the 'freezing' trouble. At least, my session lasts rather more than 10 minutes now.

I'm working with dapper, not with Edgy.

---

### Post by AJimenez on 2007-05-11
> **AJimenez said:**
> Hello DragonFyre, I'm still looking for such WEP wireless configuration without any results. Mine is the same problem Wireless and all 95% done, but apparently is the WEP security wich is not working yet.
Problem Solved, by adding this line to the rt73sta.dat

AuthMode=WEP

I know it's too trivial, keep in mind I'm newbie, and maybe other newbies over there.:) 
[/QUOTE]


Furthermore, I have a big issue, with my averatec, it freezes without any reason, I tried the MemTest,wich is Ok, and still looking for more info, I'm rather a newbie, but I really want to get trough this problem and don't give it up.
Now, I'm working with the acpi=off but, i guess this is not the best option to solve the 'freezing' trouble. At least, my session lasts rather more than 10 minutes now.

> I'm working with dapper, not with Edgy. 
I'll move to edgy, I want the beryl mode. And no longer support for dapper.:confused:

---

### Post by davef1m on 2007-05-13
I followed this guide with 6.10 with no problems.  Now I upgraded my wifes machine with 7.04 and can't seem to get wireless working again.  I think I got everything else I need to.

I got the 1.0.4 drivers from ralink, blacklisted the other drivers and it loads the new drivers (/proc/modules has rt73 215936 0 - Live 0xf8d01000)

iwconfig has:
    rausb0    RT73 WLAN  ESSID: off/any
                   Mode:Auto     Channel=1  Bit Rate:54 Mb/s
                   RTS thr: off    Fragment thr: off

I'm trying to get it working without and encryption (I'll VPN into the OpenBSD box later), so I'm ignoring any instuctions about WEP or WPA.  But when I try "sudo iwconfig rausb0 essid blahblah"  iwconfig still says "off/any".  When I do "sudo ifup rausb0" it doesn't get a lease.

What might I be missing?  Do I need the CVS drivers, or patch the current ones?

---

### Post by davef1m on 2007-05-14
OK, progress!
I think changing "wireless-essid whatever" in /etc/network/interfaces to:
pre-up iwpriv rausb0 set SSID="whatever" fixed it.
My router offers WEP and PSK{2} security modes.  Is WEP the best? 
Duh, WEP = Wired equiv. Psomething.  So is the PSK2 = WPA?
I got WEP working with the following in my /etc/network/interfaces:
```

auto rausb0
pre-up ifconfig rausb0 up
pre-up iwpriv rausb0 set NetworkType=Infra
pre-up iwpriv rausb0 set AuthMode=WEPAUTO
pre-up iwpriv rausb0 set EncrypType=WEP
pre-up iwpriv rausb0 set DefaultKeyID=1
pre-up iwpriv rausb0 set SSID="myessid"
pre-up iwpriv rausb0 set Key1="26hexhars"
pre-up iwconfig rausb0 ap 00:mac:addr:for:router

```
The last one is just to try and make sure it doesn't try the wrong place, and my router is set to only allow connections from the laptops mac addr.
Why did updating the firmware on my router change it's mac addr.?  It incremented the last byte.  What a pain.

BTW, I should have read the readme for the driver sooner.  It tells what commands "pre-up iwpriv rausb0 set" can use.

---

### Post by lythandrel on 2007-05-16
> **dragonfyre13 said:**
> Just as a quick update on the feisty guide, I'm trying to get wireless working in a way that won't require you to pull from CVS, and won't require you to change source. If anyone has a package for the ralink driver that they want to upload, that would help considerably.

If you want to get a good laugh, I went back to edgy because I needed wifi for a trip I took a few weeks ago.  Only problem with the edgy guide is for some odd reason, following the guide to the T, X got borked  when I reconfigured it.  (Perhaps due to having universe/multiverse enabled - never had a problem with it before)

I do realise that X works properly and picks up on the Nvidia driver with Feisty.  Is there any way that you can post just the wireless instructions as you go along?  It's a selfish request.  I can wait for hibernate and just about everything else, but the lack of wifi on feisty is making me batty.  I'd happily settle for CVS drivers, since unfortunately, any kernel past 2.6.17 makes you jump through hoops to get the RAlink driver working.   I do appreciate the work you're doing...  I'm just admitting that I'm getting a little frustrated.  Heck, I'll settle for the link to the CVS driver and go from there.  I can certainly wait for the rest of the guide. 

Thanks again for all your hard work.


Cam..

---

### Post by borahshadow on 2007-05-19
I was wondering how this and feisty work
I used this guide for some help (I didn't follow it to a T though)
I am currently running kubuntu edgy 32bit and the 2.6.17-10 generic kernel (I didn't want to mess with the wierd things the -11 was trying to make me do) with ndiswrapper and my wireless works great I have not tried wpa (I don''t have access to a network with wpa on it ) but the option is in knetworkmanager (which also works beautifully)

I was thinking about doing a clean install (getting rid of the windows xp MCE parition hogging up 12GB of my harddrive)
and also wondering about upgradeing to feisty while I was at it
I was also debateing whether to change to 64bit
I don't mind doing **some** hoop jumping but I want to be able to use flash java all the goodies in firefox etc 

so
1. should I go to feisty or not
2. about 64bit is it worth it I have noticed at time that this seems a **Little**slugish (bootup etc) would I notice a difference in 64bit? would that difference be enough to make me deal with all the problems (for lack of a better word) in 64bit (flash, java, w32codecs haveing compile problems on certain software, etc)
3. would I have to use a different windows driver with ndiswrpper? would ndiwrapper even work like it does now?
4. what about suspend to ram if that works in fesity I might want to go fesity but I have got by fine without suspend to ram
5. would feisty's new kernel add support for anything that 2.6.17 does not (like one of my desktops 2.6.17 does not support it'd brand new nvidia MCP61 mobo)besides k8 support which I have added in anyway ie would lm-sensors work or something
6. what about beryl on feisty I don't currently have it but I want to install it when I reinstall I think

ps when I turn off my computer I get the wierd bootspalash thing too but it does not bother me
pps. the other day my sound was wierd and I noticed that it normally detects the sound as HDA Nvidia but it had detected it as a realtek ALC or whatever I rebooted and everything was normal I don't think I had done any updates or anything but ai thought I'd throw that out there

any advice is appreciated

---

### Post by davef1m on 2007-05-23
Does anyone know what wireless-n cards will fit and work?

---

### Post by gnarayan on 2007-06-02
Hi, 

I'm running Ubuntu 7.04 on an averatec 2370 after I borked a zenwalk upgrade (damn shame it was working fine too - I just had to have the latest version of X) 

So far I've got the nvidia drivers, audio and dvd playback, flash and java and from the looks of things most everything else working except not quite the wireless

I got the latest RT73 drivers (1.0.4.0) and installed them and can apparently connect to an open network but I cannot do an

```
iwlist rausb0 scan
rausb0     Interface doesn't support scanning.

```

(this is also true if I try it with sudo btw)

to figure out what networks are present - this used to be possible with zenwalk and you'd then configure the connection with iwconfig and run dhcpcd to get an ip address. It shoul be the same other than dhcpcd -> dhclient yes?

Also can someone post their xorg.conf section for the synaptics touchpad driver especially if you have gsynaptics running to control the damn thing - I had the options for it written down someplace (I'd made a forum post about it on the averatec forums someplace but cant find it) but have gone and misplaced it and I need SHMConfig True and MaxTapMove or somesuch to control how sensitive the touchpad is I think.

Cheers,
-Gautham

---

### Post by lawr_rawr on 2007-06-03
Try this command to scan for networks:
```
iwpriv rausb0 get_site_survey
```

Then connect to the (open) network you want with:
```
sudo iwconfig rausb0 essid <name>
sudo iwpriv rausb0 set SSID=<name>
```

Check to make you're connected:
```
iwconfig rausb0
```

And then DHCP:
```
sudo dhclient rausb0
```

I haven't found a GUI connection manager that will recognize the card... has anyone else? I've found I can auto-associate with open wireless networks, but have to dhclient to get an address. I've scripted the connections for the secure networks I use most often (WPA at home and WEP at work) but it would be nice to have a GUI tool...

---

### Post by NickB on 2007-06-04
Gautham,

If you're still having problems, it's important that the interface has to be UP before you do a scan (or anything else), and you must be root (or equivalent) to do scanning.  If you see "Interface doesn't support scanning," then you need to do this:
```
sudo ifconfig rausb0 up
```
Hopefully that will get you going.

Good luck!
Nick

---

### Post by gnarayan on 2007-06-04
Thanks for the help guys - I currently type this from my WEP home network - I was missing the iwpriv commands 

so it seems I have to do this every time - 

```

sudo iwpriv rausb0 get_site_survey #just to scan  
sudo iwconfig rausb0 essid "mynewtork"
sudo iwpriv rausb0 set SSID="mynetwork"
sudo iwpriv rausb0 set EncrypType="WEP"
sudo iwpriv rausb0 set DefaultKeyID=1
sudo iwconfig rausb0 key myWEPkey
sudo iwpriv rausb0 set Key1=myWEPkey
sudo dhclient rausb0

```

Its likely that some of the above commands are redundant - it seems very odd that I have to essentially give it information twice using iwconfig and iwpriv and trying only one set does not work - very strange to me especially since the same laptop with the same wireless driver worked fine with just iwconfig previously. 

Will make this is a script for the home network - it would be nice to have a GUI tool - seems more the Ubuntu way and not a bad thing. Presumably I can also add the above commands to /etc/network/interfaces with a pre-up and it will just barf when I take it from home to school?


Nick - the interface should be up with the commands in /etc/network/interfaces but I tried bringing it up with ifconfig and ifup anyway - I still get the "interface doesn't support scanning" error with iwlist rausb0 scan  - iwpriv rausb0 get_site_survey works, though I'm not certain its list all the available networks yet - my desktop finds a few more and not all of them are weak. Again this is odd because iwlist rausb0 scan *used to work* albeit in a different distro.

And they say linux isn't ready for the desktop (jk jk jk - I've used it on and off since RH7) - I'm glad ralinktech at least has a linux driver - I've had some fun times with netgear cards and ndiswrapper and am certainly no guru.

---

### Post by NickB on 2007-06-04
> **gnarayan said:**
> Will make this is a script for the home network - it would be nice to have a GUI tool - seems more the Ubuntu way and not a bad thing. Presumably I can also add the above commands to /etc/network/interfaces with a pre-up and it will just barf when I take it from home to school?
In theory you can write a "mapping" that will allow you to work from different locations, but I have long since lost the source for a script that automates this.  Sorry I can't give more information, but I wanted to let you know that there is some hope, depending on your googling skills!

Nick

---

### Post by lawr_rawr on 2007-06-04
I believe that the interface will support scanning if you use the SerialMonkey RT73 drivers. I am using the drivers from Realtek's site. Got everything working, though, so I'm hesitant to try the other drivers... can anyone confirm?

I have thought about adding my home network settings to /etc/network/interfaces -- but I connect to home and work equally often, and I like the ability to auto-detect open networks (auto-associate with open wifi at coffee shops, etc). 

I am totally new to Linux but have been using it exclusively on my laptop for a couple weeks... much friendlier than other distros. I picked Ubuntu simply because of this nice in-depth howto for my 2370, but have since tried Fedora under VMware... I love love love my laptop again, and it doesn't take 3min to boot WinXP! :KS:KS:KS to everyone who has contributed to this thread.

---

### Post by dragonfyre13 on 2007-06-05
> **gnarayan said:**
> Hi, 

I'm running Ubuntu 7.04 on an averatec 2370 after I borked a zenwalk upgrade (damn shame it was working fine too - I just had to have the latest version of X) 

So far I've got the nvidia drivers, audio and dvd playback, flash and java and from the looks of things most everything else working except not quite the wireless

I got the latest RT73 drivers (1.0.4.0) and installed them and can apparently connect to an open network but I cannot do an

```
iwlist rausb0 scan
rausb0     Interface doesn't support scanning.

```

(this is also true if I try it with sudo btw)

to figure out what networks are present - this used to be possible with zenwalk and you'd then configure the connection with iwconfig and run dhcpcd to get an ip address. It shoul be the same other than dhcpcd -> dhclient yes?

Also can someone post their xorg.conf section for the synaptics touchpad driver especially if you have gsynaptics running to control the damn thing - I had the options for it written down someplace (I'd made a forum post about it on the averatec forums someplace but cant find it) but have gone and misplaced it and I need SHMConfig True and MaxTapMove or somesuch to control how sensitive the touchpad is I think.

Cheers,
-Gautham

Actually, making the wireless drivers usable, able to support scanning, and pluggable into a graphical interface is what I'm having so much trouble with for the 7.04 guide. Quite honestly, I haven't been able to put in the time needed, so I may post what I have soon and work on it with the rest of you. Until that point, I'm plodding away.

---

### Post by decoherence on 2007-06-07
For people who just can't seem to get rt73 drivers to work (me, since trying 1.0.4.0), I followed this howto with 7.04/x86 and got the serialmonkey driver working. Still no support for Network Manager, but I've been avoiding that thing this long, what's another release cycle or two?

[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")

This worked for me, but once you load the module (modprobe -v rt73), do an iwconfig to see what it named the interface. For me it was wlan1 for some reason.

---

### Post by dragonfyre13 on 2007-06-08
Anyone tried the drivers as of 5/09/07?

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

I never saw this page previously (went in a back way) so I've never tried these I don't think.

---

### Post by lawr_rawr on 2007-06-08
> Anyone tried the drivers as of 5/09/07?

Yes, I am using those 1.0.4.0 drivers from Ralink. Works with WPA and WEP. I have not tried the SerialMonkey drivers, but the Ralink drivers work fine for me.

---

### Post by lythandrel on 2007-06-09
> **dragonfyre13 said:**
> Actually, making the wireless drivers usable, able to support scanning, and pluggable into a graphical interface is what I'm having so much trouble with for the 7.04 guide. Quite honestly, I haven't been able to put in the time needed, so I may post what I have soon and work on it with the rest of you. Until that point, I'm plodding away.

I'd say post what you have so far, there are others here that seem to have gotten drivers working for wifi.  Even with the ealier howto, there was a proble with scan...  

Better to post what you have working, and get some additional help from those who have the wifi driver working properly...

Cam..

---

### Post by dragonfyre13 on 2007-06-11
> **lawr_rawr said:**
> Yes, I am using those 1.0.4.0 drivers from Ralink. Works with WPA and WEP. I have not tried the SerialMonkey drivers, but the Ralink drivers work fine for me.

Any chance they compile under Fiesty? (and work?) I know CVS works from ralink, but I also know there are some pretty big problems with it the last time I checked.

---

### Post by dragonfyre13 on 2007-06-11
> **lythandrel said:**
> I'd say post what you have so far, there are others here that seem to have gotten drivers working for wifi.  Even with the ealier howto, there was a proble with scan...  

Better to post what you have working, and get some additional help from those who have the wifi driver working properly...

Cam..

I think I'll do that then. Let me clean the guide up a bit, and I'll post what I am, and am not, having issues with.

---

### Post by gnarayan on 2007-06-12
> **dragonfyre13 said:**
> Any chance they compile under Fiesty? (and work?) I know CVS works from ralink, but I also know there are some pretty big problems with it the last time I checked.

The 1.04.0 drivers from ralink's website compile and work fine under Feisty - a few warnings IIRC but nothing fatal - I can recompile and pipe the output from 'make all' to a file for you to scrutinize if you like. Save for the caveat about 'iwlist scan' not working it seems fine - and the 'iwpriv get_site_survey' works fine for that. Have tested WEP but not WPA yet.

---

### Post by lawr_rawr on 2007-06-12
The Ralink 1.04.0 drivers compile and work for Feisty for me. I don't recall anything weird happening during the build... but a lotta text zoomed by pretty fast. Works with WEP and WPA, too.

I am working on a script to scan for wireless networks, let you select one, and connect. So far it works for WEP; I just need to work on it at home so I can get the WPA part right. Once I fix it for WPA, I'll post my script here.

(it's my first attempt at perl scripting so it will be ugly... but perhaps someone here can help me improve it)

---

### Post by lawr_rawr on 2007-06-13
Here is a really simple script for scanning and connecting to WEP/WPA wireless networks. I've tested it with WEP and WPA-PSK (TKIP and AES). It won't connect to open networks; if your laptop is like mine, it auto-connects to those.

I have only tried this with the Ralink 1.04.0 drivers. I have no idea how well it will work with other routers, but it connects to my Zyxel and my work's Linksys.

Save this script and chmod 755 it to make it executable. If your adapter name is not rausb0, change it in the line that says $ralink=rausb0. Then run sudo <path/to/script>. Enter the number of the wireless network you want, and enter your key.

```

#!/usr/bin/perl

$ralink = rausb0;
$count = -1;

open(SCAN, "iwpriv $ralink get_site_survey |");
   while (<SCAN>) {
   if ($count >= 1) {
      ($channel,$rssi,$ssid,$bssid,$enc,$auth,$type) = split;
      if ( $ssid ne "" ) {
      print "${count}: SSID: ${ssid}, Security: ${auth} (${enc})\n";
      }
   }
	$count += 1;
   }
close(SCAN); 

print "---------------------------------\nEnter number of network to connect to: ";
chomp($choice = <STDIN>);
$count = -1;

open(SCAN, "iwpriv $ralink get_site_survey |");
   while (<SCAN>) {
   if ($count == $choice) {
      ($channel,$rssi,$ssid,$bssid,$enc,$auth,$type) = split;
      print "Connecting to SSID: ${ssid}\n";

	if ($auth eq "WPA-PSK") {
		print "Enter passphrase: ";
		chomp($key = <STDIN>);
		`iwconfig $ralink essid $ssid`;
		`iwpriv $ralink set NetworkType=$type`;
		`iwpriv $ralink set AuthMode=WPAPSK`;
		`iwpriv $ralink set EncrypType=$enc`;
		`iwpriv $ralink set SSID=$ssid`;
		`iwpriv $ralink set WPAPSK=$key`;
		`iwpriv $ralink set SSID=$ssid`;
		`dhclient $ralink`;
		}
	elsif ($enc eq"WEP") {
		print "Enter key: ";
		chomp($key = <STDIN>);
		`iwconfig $ralink essid $ssid`;
		`iwconfig $ralink channel $channel`;
		`iwpriv $ralink set AuthMode=WEPAUTO`;
		`iwpriv $ralink set EncrypType=$enc`;
		`iwpriv $ralink set Key1=$key`;
		`iwpriv $ralink set SSID=$ssid`;
		`dhclient $ralink`;
	}
	else {
		print "Cannot connect to network.\n"
	}
	
   }
	$count += 1;
   }
close(SCAN); 

```

Any suggestions for improvement?

---

### Post by tregetour on 2007-06-27
When trying to follow your wonderful instructions to get the wireless working I received the following error when I entered the 'make' command:

```
~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function 'usb_rtusb_probe':
/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: 'struct net_device' has no member named 'get_wireless_stats'
/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable 'device'
make[2]: *** [/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/jdevries/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

any help would be much appreciated. thank you.

---

### Post by tregetour on 2007-06-27
I posted too soon. Using 1.0.4.0 instead of -.3.6 fixed the problem! Silly me.

---

### Post by borahshadow on 2007-06-27
I tried the new drivers when I installed feisty but I like network manager so I just blacklisted them and installed ndiswrapper like I did on edgy and works perfect so if you need a GUI like network manager you can just use ndiswrapper but other then that feisty work great

---

### Post by tregetour on 2007-06-29
Thank you! Everything works perfectly now. And a special thanks to lawr_rawr for the wireless script, very helpful. I love ubuntu mostly for these great forums.

---

### Post by Joshua on 2007-06-30
I just installed Feisty for AMD64.  Is anyone getting an ugly looking splash on shutdown?  Not on bootup - just on shutdown.  It looks like there are little horizontal lines taken out of the splash and moved to the right.  If I change vga settings in the menu.lst file (add vga=792, or 791, etc.) it doesn't help and even gives the same effect to all the text in other ttys (like when I hit alt-ctl-F1, the text looks like little horzontal lines are taken out and moved to the right).  Anyone know how to fix it?  It's really a pretty minor thing, but it really annoys me every time I see it, and can make it hard to work from the console.  In case it matters, I've got the desktop effects enabled (nothing changes when they aren't), and I've got the stock nvidia drivers installed (the nvidia-glx package).

---

### Post by borahshadow on 2007-06-30
I did on edgy but I can't rember if it happens after I upgraded to feisty
But I had that exact same problem on edgy I'll shutdown and see if I do.
ps I have the drivers from envy but on edgy I thok I used the repostiory that they guy who makes envy maintains (alberto milone or something)

EDIT does not happen since feisty for me but I'm on 32bit

---

### Post by pjones0404 on 2007-06-30
i had the same issue on edgy and i was using the drivers from envy. i recently killed my edgy and did a fresh install of feisty and i have the same issue again. i am using the driver from the restricted driver manager. i would really like to know how to fix it. 


My main isue is the wireless on this laptop. what is the easiest way to get it working reliably in feisty? i would also like to use a network manager of some sort to connect to vaious networks as i travel. 

any and all help is greatly appreciated .

---

### Post by lythandrel on 2007-07-01
> **dragonfyre13 said:**
> I think I'll do that then. Let me clean the guide up a bit, and I'll post what I am, and am not, having issues with.

Can't wait to see your feisty guide.  Been waiting with baited breath, and now that people have been having wonderful luck with either the cvs, or the 1.04.0 drivers working, I'm HOPING that you're having the same luck.  

Been wanting to upgrade to feisty (or sabayon) but it seems that there are some nasty problems compiling the wifi drivers since the upgrade from kernel 2.6.17-10 to 2..6.17-13 (which is when the driver s no longer wanted to work.  I truly cannot wait for your  feisty guide.

---

### Post by Joshua on 2007-07-01
> **lythandrel said:**
> Can't wait to see your feisty guide.  Been waiting with baited breath, and now that people have been having wonderful luck with either the cvs, or the 1.04.0 drivers working, I'm HOPING that you're having the same luck.  

Been wanting to upgrade to feisty (or sabayon) but it seems that there are some nasty problems compiling the wifi drivers since the upgrade from kernel 2.6.17-10 to 2..6.17-13 (which is when the driver s no longer wanted to work.  I truly cannot wait for your  feisty guide.

Just a thought, but would it be worthwhile to put a guide like this into a wiki - something like the [www.ubuntuguide.org](www.ubuntuguide.org) page but for anything that people run into with this specific laptop?  Anything that came up in a forum discussion could then more easily be included into the guide.

---

### Post by lawr_rawr on 2007-07-01
> **Joshua said:**
> I just installed Feisty for AMD64.  Is anyone getting an ugly looking splash on shutdown?  Not on bootup - just on shutdown. 

I get the same thing with the 32bit version, and I am using the same drivers as you. I also (occasionally) get similar glitchy video with horizontal lines when I resume from hibernate. 

I very rarely hibernate, though, now that suspend works perfectly with kernel 2.6.20-16. With 2.6.20-15, the screen wouldn't wake up. 

** also seconding the idea of putting all this info in a wiki -- would be helpful!

---

### Post by Joshua on 2007-07-01
> **lawr_rawr said:**
> I get the same thing with the 32bit version, and I am using the same drivers as you. I also (occasionally) get similar glitchy video with horizontal lines when I resume from hibernate. 

I very rarely hibernate, though, now that suspend works perfectly with kernel 2.6.20-16. With 2.6.20-15, the screen wouldn't wake up. 

Oh yeah, maybe I missed it earlier in the forum but I was also going to mention that suspend seems to work now in Feisty.  WAY COOL!  Also, I use a wireless Kensington PilotMouse.  It used to go dead after several minutes of non-use or after coming back from hibernation or after unplugging it and then replugging it.  Now it all seems to work well.

However, I have noticed that, while the "Desktop Effects" seem to work with a little tweaking, The screen doesn't always refresh after returning from another tty console, or from suspend.  (BTW, the tweaking I did was to correct the lack of borders on the windows after enabling desktop effects, and to make the cube work when switching between workspaces.  But I don't use the desktop effects except to impress people because of the bugs above and a couple others.)

> **lawr_rawr said:**
> ** also seconding the idea of putting all this info in a wiki -- would be helpful!

I considered copying what I could glean from this thread into a wiki on wiki.ubuntu.com, but I don't know if that is the best place for it (maybe it should go in the documentation wiki?), and I wanted to make sure most others on this thread would agree, and I don't know if I've really got the expertise to do it (I'm really just a copy and paste wizard).

---

### Post by dragonfyre13 on 2007-07-02
> **lythandrel said:**
> Can't wait to see your feisty guide.  Been waiting with baited breath, and now that people have been having wonderful luck with either the cvs, or the 1.04.0 drivers working, I'm HOPING that you're having the same luck.  

Been wanting to upgrade to feisty (or sabayon) but it seems that there are some nasty problems compiling the wifi drivers since the upgrade from kernel 2.6.17-10 to 2..6.17-13 (which is when the driver s no longer wanted to work.  I truly cannot wait for your  feisty guide.

Thanks for waiting. I must admit, I'm in the middle of buying a house (My first one! YAY!) and I haven't had much time. However, I will be grabbing the ISO tonight for Fiesty and doing a fresh install of the 32bit version to clean up the guide process, and get everything working and in order. I will likely be packaging the script that lawr_rawr made (if that's OK with you lawr_rawr) into a deb file with the script that NickB made, and maintaining an Averatec 2370 deb file. It's going to be mainly scripts, but hopefully it will make it easier on everyone.

Also, lawr_rawr, could you post a lisence for that script? GPL preferably, but anything you want to lisence it as is fine. I just want to make sure I have a license to include in the deb file.

If anyone has even decent experience with packaging (this is my first time packaging a script. Previous to this it has been building from checkinstall) or knows of somewhere with an easy to use tutorial for it, that would be really, REALLY helpful.

I'll also put this on the Wiki when I have time. I'll probably post the original guide in a post, and then replace the main guide with the fiesty one too.

---

### Post by lawr_rawr on 2007-07-02
Well, I've never created anything for public distribution before, so I'm really not sure how that's supposed to be done. (my first perl script!) GPL is fine. 

So we should just need to add something like:
    ```
<one line to give the program's name and a brief idea of what it does.>
    Copyright (C) <year>  <name of author>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
from [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) to the script?

We might also want to post something on averatecforums.com (site appears to be down at the moment) -- their linux audience is pretty small, but I know there are a few posters over there... 

I picked Ubuntu as my first Linux distro simply because of dragonfyre13's guide... this is *so awesome* that so many people are working together on this to simplify and clarify so many things. 

And this is only slightly off topic -- my fav Apple parody. Mac vs Pc vs Linux!
[http://www.youtube.com/watch?v=t-L-0s-7-Z0](http://www.youtube.com/watch?v=t-L-0s-7-Z0)

---

### Post by dragonfyre13 on 2007-07-02
> **lawr_rawr said:**
> Well, I've never created anything for public distribution before, so I'm really not sure how that's supposed to be done. (my first perl script!) GPL is fine. 

So we should just need to add something like:
    ```
<one line to give the program's name and a brief idea of what it does.>
    Copyright (C) <year>  <name of author>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
from [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) to the script?

We might also want to post something on averatecforums.com (site appears to be down at the moment) -- their linux audience is pretty small, but I know there are a few posters over there... 

I picked Ubuntu as my first Linux distro simply because of dragonfyre13's guide... this is *so awesome* that so many people are working together on this to simplify and clarify so many things. 

And this is only slightly off topic -- my fav Apple parody. Mac vs Pc vs Linux!
[http://www.youtube.com/watch?v=t-L-0s-7-Z0](http://www.youtube.com/watch?v=t-L-0s-7-Z0)

Personally, I would put it under version 2, but that's mainly because I'm not familiar with GPL 3. That's as simple as changing the 3 to a 2. Other than that, it looks great!

Oh, and I feel a bit self concious that I was your reason to choose Ubuntu. I've never been important in anyone's decision on anything before, to my knowledge. Either way, I'm happy you're here.

And here is one article on the spoofs. There are more than 1 (3 to be exact) [http://reverendted.wordpress.com/2007/03/19/mac-vs-pc-how-would-linux-fit/](http://reverendted.wordpress.com/2007/03/19/mac-vs-pc-how-would-linux-fit/)

---

### Post by lawr_rawr on 2007-07-03
> Personally, I would put it under version 2, but that's mainly because I'm not familiar with GPL 3. That's as simple as changing the 3 to a 2. Other than that, it looks great!

Oh, and I feel a bit self concious that I was your reason to choose Ubuntu. I've never been important in anyone's decision on anything before, to my knowledge. Either way, I'm happy you're here.


Ok. I'll add that part to the script tomorrow and post it here (my laptop's in my car and I'm too lazy to grab it). 

No, I think it's awesome that your guide was comprehensive enough to get so many people up + running! I tend to research things as thoroughly as possible before jumping into them. I wanted to know what the possible issues were and how to remedy them, and this thread was most helpful. I'd also been hearing more and more about this "Ubuntu" on Lifehacker, etc. and was planning to give some variant of Linux a shot as soon as my coursework was complete and I no longer needed Microsoft-specific software for my school projects. (and now I am once again excited about computing as I was when I got my first $150 486 SX-33 at the age of 10!) I've also had some pleasant surprises: the card reader working immediately, and suspend working after the latest kernel update. 

In the past couple weeks I've also ditched Windows on this desktop -- unintentionally. Had a successful install, but after rebooting I had no GRUB and a Windows install that would bluescreen with "inaccessible boot device" after displaying the Windows splash. My copy of XP was of the "yo ho, yo ho, and a bottle o' rum" variety, and rather than fix the problem I decided I ought to go legal. :-) And that's a story for an entirely different thread. 

I'm on my third Averatec (3150, 1020, now 2370 -- how can I resist buying one every year when the things are tiny, cute, and less than $700?) Cheers to everyone here, and to Averatec bargains, too!

Here is the updated script with GPL and a couple comments/prettifiers. I've added a drawer to my gnome-panel with links to scripts for my 2 regular networks (home and work) and this script. Not quite a GUI, but close enough for me!
```

#!/usr/bin/perl

#    Wifi Connection Script for Averatec 2300-series (RT73) Wireless
#    Find and connect to WPA/WEP-enabled wireless networks.
#
#    Copyright (C) 2007 - Lawrie Morey lmorey+rtavwifi @ gmail.com
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.

$ralink = rausb0; # replace with name of your adapter if it is not rausb0
$count = -1;

print "Averatec 2300-series Wifi Script";
print "\n--------------------------------------\n";

# scan for networks
open(SCAN, "iwpriv $ralink get_site_survey |");
   while (<SCAN>) {
   if ($count >= 1) {
      ($channel,$rssi,$ssid,$bssid,$enc,$auth,$type) = split;
      if ( $ssid ne "" ) {
      print "${count}: SSID: ${ssid}, Security: ${auth} (${enc})\n";
      }
   }
	$count += 1;
   }
close(SCAN); 

# make your choice!
print "\n--------------------------------------\n";
print "Enter number of network to connect to: ";
chomp($choice = <STDIN>);
$count = -1;

# scan again and connect!
open(SCAN, "iwpriv $ralink get_site_survey |");
   while (<SCAN>) {
   if ($count == $choice) {
      ($channel,$rssi,$ssid,$bssid,$enc,$auth,$type) = split;
      print "Connecting to SSID: ${ssid}\n";

	if ($auth eq "WPA-PSK") {
		print "Enter passphrase: ";
		chomp($key = <STDIN>);
		`iwconfig $ralink essid $ssid`;
		`iwpriv $ralink set NetworkType=$type`;
		`iwpriv $ralink set AuthMode=WPAPSK`;
		`iwpriv $ralink set EncrypType=$enc`;
		`iwpriv $ralink set SSID=$ssid`;
		`iwpriv $ralink set WPAPSK=$key`;
		`iwpriv $ralink set SSID=$ssid`;
		`dhclient $ralink`;
		}
	elsif ($enc eq"WEP") {
		print "Enter key: ";
		chomp($key = <STDIN>);
		`iwconfig $ralink essid $ssid`;
		`iwconfig $ralink channel $channel`;
		`iwpriv $ralink set AuthMode=WEPAUTO`;
		`iwpriv $ralink set EncrypType=$enc`;
		`iwpriv $ralink set Key1=$key`;
		`iwpriv $ralink set SSID=$ssid`;
		`dhclient $ralink`;
	}
	else {
		print "Cannot connect to network.\n"
	}
	
   }
	$count += 1;
   }
close(SCAN); 

```

---

### Post by borahshadow on 2007-07-03
Sorry I'm sure that i'm just dumb but when I suspend or resume it comes backup to a black screen and the caps lock indicator flashes what am I doing wrong I'm realy excited to know that suspend/hybernate work but this is my first real laptop and I don't know how to wake it out of the flashing caps lock 
ps I am on feisty
pps for the person who asked the easiest way to get wireless working *_I_* think it is ndiswrapper

---

### Post by dragonfyre13 on 2007-07-09
> **borahshadow said:**
> Sorry I'm sure that i'm just dumb but when I suspend or resume it comes backup to a black screen and the caps lock indicator flashes what am I doing wrong I'm realy excited to know that suspend/hybernate work but this is my first real laptop and I don't know how to wake it out of the flashing caps lock 
ps I am on feisty


I don't think your dumb. I'm having the same issue. I know it has to be something that I'm overlooking, but I'm trying an upgrade so I think I borked the install the first time around. I have my other (fourth) test partition with a special edgy eft version that ONLY has the modifications according to this tutorial. I think I will be upgrading that after I image it over this test partition.

> **borahshadow said:**
> pps for the person who asked the easiest way to get wireless working *_I_* think it is ndiswrapper

Granted, that is an easy way to get it working, and for some things it does work well. Part of the issue, and the reason I didn't want to say "Use NDISWrapper" is A) as far as I know, they don't distribute the wireless drivers online, only on the windows partition, and B) I don't have that windows partition.

Also, there are all sorts of reasons not to use NDISWrapper, but I won't go into those here. You can choose for yourself, but if you decide to go NDISWrapper, let us know how it went. Even if I can't (And won't) do it, I'll be happy to see another person happy.

PS: Please, Please, Please do not upload or link to the driver here. Not the driver on the windows side. The file is not allowed to be redistributed, which is the reason I haven't found it on the net. I read the averatec forums (Unofficial ones) that talked about this issue, and one of the members was dinged hard for uploading the file.

---

### Post by borahshadow on 2007-07-10
> I don't think your dumb. I'm having the same issue. I know it has to be something that I'm overlooking, but I'm trying an upgrade so I think I borked the install the first time around. I have my other (fourth) test partition with a special edgy eft version that ONLY has the modifications according to this tutorial. I think I will be upgrading that after I image it over this test partition.
Well At least I'm not the only one Mine was a fresh install if that makes a difference
> Granted, that is an easy way to get it working, and for some things it does work well. Part of the issue, and the reason I didn't want to say "Use NDISWrapper" is A) as far as I know, they don't distribute the wireless drivers online, only on the windows partition, and B) I don't have that windows partition.

Also, there are all sorts of reasons not to use NDISWrapper, but I won't go into those here. You can choose for yourself, but if you decide to go NDISWrapper, let us know how it went. Even if I can't (And won't) do it, I'll be happy to see another person happy.

PS: Please, Please, Please do not upload or link to the driver here. Not the driver on the windows side. The file is not allowed to be redistributed, which is the reason I haven't found it on the net. I read the averatec forums (Unofficial ones) that talked about this issue, and one of the members was dinged hard for uploading the file.
Hmm I was not aware that it could not be redistributed actually I think what I did was I used the windows ralink driver (just follow the link for the linux one and browse their site to the windows section) it was a .exe and I installed it on my virtual machine and then copied the .inf .sys and .bin over and used that
They could have changed the licence since I downloaded it though

I used ndiswrapper on edgy and feisty and it works great the reason I don't use the native is because I love my graphical network manager otherwise I would love to use the native even if it took more work as long as I could use networkmanager
> B) I don't have that windows partition
I no longer have it ether I wiped it when I fresh installed feisty

ps I like your sig :popcorn:

---

### Post by lawr_rawr on 2007-07-10
```
I don't think your dumb. I'm having the same issue. I know it has to be something that I'm overlooking, but I'm trying an upgrade so I think I borked the install the first time around. I have my other (fourth) test partition with a special edgy eft version that ONLY has the modifications according to this tutorial. I think I will be upgrading that after I image it over this test partition.
```

I wonder what the secret to a successful suspend is? I started with a clean install of Feisty, and after the most recent kernel update (2.6.20-16-generic) suspend magically worked. I haven't tried it in a couple weeks, though, so for all I know it might be borked again. :confused:

I've made no changes that I know of to anything power-related... I try not to play with things that are working well -- though I do plan to switch from Beryl to Compiz Fusion tonight. Switched yesterday on my desktop (with ATI Radeon 9600) and went from choppy, slow graphics to perfectly smooth cube-spinning and effects. Hope it goes just as smoothly on the Averatec!

---

### Post by dragonfyre13 on 2007-07-11
> **lawr_rawr said:**
> [CODE]I do plan to switch from Beryl to Compiz Fusion tonight. Switched yesterday on my desktop (with ATI Radeon 9600) and went from choppy, slow graphics to perfectly smooth cube-spinning and effects. Hope it goes just as smoothly on the Averatec!

Make sure to post back here with what you did, and how it worked! I'm anxious to try out fusion, but I haven't actually put that much effort into it.

---

### Post by lawr_rawr on 2007-07-11
Compiz Fusion works great on the 2370! I followed the instructions in the sticky in the Desktop Effects forum here: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

First, I switched back to Metacity, stopped beryl-manager, and removed Beryl from auto-start in System --> Preferences --> Sessions. 

Is it OK to copy+paste the instructions from the other how-to? Just refer to the instructions in the link above, up to the point of launching Compiz Fusion. 

Then, launch Compiz Fusion with Alt-F2:
```
compiz --replace --indirect-rendering -c emerald &
```

The indirect-rendering option helps with the infamous Nvidia black windows when you have too many things open. On the recommendation of a post on the opencompositing forums ( [http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window) ) I also added the following lines to my xorg.conf under the Screen section (be sure to make a backup first!):
```
        Option          "DamageEvents"  "True"
        Option          "UseEvents"     "True"
        Option          "TripleBuffer"  "True"
```
I am not sure whether the xorg.conf modifications or the indirect-rendering option alone would work; I made both changes at the same time, and restarted the GUI with Ctrl-Alt-Backspace. I haven't gotten a black window since!

** If you are not already using Beryl or a different version of Compiz, you will need to make sure you have 
```
 Option "AddARGBGLXVisuals" "true"
```
under the "Screen" section of your xorg.conf, as described on the first page of this thread under the "install Beryl" section.

---

### Post by kernco on 2007-07-17
I just used this guide to get my wireless working in Ubuntu 7.04 on my Averatec 2260-EK1 :D

I got the current driver from Ralink's site, rather than the one linked to here.  The strange thing is, in the network manager panel applet, it shows "Wired Network (Unknown USB Vendor Specific Interface)", but if I select that it connects to my wireless network.  I'm not sure how this will work when there are more than one networks in range, since if it actually thinks there's a wireless interface it shows the list of detected networks.  The output of iwconfig isn't exactly what you have posted, the last 3 lines are missing:
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"dlink"  
          Mode:Managed  Channel=11  Access Point: 00:1B:11:54:23:BF   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          

```
I don't know what the significance of those missing lines are.

Anyway, I have been trying to get wireless working on this laptop since Ubuntu 6.06, and this finally worked.  Thank you!!  More good news is that the ralink wireless chipsets not working out of the box is a known bug ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95889](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95889)) that's been reported, confirmed, and assigned to the ubuntu kernel team, so hopefully they will have it working for 7.10.

---

### Post by lawr_rawr on 2007-07-17
Hmm, interesting. I seem to remember the same thing showing up with "Unknown USB" in Network Manager. I promptly chucked Network Manager, as it didn't do a darn bit of good for connecting to secure networks.

I have found that the auto-connect for unsecured networks always picks the one I want. :-) If you're in a public place, like a coffee shop, the strongest network will probably be the correct one, and that's the one it will choose. 

btw, how is Ubuntu on the 2260? My boss has that laptop. Video working at proper resolution? Does Compiz/Beryl work?

---

### Post by kernco on 2007-07-17
lawr_rawr,

Ubuntu was pretty much unusable on this laptop until 7,04, but now it seems to work pretty well.  Wireless doesn't work out of the box, but the instructions on this guide seem to fix it.  Also, the synaptics trackpad isn't detected.  You can move the mouse cursor out of the box, but if you want to scroll using the trackpad, you'll have to manually edit your xorg.conf to set it up as a synaptics pad.  The graphics chip isn't nvidia or ati, it's embedded on the motherboard which is manufactured by VIA.  I haven't even bothered trying to see what Compiz/Beryl is like. The screen turns all white when I try to enable the compiz that's built into 7.04.  Out of the box, the vesa driver is used (the graphics chip is detected as "Generic Display Adapter").  If I change it to the via driver, X doesn't start.  I haven't tried to do much to get it working, since I'm not using this laptop for any heavy graphics stuff, so vesa is fine.  Although Compiz Fusion would be nice...I'll post here if I ever get it working.

Edit: Oh, and the resolution is set at 1024x768 by default, but it's pretty easy to edit the xorg.conf and add 1280x800, and that works fine.

---

### Post by pjones0404 on 2007-07-18
i need some help getting my wireless to work. i am fairly new to ubuntu and i am unsure of the best way to get it up and running.

I would like to be able to use the graphical network manager and be able to connect to various secured networks. if i have to use  "sudo iwconfig" every time that would be ok as well as long as it is a reliable connection.

If someone could provide fairly detailed instructions of either using ndis wrapper or another method to get this set up i would appreciate it. Currently i am using a novatel u720 CDMA wireless card to access the web and i am limited to about 750k. It isn't bad but i know it would be so much better if i could use my wifi at home.

If any one has a sprint evdo card and need assistance setting it up i could help with that. 

thanks in advance

edit - by the way i have a fresh install of feisty

---

### Post by dragonfyre13 on 2007-07-19
> **pjones0404 said:**
> I would like to be able to use the graphical network manager and be able to connect to various secured networks. if i have to use  "sudo iwconfig" every time that would be ok as well as long as it is a reliable connection.

[http://ubuntuforums.org/showthread.php?t=489368&highlight=howto+ndiswrapper+fiesty](http://ubuntuforums.org/showthread.php?t=489368&highlight=howto+ndiswrapper+fiesty)

You need to install Ndiswrapper to use the graphical network manager. The above link is a pretty good one for that, though you will use a different *.inf file than the one listed there. Lawr_rawr? You installed Ndiswrapper didn't you?

---

### Post by pjones0404 on 2007-07-20
thank you for the link. where can i find the *.inf file that i need. i had the wireless working in edgy but i always had to run the "sudo iwconfig" to get it working. i could not use a gui to set up networks at all.

i will be so happy if i can set it up in feisty w/ the gui becaus i move from diferent secure networks. i eagerly await his information. \\:D/

---

### Post by lawr_rawr on 2007-07-21
I have not used Ndiswrapper on the 2370. Actually had a disastrous time with it on a Fedora install on my boyfriend's spare PC with a Netgear card... ended up using MadWiFi (atheros) and got it working in no time. Never wanted to touch it again.

The Ralink driver package from Averatec is an executable but there might be a way to extract the files you need for Ndiswrapper without actually installing it under Windows.

However, if you still have your Windows partition, you can look for the following files:
```
windows/system32/drivers/rt73.sys, rt73.bin

windows/inf/rt73.inf
```
... I'm not sure which files are necessary to use ndiswrapper. I think just the .inf and the .sys. 

If you don't have the Windows partition any longer, you might be able to begin the install of the drivers under Wine -- the install creates a temp1orary folder with a data1.cab... which presumably contains the drivers you need, if you extract it with the cabextract util. Let me know, I'll try it if you don't have a Windows install to grab the .inf and .sys files from. Can't post the files here, but if necessary, could post instructions...

Wow, I booted into Windows for the first time in about a month to verify those drivers and to try the installer... glad to be back to the Linux-world.

---

### Post by pjones0404 on 2007-07-22
i do still have my windows partition. so i should be able to copy the needed files.

If you would provide some basic instructions on how to instal them i would appreciate it. i have been ithout my wireless since i did a fresh install of feisty and it is killing me.

---

### Post by lawr_rawr on 2007-07-22
These are the basic instructions for Ndiswrapper:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

At the bottom of that page, there's a link with instructions for configuring WPAsupport with wpa_supplicant. If you need WPA, it looks like you will need to configure wpa_supplicant first. I'm not sure how it works with roaming between networks, though, because it instructs you to create a .conf file with your network info. 

Honestly, the native Ralink drivers combined with my script (posted earlier) or a scripted set of commands to connect to a single secured network (I have 2 of these scripts, 1 for home and 1 for work), seems like a much more flexible way of moving between different secured networks. 

Personally, I added a drawer to my panel with launchers for my homewifi, workwifi, and wificonnect scripts. It's just one extra click and a password to connect... not quite a gui but it has been very reliable for me. I've actually only encountered one WPA access point that requires additional commands... I have to request a DHCP address 2 or 3 times before it will assign one; first couple attempts time out. It's at a coffee shop, so I have no idea what type of router it is. 

I think you will probably get *better* support in the forum if you try the Ralink method first... there does not seem to be anyone here who has used Ndiswrapper. I'm not trying to say one way is better than the other; just that people here have more experience with the Linux Ralink drivers and configuration. If you want to try the Ralink drivers, and then post the output of "iwpriv rausb0 get_site_survey" I'd be happy to post a script for your specific config.

I wish I had the HD space to do a second install of Ubuntu so I could try Ndiswrapper, as I'm unwilling to replace my current config...

---

### Post by pjones0404 on 2007-07-22
ok i installed the 1.0.4.0 drivers. i anow have the rausb0 listing when i run iwconfig. below is the output from the command "iwpriv rausb0 get_site_survey"

rausb0    get_site_survey:
Channel RSSI    SSID                                BSSID               Enc         Auth                NetworkType 
6       -78     2WIRE436                            00:18:3f:05:99:59   NONE        OPEN                Infra       
10      -58     h0me                                00:40:05:24:2e:9f   WEP         OPEN                Infra       

i appreciate the help. i found the script from this thread, but i do not know what to do with it exactly. 

thanks again

---

### Post by lawr_rawr on 2007-07-23
Which of the wireless networks is yours? I'm guessing it's the h0me, and not the 2wire, but I want to make sure...

---

### Post by pjones0404 on 2007-07-23
you are correct. my network is the "h0me" network.

another quick question for everyone that has this same laptop. i occasionally have issues w/ it freezing up. the mouse still moves an music still plays but everything else is non-responsive. i can not close windows or anything. i have even tried ctrl-alt-F1 and it does not work either. i eventually have to hard reset since it never unfreezes. This has been an issue in fiesty as well as edgy. anyone else have any freezing problems.

---

### Post by lawr_rawr on 2007-07-23
First you will want to make a location to store your scripts. I have a scripts directory in my home folder.

Open a terminal window, and do the following:
```
mkdir scripts
gedit scripts/h0mewifi
```

Paste the following into the text editor:
```
#!/bin/bash
echo "working..." 
iwconfig rausb0 essid h0me
iwconfig rausb0 channel 10
iwpriv rausb0 set AuthMode=WEPAUTO
iwpriv rausb0 set EncrypType=WEP
iwpriv rausb0 set Key1=<enteryourkeyhere>
iwpriv rausb0 set SSID=h0me
sleep 2
dhclient rausb0
```
Edit the line sets Key1, replacing <enteryourkeyhere> with your key in hex (the big long string of alphanumeric characters).

Save the file and close the text editor window. Make the script executable:
```
chmod 755 scripts/h0mewifi
```

Now you're ready to run the script:
```
sudo ./scripts/h0mewifi
```
It will prompt you for your password. and you should see the status of the dhclient command. If it's successful, you'll see the IP address your computer has been assigned.

If you have problems:
To make sure you're associated with the correct access point, try:
```
iwconfig rausb0
```
To make sure you have an IP, try:
```
ifconfig rausb0
```
Post the output of these commands if you can't get online.

I have not had permanent problems with freezing... I get occasional (2-3 second) lockups with Compiz Fusion running, but it always returns to normal after a couple seconds.

---

### Post by pjones0404 on 2007-07-24
that worked fantastically. i appreciate you making that quick guide so easy to use. i am now able to access my h0me wifi network in all it's high speed glory. \\:D/=D>\\:D/

i just have a few questions regarding the script so i can understand exactly what is going on if u don't mind. 

1. #!/bin/bash - is this all it takes to create a shell script? anything after this is run in order?
2. there is not a special file extension of naming convention that is required for these types of scripts. the other scripts that i have copied from others all start w/ a . before the name and are hidden files. 
3. when issuing this command "sudo ./scripts/h0mewifi" what is the difference between ./ and~/?


Once again i greatly appreciate it i will be modifying this script for the other networks that i connect to.

---

### Post by lawr_rawr on 2007-07-24
Glad it worked! 

The first line in a script starts with #! and specifies which shell will be used to execute the commands.
```
#!/bin/bash
```
means use the bash shell. If you take a look at my earlier wifi script, it uses #!/usr/bin/perl, since it's a perl script. 

After that, you just list the commands you want to run, and they'll be run in order. The unix/linux world doesn't care about naming conventions: as long as you make the file executable with "chmod 755" (or any other variant that grants execute permissions), you can run it. 

"~ " is your home directory. "." is your current folder. So, the command I gave you to run the script will work as long as you're in your home directory. If you want to add the script to a launcher in your panel, you'd want to use "sudo <full path to file>", like "sudo /home/username/scripts/scriptname". 

Some people use .filename to hide the script; some use .sh at the end to indicate it's a script... I think it's all a matter of personal preference. I like having a scripts directory, because then I can see at a glance what scripts I've personally created, and I don't have to remember to list the hidden files. All up to you! 

The h0me script should work for other WEP-encrypted networks; just change the channel, ssid, essid, and key. If you need to connect to WPA, try my other script as there's a few more variables and options needed to connect to WPA networks.

---

### Post by borahshadow on 2007-07-28
So I have tried many different things and I still can't get mt suspend working hibernate used to work (sorta) in edgy but now with suspend or hibernate it boots and then my caps lock just flashes for those who do have suspend working did you do anything special? 
ps. I'm running kubuntu but I don't see how that would make much of a difference since the core and the kernel is the same
I've got by without suspend but it would be really cool if it would work I feel that it is close but I just can't figure out the last part

---

### Post by Joshua on 2007-07-30
borahshadow,

I installed Feisty from scratch, and then immediately changed my sources list to include main, restricted, universe, and multiverse and upgraded everything.  Then suspend and hibernate both just worked.  Suspend comes back quickly with no problems.  Hybernate takes a while and it's hard to tell where it is in the process (for both going into hibernate and for coming out of it), but eventually everything comes back.  I have noticed that neither works properly when I've got the desktop effects enabled.

---

### Post by borahshadow on 2007-07-31
Hmm I have beryl installed but it is not active I don't use it because of the bugs I'm waiting for a stable release of compiz fusion
I realy don't want to do a freshinstall but I might because of this bug which is a big deal for me [bug 82292]("http://bugs.kde.org/show_bug.cgi?id=82292")
If I do reinstall I'll try immedietly anfter an update to see if it is a kubuntu thing or not

---

### Post by Joshua on 2007-08-03
I was just googling for info on the wireless card and found this:

[Relevant Comment]("https://bugs.launchpad.net/ubuntu/+bug/34902/comments/45")
[Thread]("https://bugs.launchpad.net/ubuntu/+bug/34902")

Is it true that adding those options will get the card to work?  Has anyone tried it?  On AMD64?

Hopefully, I didn't miss a previous discussion on this.  I appologize if I did.

Also, I don't mean to be pushy, but did anyone create an updated version of this Howto, or set up a wiki as was discussed earlier?  If so, we should probably link it from the first page.  If not, well, let's get a move on!  The public awaits!

---

### Post by Joshua on 2007-08-03
Oops, I guest those were old.  I wasn't even thinking about the dates on that stuff.  On top of that I was searching for my old laptop.  These posts should probably be ignored.

---

### Post by borahshadow on 2007-08-08
I was about to install another install of feistu to test suspend but when I booted into a live cd I coulden't resize my current partiton can you resize ext3 partitions?

---

### Post by Joshua on 2007-08-10
I'm pretty sure you should be able to resize ext3.  I've found that the installation CD doesn't always work when I let it do all the resizing.  I usually use gparted (I think it's in the menus on the CD) to resize and create a free space (unpartitioned) and then during the installation I tell it to use the largest free space available.

---

### Post by borahshadow on 2007-08-13
ok i found out that qtparted doesn't resize ext3 but gparted can so I installed gparted (kubuntu livecd)
anyway I resized it made a new feisty install and then upgraded everything (one thing I did do however was I added an official repository for KDE 3.5.7 which came out right after feisty did so they made official packages) and then when I tried suspend it came back to a black screen it didn't even look like the screen was on. however the caps lock didn't blink this time so something is different I might reinstall and not use kde3.5.7

EDIT: I just saw your sig are you using 64bit? I wonder if that could be it I might try that too I was using 32

---

### Post by dragonfyre13 on 2007-08-14
Alright guys, I'm back, and I have news.

Wow, have you been busy while I've been gone. Working out the issues and such....

Well, the news is simple. My server crashed, and I haven't had access to the internet for a few weeks, except through work (like now). My server was running Ubuntu, but as far as I can tell, it was a hard drive failure. (IO Errors everywhere). However, this being my main machine, that I also used as a server, I was pretty shocked. I also upgraded this one from Warty, so I was a bit disappointed.

Either way, my main machine failed, and in addition, I moved into my first house. (YAY! :KS ) Well, there is a downside. Qwest just recently got the phone working, and I can't find the power cable for the Modem. Now, there is no way that I am buying another DSL modem from them, so I'm unpacking everything like a madman.

The downside to all this is that I haven't spent ANY time on the guide, the reasoning being that it's gone. It was on the server, and not making backups will do that to you. However, I'm running disk recovery software on it now (unfortunately not linux based, I don't think. It's like a live CD kinda, but proprietary.) and I very well might be able to actually get everything (or most everything) back. Including the guide. The UP side to this, is that now I am using the Laptop full time. In addition to the other 6 servers, 4 desktops, and 7 thin clients that I have. But mainly the laptop.

Thsi means that I will be working on the guide like mad for a while, to get it up to spec. Also, more good news. My wife is leaving. No, not the bad kind, she's leaving to go visit her mother. And I don't have to come! :lolflag:

Seriously though, this gives me time to buckle down on the guide, and the other tasks I haven't had time for lately.

Just figured I'd give you all an update, and make sure that the thread didn't die in my absense. Of course I should have known that lawr_rawr wouldn't let that happen.

---

### Post by dragonfyre13 on 2007-08-14
> **borahshadow said:**
> So I have tried many different things and I still can't get mt suspend working hibernate used to work (sorta) in edgy but now with suspend or hibernate it boots and then my caps lock just flashes for those who do have suspend working did you do anything special? 
ps. I'm running kubuntu but I don't see how that would make much of a difference since the core and the kernel is the same
I've got by without suspend but it would be really cool if it would work I feel that it is close but I just can't figure out the last part

Just as an aside, it matters incredibly that you are using KDE to my understanding. Gnome Vs. KDE both handle suspend and hibernate differently, from what I have read. Of course, this may be entirely wrong....

---

### Post by lawr_rawr on 2007-08-16
Glad you're back. :-) Seems like drive failure is hitting us Averatec fans... first averatecforums.com, now dfyre. 

I haven't been too active on here; I'm starting a new job on Monday and have been training my replacement here for the past 2 weeks. (I've developed a great means of motivation -- *punch* "if you don't read the warning or error message thoroughly, I'm going to hit you harder next time")

I also had router problems at home and picked up a new Buffalo router (flashed to DD-WRT firmware, awesome stuff!) and have been exploring the features. Highly recommended!

---

### Post by ministre on 2007-08-17
Hello All:

Thanks for the useful forum. This thread helped me install ubuntu on my averatec 2370 laptop.

For wireless ... the native linux driver did not do it for me. I can see the rausb0 interface but I was never able to get good connectivity with my wireless network. Instead I am using ndiswrapper and it works fine.

The problem I am having is suspend to ram. The screen stays blank after I try to wake up the laptop. I did a clean Feisty install and suspend to ram does not work. I think I saw it work at some point, but then I did a clean reinstall of Feisty and it does not work anymore. Could anyone give me some directions about how I could debug the problem.

Warm regards

---

### Post by Joshua on 2007-08-17
borahshadow,

> EDIT: I just saw your sig are you using 64bit? I wonder if that could be it I might try that too I was using 32

Yeah, I just updated my signature.  I've got Feisty for AMD64 on both my desktop and laptop and I use the regular desktop with Gnome.  I actually hardly know anything about KDE.  Sorry.

---

### Post by Joshua on 2007-08-17
> **ministre said:**
> Instead I am using ndiswrapper and it works fine.

I'm using ndiswrapper, but I think it's causing my computer to lock up after several minutes of web browsing.  Everything freezes and the caps lock button flashes.  I have to do a hard restart.

> The problem I am having is suspend to ram. The screen stays blank after I try to wake up the laptop. I did a clean Feisty install and suspend to ram does not work. I think I saw it work at some point, but then I did a clean reinstall of Feisty and it does not work anymore. Could anyone give me some directions about how I could debug the problem.

Warm regards

Are you using KDE?  A couple posts above, it looked like maybe KDE doesn't do suspend well.  Also, if you are using Gnome, when I have the desktop effects enabled, suspend doesn't always work properly, but it works perfectly when I have the effects turned off.

---

### Post by ministre on 2007-08-19
Hello Joshua:

No I am using Gnome and I don't think I have desktop effects turned on.

---

### Post by curiocheerio on 2007-08-20
I'm not sure if this was mentioned earlier but the alpha release of ubuntu gutsy supports both the video and wireless card for the averatec 2300 out of the box. I was pleasantly surprised to not have to do any tweaking to get it working WPA included. So im pretty stoked about it. On the downside, compiz-fusion seemed pretty buggy and eventually killed my installation. That said, i would imagine that the final release will be significantly more stable. I'm really looking forward to it. It will be nice.

---

### Post by ministre on 2007-08-21
Does suspend to ram work on Gutsy ?
I am pretty desperate to get that to work ... suspend to ram does not work with Feisty for me.

---

### Post by curiocheerio on 2007-08-21
> **ministre said:**
> Does suspend to ram work on Gutsy ?
I am pretty desperate to get that to work ... suspend to ram does not work with Feisty for me.

No it doesn't, at least not for me. Not out of the box at least. I was a little disappointed by that as well. :(But then again you cant really judge what will and wont work until the final release.

---

### Post by lawr_rawr on 2007-08-21
Well, I'm now part of the no-suspend club. Ever since the latest update to Compiz Fusion (Trevino's repository, 0.5.3) I get a cursor with a purple box around it when I resume. I can switch to a console and restart it, but it hangs during the shutdown process and needs to be powered off manually. 

I'll see what happens when I prevent Compiz from loading at startup... I suspect it will suspend just fine then.

*Added 8/23/07: Just a quick note to say yes, suspend works when Compiz Fusion is not running. Let's see what today's updates do!*

---

### Post by LasTion on 2007-08-26
I'm trying to get the wireless working but I am getting errors when trying to make the build and it won't complete. Any solutions?

---

### Post by lawr_rawr on 2007-08-30
What are the errors? Post them here.

---

### Post by borahshadow on 2007-09-08
Someone just mentioned this on the other page but I thought I would elaborate a little.
I just booted into a Gutsy Tribe5 live cd and the first thing I noticed was the new graphics (still KDE but new graphics).  Then the next thing I noticed was that it correctly detected the graphics card and used the nv driver and the 1280x800 resolution which looks Beautiful.  I don't know if it a new font or something but I think it looks better than feisty and the envy driver.
The next thing is I could connect (with network manager) to my wep network perfectly)
I have not done an install to test suspend because I wanted to back up my data first (just in case of the worst) but I hope to do that today gutsy is looking great

ps. the kubuntu team has stepped up the the normal ubuntu team I think.  We finally have a restricted driver manager :)

pps. when I get gutsy installed I will install kde4 too the live cd's always give me problems

---

### Post by deadlydeathcone on 2007-09-11
> **borahshadow said:**
> ps. the kubuntu team has stepped up the the normal ubuntu team I think.  We finally have a restricted driver manager :)s

There also seems to be a kde version of gdebi, too, which is awesome. I haven't used KDE in a while, but I remember the exclusion of those bugging me a bit.

Like you said, Gutsy is shaping up really well on this laptop, especially since the wireless drivers work with network manager out of the box now! The only major problem I've had is with said wireless drivers, which would cut out every 45 minutes and need a cold shutdown to fix.

Compiling the latest (9/11/07) revision cleared it up, fortunately. If anyone wants to save some compiling time, I uploaded 32 binaries [here]("http://www.box.net/shared/gvggarfk4y"). Extract the archive, make a backup of the old drivers, and copy the rt2x00 folder to ```
/lib/modules/2.6.22-11-generic/ubuntu/wireless
``` Reboot, and you're done,

---

### Post by deadlydeathcone on 2007-09-11
Double post, so here's a guitar:

:guitar:

---

### Post by curiocheerio on 2007-09-14
:):):)
I'm pretty excited now. After getting the latest updates to gutsy, suspend to ram seems to be working. sort of. It suspends and actually comes back alive instead of staying in an endless coma like usual. There are still a couple issues however. First of all, it isnt suspending when i close the laptop lid. I have to initiate the suspend from the shutdown menu. Also, its not suspending when i'm connected to a wireless network. Just disabling the network adapter with "ifconfig wlan0 down" wont do it though. You have to disconnect from the wireless network such that you have the little "no network available" icon in the tool tray.

As for it coming back up, i've had a couple things happen depending on my video settings. If i have "No Effects" selected then only 2/3rds of the screen is used when it restores. It does come all the way up though without any coercion. If i have "Normal effects" or "Extra effects" then i get a blank screen with a cursor that i can move around. At this point if i restart the X-server (ctrl+alt+backspace) then it "usually" comes back up (full-screen, unlike the 2/3rds screen you get with effects turned off).

This all seems very promising. I'm not quite sure what to do at this point. I may try using the s2ram utility and see if that works any differently.

---

### Post by curiocheerio on 2007-09-15
I did a fresh install of gutsy tribe 5 then got all of the latest updates this morning. With the fresh install suspend to ram and suspend to disk are working great. Also, i feel kinda dumb since i realized that the reason it wasn't suspending when the lid was shut is because it wasnt enabled in the power manager.

The issue with it not wanting to suspend when i was connected to a wireless network seems to be resolved as well.

The only thing that i needed to do was install the restricted nvidia driver. Without it wouldnt fully wake up from suspend.

At this point, i finally dont have any good reason to not use ubuntu all the time. All i can say is woot woot!

---

### Post by borahshadow on 2007-09-25
> **curiocheerio said:**
> I did a fresh install of gutsy tribe 5 then got all of the latest updates this morning. With the fresh install suspend to ram and suspend to disk are working great. Also, i feel kinda dumb since i realized that the reason it wasn't suspending when the lid was shut is because it wasnt enabled in the power manager.

The issue with it not wanting to suspend when i was connected to a wireless network seems to be resolved as well.

The only thing that i needed to do was install the restricted nvidia driver. Without it wouldnt fully wake up from suspend.

At this point, i finally dont have any good reason to not use ubuntu all the time. All i can say is woot woot!
I installed the tribe 5 cd shortly after it came out and have been continually updating it.
I just got around to installing the restricted driver and suspend works :) :):guitar::popcorn::KS:) but not with nv :(
This is in kubuntu remember it is also with the latest kernel 2.6.22-12 or something.

But I have a strange problem which as of now has not been reproduced I'm trying to figure out how to reproduce it but here it is...
I was on the internet and suddenly it said it couldn't find the page I looked and network manager said it was connected but I right clicked to try to reconnect but it stopped at configuring device.  I thought I would reboot into feisty to get my work done, but while it was shutting down it gave some errors that looked like they related to my wireless card but they went away too fast to read it all.  I thought it was just a buggy driver in gutsy.
When feisty was starting up it gave usb errors on loading manual modules or something and again on starting bluetooth services.  When I logged in it didn't even see that my wireless card existed I was thinking that my usb root hub had fried or something, but I shutdown and waited 30sec and booted up it worked fine and just a second ago it did it again but it didn't want to shutdown and I had to hold the power button so I couldn't see if it gave errors on booting up immediately after shutdown 
I have been on gutsy for almost a half an hour and it has not done it yet I'm going to try to see if it has something to do with suspend but the first time it did it I don't think I had suspended

ps this is the 2nd time my avaratec has given me a scare in the last few months
the first time I was in a hurry and turned my laptop on on the way down the stairs so it could have a head start booting up and when I got down the stirs the bios had given an error about a bad smart status on my hard drive but everything has been fine so far. and then this but gladly this was not a hardware problem
in reply to the earlier post it does seem that hard drive troubles come to avaratec owners (thank goodness I have raid on my server :))

hmm I just suspended and when I came back knetworkmanager (the gui) said that network manager was not running (I had this problem once before but not after suspend) so I typed suso NetworkManager in the terminal and then I could connect so my usb was not screwed up hmm

---

### Post by curiocheerio on 2007-09-25
After my previous post i noticed that suspend works so long as im not running Compiz. When i am running compiz i get the infamous black screen with a cursor. I can hit ctrl+alt+backspace but when i log back in nothing works. No network connection and apps wont open. I'm not sure if its an issue with compiz or the nv driver. I've tried all the tricks i could  find to get is working but with no luck. I'm going to install the Beta release as soon as it's available and see if there is any improvement for my little lappy top.

---

### Post by borahshadow on 2007-09-28
ok I noticed this problem with the wireless disconnecting and disabling my usb again this time I could reboot directly into feisty and low and behold there was no wireless card detected
Could any one else help me try to reproduce this I would make a bug report except I don't know it it is a kernel issue or a networkmanager issue and it is not constant and I can't reliably reproduce it 
This is really the only show stopper from me just killing my feisty install I need help reproducing it so I can report it and get in fixed by the final release

---

### Post by NickB on 2007-09-30
I installed the amd64 flavour of Gutsy beta this weekend, and for the most part everything works pretty well out of the box.  The only exception is that the "quiet" option *must* be removed from the boot options.  It makes APIC fail, and using noapic is NOT an option if you want such things as CPU scaling, USB support, etc.  Kind of an odd workaround, but I prefer seeing the boot sequence anyway.

This is probably an amd64 issue ONLY.

Nick

---

### Post by Ru$$i@N on 2007-10-05
HI, I'm using averatec 2300 too.
So yeah, the system is Feisty AMD64. When I boot up the laptop, right after I choose the distribution in Grub, white lines start blinking all over the screen, then the ubuntu splash appears and everything comes to normal.

It doesn't really bother me, but I feel that something is wrong and should be fixed, because it is not usual and doesn't happen on my desktop.

Thanks

---

### Post by Joshua on 2007-10-06
> **NickB said:**
> for the most part everything works pretty well out of the box.

So wireless works out of the box in Gutsy?  Do the network manager and encryption work, too?  How should I go about uninstalling the stuff that I compiled before I upgrade?  I guess I should at least take the stock drivers out of the blacklisted file, right?

---

### Post by borahshadow on 2007-10-07
> **Joshua said:**
> So wireless works out of the box in Gutsy?  Do the network manager and encryption work, too?  How should I go about uninstalling the stuff that I compiled before I upgrade?  I guess I should at least take the stock drivers out of the blacklisted file, right?

I would just do a clean install especially since many things have changed in gutsy

---

### Post by pjones0404 on 2007-10-07
i recently did a clean install of gutsy on my machine and the wireless does not work. the network manager sees the network and i input the key. 

it says that i am connected but i can not brows or ping. i have been assigned an ip by my netowrk but it does not work. any ideas?

---

### Post by dragon76 on 2007-10-10
Hello everyone. I am so glad that I found this thread. I just ordered an Everex StepNote ST5340T. This is esentially the same laptop as the averatec 2300 series. OfficeMax.com has them on sale for $599 so it was a no brainer. The motherboards are the same and some of the Averatec owners use the everex bios to solve an issue with cpu scaling in Vista. Here's the specs:

-Operating System: Genuine Windows Vista® Home Premium
-Display: 12.1" WXGA Widescreen (1280 x 800) with DiamondBrite Technology, TFT Active Matrix LCD
-Processor: AMD Athlon™ 64 X2 Dual-Core Processor Dual-Core Processor TK-53 (512KB L2 Cache, 1.70GHz, 1600MHz)
-Chipset: NVIDIA® GeForce Go 6100 (Northbridge), NVIDIA® nForce® Go 430 (Southbridge)
-Memory: 1GB DDRII 533MHz (512MB x 2) 2GB maximum memory
-Hard Disk Drive: 100GB SATA, 5400RPM, 9.5mm
-Optical Drive: DVD-ROM/DVD+/-RW Double Layer Support (Maximum speed and compatiblity 4X DVD+R DL, 4X DVD-R DL, 6X DVD-RW, 8X DVD+RW, 8X DVD+R, 8X DVD-R, 8X DVD-ROM, 16X CD-RW, 24X CD-R, 24X CD-ROM)
-Graphics: NVIDIA® GeForce® Go 6100 with 256MB dynamically allocated
-Audio: HD Audio with Built-in Speakers. Realtek ALC262 High-Definition Audio Codec (Analog: 20-Bits Max Resolution, 192kHz Max Samping; Digital: 24-Bits Max Resolution, 96kHz Max Samping)
-I/O Ports: (1) DB 15-Pin VGA Port, (3) USB, (1) Microphone Port, (1) Headphone Port, (1) IEEE1394
-Modem: (1) 56K Motorola SM56 Data/Fax Modem (V.92, 56kbps)
-LAN: (1) Realtek RT8201CL, 10/100 Base-T Fast Ethernet
-Wireless LAN: Built-in RaLink RT2571WF 802.11b/g
-Keyboard: 84-Key US Keyboard with Hot Keys Functions
-Pointing Device: 2 Button Glide Pad with Integrated Vertical and Horizontal Scroll Functions
-Power Supply: 65 Watt (20V@3.25A) Auto sensing external AC-DC Adapter (100-240V~1.5A; 50-60Hz), 3-Prong US Power Cord
-Battery: 6-Cell Lithium-Ion (11.1V, 4400mAh) included
-Measurements: 11.7” x 8.4” x 1.3 - 1.4” (L x W x H)
-Weight: 3.8 lbs

It should be here in a day or two and after a backup of the partitions is done (warranty) I'll break out the Gutsy Beta CD and let you know how it goes. Gutsy beta has been quite stable on my x2 desktop and shows a real evolution of the Ubuntu OS IMHO.

Dragon

---

### Post by NickB on 2007-10-10
> **borahshadow said:**
> I would just do a clean install especially since many things have changed in gutsy
That's pretty much what I did.  I backed up my /etc directory and started over (everybody puts /home on a separate partition, right??).  Everything worked out of the box, including wireless and WPA, except for suspend and hibernate, which are now working thanks to a recent update.

Nick

---

### Post by borahshadow on 2007-10-12
I've never put home on a seperate partition because I always have wondered about running out of room on one and plenty on the other what would you reccomend for /home and for /  ?
i'll try to do some more testing this weekend and see if the new -14 kernel fixed the network bug i've been talking about

---

### Post by dragon76 on 2007-10-12
Ok, so UPS showed up with my new toy last night and when I opened it up, to my surprise there was a restore cd. That saved me from having to do a backup of the partitions. So I booted into Vista just to see if all of the hardware was working ok... YUK!! Vista is even worse than I thought, and the stuff that is supposed to be impressive isn't any better than kde without compiz, not to mention that it's almost unusable. It was eating over 600MB ram at idle even after I turned a bunch of junk off. Oh well... easily solved, just pop in the System Rescue CD, type startx, and double click on gparted.

I booted with the kubuntu gutsy live disk and everything was recognized so I rebooted with the alternate disk and away we went. Everything worked out of the box. Other than bugs that I also have on my desktop system with gutsy I have only noticed the following things:

- Volume hotkeys will only change volume by one step no matter how many times you press them. Mute works, however.
- Brightness hotkeys do not change brightness.

If they get the last few bugs worked out of gutsy I think it will be the best os I've run yet.I am running the amd64 version on the laptop and also on my x2 desktop.

Dragon

---

### Post by borahshadow on 2007-10-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152456](https://bugs.launchpad.net/ubuntu/+bug/152456) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just filed this bug report if anybody wants to try to reproduce it ( I posted a possible way) and add a comment that might help it get fixed

---

### Post by dragon76 on 2007-10-15
borahshadow...

I had this happen to me today and a few days ago. The first time it happened I noticed that my usb trackball quit working... yes wireless was on at the time. Today when it happened it occured exactly at 4.00hrs uptime... maybe has something to do with it? I don't know if this is an issue with the wireless drivers or the usb. I would guess the usb maybe. The only way I can get the wireless/usb to come back up is like you... turn the system off and cold boot. I have a strong feeling this may be a usb issue.

I am running Kubuntu Gutsy beta amd64 Generic kernel... what are you running?

I have posted to the launchpad bug as well.

Dragon

---

### Post by dragon76 on 2007-10-15
I also marked the bug as confirmed.

---

### Post by dragon76 on 2007-10-15
Ok, just did it again. This time uptime was 1hr 52 min so that is not related. The usb continues to work just fine. Both my trackball and the cardreader continued to work after the problem appears. You can hibernate and then reboot. This also causes the wifi to come back without having to close your x session.

I will update the bug report as well.

Dragon

EDIT: There is another thread reporting this same problem with external adapters using this same chipset.

[http://ubuntuforums.org/showthread.php?t=569776]("http://ubuntuforums.org/showthread.php?t=569776")

---

### Post by borahshadow on 2007-10-15
I'm running gutsy 32bit so the architecture does not seem to be the problem
thanks for confirming it maybe it will get some fire under it :)
I'm going to try to reproduce it without saving to a server then maybe try compiling the new drivers
does anybody else know anything about getting a bug more attention I've already nominated it for gutsy

edit too bad we can't plug and unplug the card like that other thread says helps

---

### Post by dragon76 on 2007-10-15
I tried to use modprobe to unload and load the rt2x00 kernel module. I couldn't unload it though as it would fail saying it was in use. If someone could tell me how to get around that I am wanting to try to unload and reload the module as that may solve the problem. I then could write a script that we could use to "reset" the driver until a new driver version fixes the bug.

Dragon

---

### Post by dragonfyre13 on 2007-10-15
I wanted to let everyone know that I am finishing up the Gutsy Guide right now. It should be posted tonight, or possibly tomorrow during the day.

YAY! I give myself a cookie.

Anyway, sorry for skipping a release, and I hope I can still be here to help. I'll be majorly basing it on what I read in this thread, and it likely won't solve all of the issues right off, but it should solve a big part of them for people who are reinstalling, or just first installing Gutsy.

Anyway, just a heads up.

---

### Post by dragonfyre13 on 2007-10-16
> **dragon76 said:**
> I tried to use modprobe to unload and load the rt2x00 kernel module. I couldn't unload it though as it would fail saying it was in use. If someone could tell me how to get around that I am wanting to try to unload and reload the module as that may solve the problem. I then could write a script that we could use to "reset" the driver until a new driver version fixes the bug.

Dragon
Try flipping the wireless switch. That may be something you want to do on suspend anyway (it's cleaner to come back when it's not connected to a network.)

Also, try the -f option when you modprobe -r the module.

Most importantly, could you please post (as an attachment) the output of dmesg the next time that this happens? it gives some valuable information on it.

If anyone comes across a syslog that would log events of wireless cards, that would be a log to upload too.

By the way, I've found out that a great many people are having issues with the serialmonkey drivers for rt73, so that's not a route that the guide is going to take.

---

### Post by dragonfyre13 on 2007-10-16
> **dragon76 said:**
> I tried to use modprobe to unload and load the rt2x00 kernel module. I couldn't unload it though as it would fail saying it was in use. If someone could tell me how to get around that I am wanting to try to unload and reload the module as that may solve the problem. I then could write a script that we could use to "reset" the driver until a new driver version fixes the bug.

Dragon
A bit wierd of a request, but here it is. Try killing network manager (not shutting it down via it's interface, killing it.) and see if that brings the card back in business.

I have a feeling it's a firmware issue.....

---

### Post by dragon76 on 2007-10-16
I think that I had tried the hardware switch earlier but will be sure to give it a try. I will try killing network manager next time. I wasn't sure if the modprobe -f option would work in conjunction with -r but will try that as well. The two of us that have reported the issue are both running kde. Has anyone running gnome had the issue? Perhaps it is an issue with network manager in kde... It shouldn't be a kernel problem as we are running different architectures of kernel.

I usually just go to offline mode when I hibernate the system. I have found that if you don't and you restore and are out of range of the previously connected network it usually causes problems and requires a reboot to get the wireless back.

Dragon

---

### Post by dragonfyre13 on 2007-10-16
I'm working on Gnome, but will be testing on KDE and XFCE later on. I want to get this Laptop working out of the box, with no issues whatsoever on any DE.

Make sure to grab the dmesg, that's the most important bit. That gives some useful output that we can parse through next time.

---

### Post by borahshadow on 2007-10-16
I think I have a dmesg before and after it crashes on the bug report but I haven't had time to wade through it
I posted it on the bug report but I couldn't get it to crash with out anylocal traffic so it seems like the driver can't handle more than 2 way traffic (ie to router and back ) like it can't handle from router to router to router to server from server and back etc.

ps has anyone considered joining the laptp testing team or whatever (look it up on the wiki)

---

### Post by borahshadow on 2007-10-16
> **dragon76 said:**
> I tried to use modprobe to unload and load the rt2x00 kernel module. I couldn't unload it though as it would fail saying it was in use. If someone could tell me how to get around that I am wanting to try to unload and reload the module as that may solve the problem. I then could write a script that we could use to "reset" the driver until a new driver version fixes the bug.

Dragon

BTW thanks for trying this I was going to but once again I'm really busy right now (great timing huh)
One other thing I wondered about was try the usbcore module it will kill all usb devices but I would imagine that they would come alive again when you radded the module

---

### Post by dragon76 on 2007-10-16
It did it again!!!

Here is what I've learned:

the drivers are the serialmonkey drivers... just modinfo rt2x00usb or rt73usb

the wireless switch on the front of the laptop turns the led on and off but must just be connected to an interupt which is monitored by the windows driver as it has no effect other than turning the led on/off. It doesn't even affect the signal strength so it is not turning the radio or amp on or off either.

As I thought the -f option for modprobe won't work with -r. If you unload the rt73usb you can then unload rt2x00usb, then rt2x00lib. I couldn't unload usbcore or mac80211 as they were in use and I couldn't figure out what was using them. Unloading and reloading the above modules and restarting networking does not get you anywhere.

dmesg.txt is the dmesg from when I noticed the wireless was down

modprobe_rt73usb.txt is from after unloading and loading rt73usb

modprobe_rt2x00usb_rt73usb.txt is from after unloading rt73usb and rt2x00usb and reloading them.

ifconfig.txt and iwconfig.txt are from immediately after the problem as well

I hope these can help.

The following thread on the serial monkey forums indicates this problem with external usb adapters and gutsy

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4347]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4347")

If we are looking for commonalities I wonder if this is an issue with non smp kernels? We are all here running x2 cpu's. I am using WPA. Are all of us that are having problems using WPA?

---

### Post by borahshadow on 2007-10-16
I am using WEP and under feisty in which I use ndiswrapper the switch does turn something off because with the switch off I can't connect to a network
I'll see if there is a non smp kernel in the repos and try it (I believe it should work just not use both cores)

---

### Post by dragon76 on 2007-10-16
It would make sense that the switch works when using ndiswrapper, as you are using the windows driver and it would be monitoring for the switch and take the appropriate action.

Dragon

---

### Post by dragon76 on 2007-10-16
Has anyone had any luck with the modem? I was just thinking that it would be nice to be able to fax on the road.

Dragon

---

### Post by borahshadow on 2007-10-16
I have never tried nor have need for a modem
I just tried to reproduce it again and after ~3 hours no crash :confused::confused::confused:
hmm
It would be nice to have the switch work if you have to turn it off when you come back from suspend but oh well

---

### Post by dragon76 on 2007-10-16
Before I suspend or hibernate I go to the knetworkmanager applet (right click) > Options > Disable Wireless. I also tried going to offline mode but this didn't work. Yes the switch would be easier. Other than the obvious fact of not being open source, what is the disadvantages to using the win driver under ndiswrapper? Is there a third alternative for a driver, other than serialmonkey's and ndiswrapper, that is? This is the first laptop I have dealt with in linux and also the first time playing with wireless in linux as well so please forgive my ignorance.

Dragon

---

### Post by dragonfyre13 on 2007-10-17
OK, I'm posting the guide now, but a lot of it is blank. Much of it works by default, but I'm noting some personal caveats, and the wireless issues.

---

### Post by dragonfyre13 on 2007-10-17
Update applied. I tested quite a bit on this, and didn't come up with much that doesn't work by default. Post if you find anything wrong or incomplete.

---

### Post by borahshadow on 2007-10-17
> **dragonfyre13 said:**
> Update applied. I tested quite a bit on this, and didn't come up with much that doesn't work by default. Post if you find anything wrong or incomplete.
Realy the only thing that doesnot work is the wireless and under KDE the volume up keys with the function key don't work right but that is all that I can think of> Other than the obvious fact of not being open source, what is the disadvantages to using the win driver under ndiswrapper?
I've noticed that the serialmonley driver tends to read A little higher signal strength I think that it is just a more accurate signal reader
sometimes when I try to use a wifi hotspot (no encryption) I have to close Knetworkmanager(Network manager) and use Wireless assistant don't know why but I couldn't connect with network manager
other than those 2 things Not much
> Is there a third alternative for a driver, other than serialmonkey's and ndiswrapper, that is? 
The official ralink driver but I believe it is not GPL so that is why ubuntu shiped with the serialmonkey driver (serialmonkey claims to be more stable but I don't know)

> This is the first laptop I have dealt with in linux and also the first time playing with wireless in linux as well so please forgive my ignorance.
You seemed very knowledgeable probably more so then when I first put linux on this laptop (coming up on 1 year now in 1 month (after thanksgiving sale :)))

---

### Post by dragon76 on 2007-10-17
I thought I would post a list of the problems I have found in Kubuntu Gutsy:

- Wireless issue... it is annoying but not the end of the world
- Wireless switch on the front of the laptop only turns led on/off

I have found the function (Fn) keys to be working as follows:

Fn+F3 - backlight on/off - works
Fn+F4 - suspend - works
Fn+F5 - lcd/external display toggle - works
Fn+F6 - brightness down - not working
Fn+F7 - brightness up - not working
Fn+F8 - volume down - only moves one step no matter how many times you press it.
Fn+F9 - volume up - same as volume down
Fn+F10 - mute - works

It is annoying to have to use the gui interfaces for brightness and volume adjustments but at least it works! I wish that I could suspend without having to disable wireless but this is a problem with many laptops under linux from my understanding. I have not tried to get the modem working. If I succeed I will make a post of how to do it in this thread and dragonfyre13 can add it to the main page. I have not tested any expansion cards as I don't have any. Dual monitors works. It works the best using the nvidia-settings application and not using Xinerama. I will try to write a how-to for the dual displays in a few days when I get some time. I don't have the built in mic working yet but haven't had time to play with it much. The different items in the kde sound mixer are labled a bit confusingly. Card reader works with sd and mmc cards. I don't have a 4pin to 4pin IEEE1394 cable so I haven't tested it yet. I haven't tested any wireless drivers other than the ubuntu defaults (serialmonkey). The power manager in kubuntu works great, including setting the cpu power profile. I haven't burned a cd/dvd yet but expect it should work fine. All of the usb devices I have tried (1.1 and 2.0) worked fine.

Dragon

---

### Post by lawr_rawr on 2007-10-17
Ooh, progress! Okay, I'm holding off on Gutsy until the wireless problems are resolved, but I wanted to throw in my 2 cents regarding the RT73 chipset and the serialmonkey drivers. I just moved to a new apartment, and there's no way to get ethernet to my desktop... at least, no way that is aesthetically pleasing. By pure chance I picked up a (brand new!) Belkin MIMO USB adapter at Goodwill (8 bucks!) and took a chance that its guts would somehow be supported under Linux. It's RT73, just like our laptops.

I used the serialmonkey drivers on my desktop  (with Feisty) and got everything working, but have been seeing frequent disconnects. Can't get the device to scan or do anything at all unless it's unplugged and re-plugged. 

Has anyone tried using the official ralink drivers with Gutsy?

---

### Post by borahshadow on 2007-10-17
> **dragon76 said:**
> I thought I would post a list of the problems I have found in Kubuntu Gutsy:

- Wireless issue... it is annoying but not the end of the world
- Wireless switch on the front of the laptop only turns led on/off

I have found the function (Fn) keys to be working as follows:

Fn+F3 - backlight on/off - works
Fn+F4 - suspend - works
Fn+F5 - lcd/external display toggle - works
Fn+F6 - brightness down - not working
Fn+F7 - brightness up - not working
Fn+F8 - volume down - only moves one step no matter how many times you press it.
Fn+F9 - volume up - same as volume down
Fn+F10 - mute - works

It is annoying to have to use the gui interfaces for brightness and volume adjustments but at least it works! I wish that I could suspend without having to disable wireless but this is a problem with many laptops under linux from my understanding. I have not tried to get the modem working. If I succeed I will make a post of how to do it in this thread and dragonfyre13 can add it to the main page. I have not tested any expansion cards as I don't have any. Dual monitors works. It works the best using the nvidia-settings application and not using Xinerama. I will try to write a how-to for the dual displays in a few days when I get some time. I don't have the built in mic working yet but haven't had time to play with it much. The different items in the kde sound mixer are labled a bit confusingly. Card reader works with sd and mmc cards. I don't have a 4pin to 4pin IEEE1394 cable so I haven't tested it yet. I haven't tested any wireless drivers other than the ubuntu defaults (serialmonkey). The power manager in kubuntu works great, including setting the cpu power profile. I haven't burned a cd/dvd yet but expect it should work fine. All of the usb devices I have tried (1.1 and 2.0) worked fine.

Dragon

Amen to all of those function statements
I do not have any expansion cards ether. I have done dual monitors in feisty don't see why it shouldent work (should be great with 8.04 and xorg 7.3) I've got the built in mic working in feisty I'll try in gutsy(avaratec still claims there is not one :guitar:) I've used firewire in feisty don't know why that would regress
I'll apply any updates and once again try to reproduce last time I coulden't

---

### Post by borahshadow on 2007-10-17
> **lawr_rawr said:**
> Ooh, progress! Okay, I'm holding off on Gutsy until the wireless problems are resolved, but I wanted to throw in my 2 cents regarding the RT73 chipset and the serialmonkey drivers. I just moved to a new apartment, and there's no way to get ethernet to my laptop... at least, no way that is aesthetically pleasing. By pure chance I picked up a (brand new!) Belkin MIMO USB adapter at Goodwill (8 bucks!) and took a chance that its guts would somehow be supported under Linux. It's RT73, just like our laptops.

I used the serialmonkey drivers on my desktop  (with Feisty) and got everything working, but have been seeing frequent disconnects. Can't get the device to scan or do anything at all unless it's unplugged and re-plugged. 

Has anyone tried using the official ralink drivers with Gutsy?
lol you posted while I was I'm going to clean install soon and try the latest cvs serail monkey drivers there has been some recent progress for new kernels and smp machines but I don't know how recent and how recent the stock gutsy ones are if they don't work I'll try the official ralink ones (serialmonkey claims theirs are more stable :wink:(if they work :)))

there is a link to a thread about the rt73 chipset and gutsy somewhere a few pages back with the same problem this laptop has an rt73 the problem is we can't unplug it:mad:

---

### Post by borahshadow on 2007-10-17
Happened again today at 26min then reboot and 3 min and reboot no network card 
I tried various modprobe things nothing worked I tried killing knetwork manager no work :(:(:(

---

### Post by dragon76 on 2007-10-18
I just noticed about NickB's tray applet to set the power saving mode for the cpu. In kubuntu the power manager tray applet (battery icon) that is installed by default in gutsy lets you change modes out of the box. 

Right click > CPU policy > choose Dynamic, Powersave, or Performance

Another out of the box goody compliments of the wonderful Gutsy dev team. Of course this isn't as easy as using Nick's program for using the S button. My everex doesn't have the S button so I am limited to using the power manager applet, or write a script and have it executed by a hotkey combination.

---

### Post by lawr_rawr on 2007-10-18
> **borahshadow said:**
> lol you posted while I was I'm going to clean install soon and try the latest cvs serail monkey drivers there has been some recent progress for new kernels and smp machines but I don't know how recent and how recent the stock gutsy ones are if they don't work I'll try the official ralink ones (serialmonkey claims theirs are more stable :wink:(if they work :)))

there is a link to a thread about the rt73 chipset and gutsy somewhere a few pages back with the same problem this laptop has an rt73 the problem is we can't unplug it:mad:

Well, in the time I've had the Averatec with official Ralink drivers I've had no problems with disconnects. Using the serialmonkey drivers on my desktop, disconnects between 5-30 minutes. I still don't have internet access at home, but when I do, I will play with it more.

At least with the Ralink drivers we'll be no worse off than we have been with Feisty.

---

### Post by pjones0404 on 2007-10-18
hello everyone. i just installed 7.10 w/ a clean install. unfortunately i do not have any wireless as at this time. 

The network manager sees the network and allows me to put in the wep key and says that it is connected. however i can not ping or browse. I am just using the default install and thought that it would work out of the box. I know that in feisty i had to do something different to make it work. do i need to follow those steps again?

any and all help is appreciated. It looks really good so far but without wireless i cant really do much.....

-edit
with the guide being updated the steps for the old driver are no longer there. 

also... i recently spilled a coke on my laptop. :( everything still works but some of the keys are sticky now. i need to clean them. anyone know of the best way to do this? I found a link that goes over how to replace the keyboard. so i can just detach it and clean the needed keys. any info on this would be welcome as well. 

[http://forum.notebookreview.com/showthread.php?t=159350](http://forum.notebookreview.com/showthread.php?t=159350)

---

### Post by dragon76 on 2007-10-19
I just connected to a wep network last night at our local linux user group meeting without troubles. You shouldn't have to do the steps that you needed to on the command line in feisty AFAIK. I am using kde (kubuntu) so there might be a problem with the gtk (gnome) network manager?

One thing I did notice was that I had to tell network manager what type of passphrase I was using (it was 40bit hex so I had to select 40bit hex from the dropdown box). Once I figured that out I was as good as gold. I actually read your post there last night, but didn't have time to respond until today.

Thanks for the link on the keyboard... very useful.

Dragon

---

### Post by borahshadow on 2007-10-19
I defiantly do not want to une the c0mmand line I like my GUI network apps too much (plus is does not inperss my non linux family/friends
If the ralink drivers still don't work with gutsy it is back to ndiswrapper for me :(:( I was happy to get rid of closed source and windoze drivers
BTW the brightness keys work in gutsy

---

### Post by pjones0404 on 2007-10-20
i am using ubuntu gnome right now and there is no wireless at all...

What is the easiest way for me to determine what is causing the issue? i dont mind using the script to set it up like i did in feisty i just want it to work.  i may even download and install kubuntu so i can at least have it working and install gnome later.

---

### Post by dragon76 on 2007-10-20
You don't need to reinstall with Kubuntu if you already have ubuntu installed. Go into synaptic and search for kubuntu-desktop and install it. That should give you kde in addition to gnome and you can choose which you want to run on login. You could also use the command:

apt-get install kubuntu-desktop

I will try to get time this weekend to install Ubuntu gutsy (gnome) on my testing partition to find out what is going on and if there are any other things that aren't working. My guess is that it might be a problem with the gtk based network manager. If that is the case, one could theoretically run the qt based one under gnome I would think. I have done similar things in the past anyway.

Dragon

---

### Post by dragon76 on 2007-10-20
pjones - Try installing the knetworkmanager. Make sure to exit the default gnome network manager before running knetworkmanager. This is the network manager program that is the default in kubuntu. It should run under gnome without having to install the whole kde desktop. If you can try this out it would help us figure out where the problem is.

Thanks,
Dragon

---

### Post by jabeez on 2007-10-20
wow talk about funky, I am now having very strange wireless issues. I installed Kubuntu Gutsy beta a couple weeks ago, and the wireless worked outta the box (yay!) and worked flawlessly. A couple days ago I installed Ubuntu Gutsy on a separate partition, and wireless is pretty much unusable for any length of time, and now my Kubuntu install is doing the same thing. It not only disconnects randomly, but the device vanishes as well?!?!? And even weirder, after it vanished in Ubuntu earlier, I rebooted into Kubuntu and it didn't show up there, so I rebooted into Vista (I know, but honestly it works really well on this lappy, I was shocked), and there was STILL no wireless device. I had to turn it off and left it off for a couple minutes, then it worked again. So any ideas on how a device can work and then completely vanish?!? Never seen such a thing, especially after rebooting into different OS's. Pretty frustrating though, I was thrilled when Kubuntu was working so well outta the box, and finally seems to be catching up feature-wise with Ubuntu................

---

### Post by borahshadow on 2007-10-20
Yep same exact problem that wel all are having I have never seen it screw it up in different os's my best guess is that is does somthing weird the the bios or internal usb hub that takes a complete poweroff (zero power) to fix because a restart never turns off the power

---

### Post by pjones0404 on 2007-10-20
i installed the knetwork manager and it does the exact same thing. 

i made sure that i exited the gnome network manager. i then started the knetwork and it detected my wireless network. i entered my key and it said that i was connected. i am still unable to browse or ping at all. The details of the connection using the gui state that it is wlan0 and a ralink device. it is assigned an ip address as well as the default gateway. This lets me know that it is connected and that the DHCP is enabled. 

i have ran iwconfig and it shows again that i am connected to my network. i can also run ifconfig and it shows i am connected as well. are there any other commands that i can run that would help identify the issue?

any help on this would be appreciated.

---

### Post by dragon76 on 2007-10-21
Pjones, can you ping the router or any other local machines? When you try to ping them use their ip address in case you are having a dns problem. You could also try to connect on a different wireless network to see if we have issues between the laptop and your ap.

One thing that might make a difference also that I forgot to mention before. Try knetworkmanager again. This time instead of simply quiting the gnome network manager disable the wireless first, then run knetworkmanager and enable the wireless again. The wireless driver could have gotten funky when you quite the network manager while it was enabled. Sorry I forgot to mention that.

Dragon

---

### Post by pjones0404 on 2007-10-21
Well, still no go...

i tried to use the gui's again after disabling wireless before exiting and running the knetwork manager. Still the exact same issue. I do find the issue a little strange. I am not in a position to be able to go to another wireless network and see if i have the same issue. I dont think that it is my network as this same lappy worked on this same network in edgy and feisty. It also works fine in xp (what i am using to post this). I also have a  powerbook, 360, wii, and another windows desktop on this network w/ no issues at all. 

Now for some other information regarding the issue. 

the unusual thing is that when i try to browse it tries for a really long time. Also when i ping i do not get a host unreachable message. i have complete packet loss as shown below. 
Thanks again for the help. 


[I]Ping outputs

jones@jones-laptop:~$ ping [www.yahoo.com](www.yahoo.com) 
PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (209.191.93.52) 56(84) bytes of data. 

--- [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) ping statistics --- 
9 packets transmitted, 0 received, 100% packet loss, time 8009ms 

jones@jones-laptop:~$ ping 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 

--- 192.168.0.1 ping statistics --- 
9 packets transmitted, 0 received, 100% packet loss, time 8022ms 


[/I]

---

### Post by dragon76 on 2007-10-21
I will try to get a fresh gutsy install of plain old ubuntu on my testing partition this week and see if I have the same problems. Hopefully I will get time later tonight or tomorrow...

Hang in there!

---

### Post by lawr_rawr on 2007-10-21
Well, kids, I'm now part of the Gutsy club. I didn't *want* to do it right away, but I started having big wireless problems in Feisty. I finally got internet at my new apartment yesterday, but when I set up my router (which had previously worked just fine) I could not get an IP. Set up my old router; same thing. I even restored both routers to default settings, but couldn't get a dhcp address, even with no security. Totally bizarre. Setting a static IP made no difference, as I couldn't access anything. Any ideas what barfed?

Anyhow, I downloaded Gutsy from my other PC (and I gotta say, I love having 5MB cable instead of 1.5MB DSL!) and lo and behold, wireless worked from the live CD. So; here I am. Now let's see how long my wifi lasts. :-)

---

### Post by pjones0404 on 2007-10-21
> **lawr_rawr said:**
> 
Anyhow, I downloaded Gutsy from my other PC (and I gotta say, I love having 5MB cable instead of 1.5MB DSL!) and lo and behold, wireless worked from the live CD. So; here I am. Now let's see how long my wifi lasts. :-)

Are you saying that u installed gutsy from the live cd and wireless worked no issues at all? are u using gnome? i am having major wireless issues and you seem to not have any at all. i wonder what the difference is? i am using a 64 bit wep key at the moment. what kind of encryption are u using, i wonder if that has anything to do w it.

 dragon has been helping me find out what is wrong. thanks alot for that too! i am pretty sure you are the one that assisted me w/ sitting up wireless in feisty using the script. i could sure use more assistance now.

I appreciate all the help. i just dont know where to start since it appears that the driver is loaded correctly and is seeing the network. i even have an ip address.

---

### Post by lawr_rawr on 2007-10-21
Gutsy wireless worked straight away... sort of. I left my laptop on this afternoon, and it's been up for 5 hrs 27 min without dropping the connection.

I have 2 routers: a Zyxel P330W and a Buffalo G125 (with DD-WRT firmware). Yesterday, after not using my laptop for about a week,Feisty DHCP would not work with either router. I could associate to the access point but could not get an IP. Both routers were using WPA-PSK, TKIP. After I booted to the Gutsy live CD, I couldn't connect to the Zyxel. It would keep prompting for the password even though I knew I was typing the correct one. Windows worked with both routers.

(I even reset the Zyxel to defaults and upgraded the firmware on both routers yesterday!)

Gutsy and the Buffalo router worked straight away. I did not have to do anything fancy to make it work... it just did. I have no idea what caused the Feisty wifi freakout, or why I cannot connect to the Zyxel at all. 

You could try turning off your encryption entirely... see if that makes a difference. Would be best, though, if you could go to a friends house or coffee shop to test it on another network.

UPDATE: got the dreaded dropped connection within 5 minutes after I rebooted and enabled Compiz. Not sure if it's a coincidence or not, but 5.5hrs seems to be more wi-fi uptime than others are getting... we shall see what happens this time.

---

### Post by curiocheerio on 2007-10-21
I've also installed the final release and so far its looking pretty good. Suspend "seems" to work flawlessly as long as the restricted driver is installed. Compiz, seems to work nicely. Also, wireless seems to be working.

In the past i have been a little too quick to say that everything works perfect. I'll have to use it for a week or so before I'm convinced.

---

### Post by Joshua on 2007-10-21
So does anyone know why the network manager works with wireless on the live CD, but when I upgrade it doesn't?

---

### Post by lawr_rawr on 2007-10-22
I did a clean install, not an upgrade, so I can't tell you for sure -- but I suspect it is still using the same wireless drivers you were using in Feisty... not the new ones that are part of Feisty.

---

### Post by Joshua on 2007-10-22
> **lawr_rawr said:**
> I did a clean install, not an upgrade, so I can't tell you for sure -- but I suspect it is still using the same wireless drivers you were using in Feisty... not the new ones that are part of Feisty.

I suspected that, too.  Do you know how to check/fix that?  "lsmod" shows what looks like 3 drivers for the wireless: rt73usb (same name as the one I compiled for Feisty), rt2x00usb, and rt2x00lib.  Are there others that should be a concern?  Maybe things that should be blacklisted (I think I had the upgrader erase my custom blacklist file)?

I was originally going to backup my system and do a fresh install, but I wanted to try it now, and I don't have a lot of time lately to make sure that I backup everything I need.  Besides - requiring a fresh install to get everything right - shouldn't Ubuntu be better than that?

---

### Post by dragonfyre13 on 2007-10-23
> **dragon76 said:**
> Fn+F8 - volume down - only moves one step no matter how many times you press it.
Fn+F9 - volume up - same as volume down
Fn+F10 - mute - works


I've tried these in Gnome, and they seem to work fine. This could be a KDE issue.... Or maybe there is a very slight difference between the two laptops....

---

### Post by dragonfyre13 on 2007-10-23
> **dragon76 said:**
> I just noticed about NickB's tray applet to set the power saving mode for the cpu. In kubuntu the power manager tray applet (battery icon) that is installed by default in gutsy lets you change modes out of the box. 

Right click > CPU policy > choose Dynamic, Powersave, or Performance

Another out of the box goody compliments of the wonderful Gutsy dev team. Of course this isn't as easy as using Nick's program for using the S button. My everex doesn't have the S button so I am limited to using the power manager applet, or write a script and have it executed by a hotkey combination.

Actually, that is the thing that Nick's applet did, I believe. Assigns the S button to powersave. Very, very handy. Especially for those of us who have the button..... ^_^

---

### Post by dragonfyre13 on 2007-10-23
> **pjones0404 said:**
> hello everyone. i just installed 7.10 w/ a clean install. unfortunately i do not have any wireless as at this time. 

The network manager sees the network and allows me to put in the wep key and says that it is connected. however i can not ping or browse. I am just using the default install and thought that it would work out of the box. I know that in feisty i had to do something different to make it work. do i need to follow those steps again?

any and all help is appreciated. It looks really good so far but without wireless i cant really do much.....

-edit
with the guide being updated the steps for the old driver are no longer there. 

also... i recently spilled a coke on my laptop. :( everything still works but some of the keys are sticky now. i need to clean them. anyone know of the best way to do this? I found a link that goes over how to replace the keyboard. so i can just detach it and clean the needed keys. any info on this would be welcome as well. 

[http://forum.notebookreview.com/showthread.php?t=159350](http://forum.notebookreview.com/showthread.php?t=159350)

I'll rewrite the driver instructions if we find that it's better with the Ralink standard.

I did run across this issue also. I can browse a tiny bit, but it looks like HUGE packet loss when connecting to a WEP encrypted Network in Gnome. KDE it sounds like it's fine. Looking into it. More info would be appreciated. In the mean time, an unencrypted network works fine.....

---

### Post by dragonfyre13 on 2007-10-23
> **dragon76 said:**
> Pjones, can you ping the router or any other local machines? When you try to ping them use their ip address in case you are having a dns problem. You could also try to connect on a different wireless network to see if we have issues between the laptop and your ap.

One thing that might make a difference also that I forgot to mention before. Try knetworkmanager again. This time instead of simply quiting the gnome network manager disable the wireless first, then run knetworkmanager and enable the wireless again. The wireless driver could have gotten funky when you quite the network manager while it was enabled. Sorry I forgot to mention that.

Dragon


I think I'm suffering the same issue. It's an 802.11 B router, though I doubt that has anything to do with it. When I pinged it, I would get about 3-5 packets for every 50-70 packets requested. Eeek.

---

### Post by dragonfyre13 on 2007-10-23
> **pjones0404 said:**
> Are you saying that u installed gutsy from the live cd and wireless worked no issues at all? are u using gnome? i am having major wireless issues and you seem to not have any at all. i wonder what the difference is? i am using a 64 bit wep key at the moment. what kind of encryption are u using, i wonder if that has anything to do w it.

 dragon has been helping me find out what is wrong. thanks alot for that too! i am pretty sure you are the one that assisted me w/ sitting up wireless in feisty using the script. i could sure use more assistance now.

I appreciate all the help. i just dont know where to start since it appears that the driver is loaded correctly and is seeing the network. i even have an ip address.



Hmm. I had my issues with 64 bit Wep too. That's wierd.....

And yet my brother (another Ubuntu Convert thanks to me) using Fiesty had it work just fine. Granted, different card, but it means it's with the card or drivers itself, or the upgrade.

---

### Post by dragonfyre13 on 2007-10-23
> **Joshua said:**
> I suspected that, too.  Do you know how to check/fix that?  "lsmod" shows what looks like 3 drivers for the wireless: rt73usb (same name as the one I compiled for Feisty), rt2x00usb, and rt2x00lib.  Are there others that should be a concern?  Maybe things that should be blacklisted (I think I had the upgrader erase my custom blacklist file)?

I was originally going to backup my system and do a fresh install, but I wanted to try it now, and I don't have a lot of time lately to make sure that I backup everything I need.  Besides - requiring a fresh install to get everything right - shouldn't Ubuntu be better than that?

A. try blacklisting rt73usb. That should get things on the right track.

B. It shouldn't support upgrading from a wierd setup like we are causing with this laptop. Custom compiling those drivers, and having them conflict? The best they can do is erase the blacklist file and hope it works. We did some MAJOR mods to this to get it to work in feisty.

---

### Post by pjones0404 on 2007-10-23
thanks for the reply. i am using a d-link 802.11b router. i think that this is a very strange issue. 

i dont understand how some people are not having any issues at all and others are. :confused:

i will be trying it w/ out encryption tomorrow and will post back the results. thanks everyone.

---

### Post by lawr_rawr on 2007-10-23
Has anyone tried connecting to a network with hidden SSID? My work has access points all over the place.  iwlist scan shows me a half-dozen access points with a blank SSID, but when I use network manager to enter the hidden SSID, I cannot connect, and I cannot scan for networks again until I reboot. 

This did work under Feisty, though I had to manually set the ssid twice (twice for iwpriv, twice for iwconfig) I've tried manually setting the essid in Gutsy, but while it shows I am associated to the network, I'm really not. 

(Btw, I've had basically no problems with the intermittent wireless issues. I don't use the laptop for more than 3-4 hours at a time, usually, and I've only had the early and sudden drop once.)

EDIT: Figured it out! I needed to manually set the AP's MAC address, and configure the SSID, channel, and accesspoint MAC in Terminal. Uh-oh... I suspect I am going to be writing another script for this one. There are dozens of access points here (I work for a university) and while I can only pick up 2 in my office, from other locations I can pick up 6 or more. 

Please post here if you're connecting to a network with hidden SSID and if you can get it to work with Network Manager.

---

### Post by Joshua on 2007-10-23
> **dragonfyre13 said:**
> A. try blacklisting rt73usb. That should get things on the right track.

So "rt73usb" can only be the driver that I compiled?  There is no built in driver with the same name?  If blacklisting works, how can I go about uninstalling that driver that I compiled - something to the effect of reversing the installation process that you described in your howto?  Why have some custom installation on my system that I don't use, right?

> **dragonfyre13 said:**
> B. It shouldn't support upgrading from a wierd setup like we are causing with this laptop. Custom compiling those drivers, and having them conflict? The best they can do is erase the blacklist file and hope it works. We did some MAJOR mods to this to get it to work in feisty.

Well, I think that the only thing I've changed on mine is the wireless stuff.  There were some other problems in Edgy, but everything elses works fine in Feisty.  Anyway, I didn't mean that Ubuntu should just automatically recognize custom changes I've made and act correctly with them.  I just thought that, after upgrading a system where I've only changed the wireless drivers, it shouldn't be so botched that the BEST way to handle it is installing a new system.  That's too much like Windows, with constant restarts, and reinstalls, to keep your system "fresh" and "clean" ;-)  But I should be able to get rid of my changes somehow, and then let Ubuntu do it's thing.

I've run into other situations when I first started using Ubuntu where I'd upgraded a stock system and they wouldn't properly handle built in settings - where something would not work on an old version, then a new version would come out and it would work on the live CD, but then when I'd install everything it wouldn't work again.  In the end it sound's like that's not what's going on here.  They've gotten really good with their upgrades compared to where they were a couple years ago.

**UPDATE**
Ok, I don't know what happened, but it works now.  I put rt73usb in the blacklist, but that keeps all the wireless modules from loading.  Booted a couple times, loaded modules manually, booted a couple times, unplugged the wired port, booted a couple times... anyway, all of a sudden I clicked on the network icon and saw the options to choose networks.  SWEET!!!  Also, I didn't end up having to remove that compiled driver or anything, and after thinking about it, it made sense because it was compiled for the old kernel.  GUTSY ROCKS!

---

### Post by dragon76 on 2007-10-25
I had made a post about the hidden ssid issue on sunday night... for some reason I can't find it now. Yes I have experienced the same issue with hidden ssid's. Thanks for the workaround. I have 3 ap's that I regularly connect to that we have the ssid broadcast turned off on for security reasons of course. This will at least get me a workaround until we can try to get driver/network manager issues worked out.

I found out that there is an underlying network manager binary in ubuntu. There is then a GTK and a QT applet that runs on top of this depending on if you are running gnome or kde. The underlying network manager is the same on both. This would suggest that any problems should be identical regardless of desktop environment, as the network manager and driver is common for both. I am going to do a different install of kubuntu today to try out the oem drivers.

I don't know why the volume keys work in gnome but not kde. The volume keys on my desktop's keyboard work fine. Since it does change the level one step I am guessing it is a problem with the kde mixer since the keys are getting recognized. Also the default volume level that is ajusted by the kde pop up box or the volume keys is the headphone port volume. I have to actually enter the mixer to adjust the speaker volume.

Dragon

---

### Post by dragon76 on 2007-10-25
The volume key issue in kde is a problem with kmilo. There is a launchpad bug here:

[https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723]("https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723")

Hopefully it will be fixed soon, or you could apply the patch yourself.

Dragon

---

### Post by dragon76 on 2007-10-25
The brightness up/down key bug has been reported to launchpad here:

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337")

It appears to be an issue in changes to acpi and hal that have not been updated/addressed in kpowermanger. Gnome power manager has been fixed to solve the problem. I have confirmed that running gnome-powermanager in place of kpowermanager allows the brightness keys to function properly.

Dragon

---

### Post by borahshadow on 2007-10-25
hmm last I checked the brightness worked in gutsy:confused: I'll check again
I might apply that patch if I rember it didn't work well in kubuntu edgy ether it seems to break often
yes network manager is just the core with GUI's (ps network manager .7 is going to be awesome (google it) we can use more than one device at once (just like vista has eat that) and it looks like more drivers will work with it (eg. no more command line even for some of the weird drivers (ralink)
I think I'll just go back to ndiswrapper for one more release but make a partition for hardy to continually test it for this lappy so we have it Perfect :):):) (bug reports soon enough not while in RC)

---

### Post by Joshua on 2007-10-25
Has anyone figured out how to make the mic work?

---

### Post by borahshadow on 2007-10-25
I have in feisty but I have not got around to doing it for gutsy though shouldn't be much different (ps that is in kde)
just checked the brightness works in gutsy but]st have been a last minute update that bug report said some peoples were fixed our laptop must have been included
I just go the disconnect bug and I was using almost no internet only local it had to be <1h 
it seems like it happens without local traffic just takes alot longer

---

### Post by dragon76 on 2007-10-26
Borahshadow, the wireless driver crashes for me are completely unrelated to local trafic usage. They are also infrequent enough to be a nuicense but not a major issue. I still want to try using the oem drivers to see how stable they are, I just haven't had time to play yet.

I am now using the gnome power manager under kde as the brightness issue has been fixed with it. It also has a couple of other nice features that I like.

I also haven't had time to play with the mic yet.

To set the master volume control for the volume popup for the kmixer systray applet:

1. Right click on the systray applet.
2. Choose "Select master channel..." from the drop down box
3. Select "Front" in the list of coices.

Dragon

---

### Post by dragon76 on 2007-10-26
The bug with the brightness keys also effects kpowersave as I just tried it in place of kpowermanager. The only choice that I know of right now in kde if you want to use the brightness keys is to use gnome-powermanager.

Dragon

---

### Post by lawr_rawr on 2007-10-26
Has anyone had problems with slow wireless after a period of time? If I do a speed test within 10 min or so of powering on the laptop, I get my full 5M/500K speeds... or very close to them. If I try the exact same test (or any other speed test!) 10 minutes later, I get no more than 1100K/300K. I can verify with the conky monitor for up/down speeds that I am beginning the test with 0 traffic, and the up/down speeds conky reports correspond to the speed test.

I am testing with only one wireless device on the network at a time; I don't get the slowdown with my other pc (also using RT73 wireless, but the SerialMonkey legacy driver), or over a wired connection.

Edit: Sorry guys, crossing over to the dark side. I'm giving ndiswrapper and the windows drivers a try... I'll post back with the results. I really didn't mind power cycling the laptop every 3 hours or so with the spontaneous disconnect and wlan disappearance, but if I can only get 1/5 of my available internet speed, I gotta try something else.

So far, here's a plus to ndiswrapper. With the hidden SSID here, using the Gutsy defaults I had to set the ssid, then the channel, then the AP MAC. With ndiswrapper, I'm able to associate using just the ssid.

---

### Post by pwithem on 2007-10-27
Hello! The last time I messed around with Kubuntu was with edgy, where I was able to get wireless working.  It broke once I upgraded to feisty, so I've just taken a break until now.  Having installed 7.10 RC, my wireless did not work out of the box.  So, looks like i'm back to the blacklisting procedure.  This is fine, but it's been a while and I'm confused.  I can't find the old wireless directions in this thread, and I've heard of the serialmonkey drivers, ndis, and maybe something else.  I remember reading about a complicated procedure, alternative procedures, etc. and don't know what's the best route.  

Can someone succinctly lay out the procedure for installing each driver alternative?  Maybe some pros and cons of ndis vs. serialmonkey?  I don't use linux regularly, so I still am somewhat of a noob.  THANKS!

---

### Post by lawr_rawr on 2007-10-27
There are 3 options for wireless -- Ralink, SerialMonkey, and ndiswrapper.

Ralink: (haven't tested with Gutsy, but these are my observations from Feisty)
+ stable
+ manufacturer's official drivers
- difficult to configure
- no GUI
- doesn't use standard commands to configure the connection (must use both iwconfig and iwpriv to set properties)

SerialMonkey: (these are the drivers included with Gutsy)
+ works with network manager (GUI)
- requires manual configuration for hidden SSIDs (GUI does not work)
- random disconnects, wlan0 disappears entirely until you power-cycle the laptop (confirmed bug)
- sloooooow! (not confirmed, but I was able to replicate it multiple times. This might have existed with the ralink drivers, too, but I had slow DSL service when using them.) 

ndiswrapper: (this is what I am using currently)
+ works with network manager
+ seems to be stable (no drops or disconnects, but I've only been using it for about 4 consecutive hours)
+ easier to connect to hidden SSIDs (GUI works)
- must use Windows drivers (not open source)
- must have Windows installed to retrieve the drivers (I could not extract the drivers from the executable. I could extract the install files, but got errors when trying to extract the drivers from the .cab file) 

So, in short, I feel like a traitor for recommending ndiswrapper over the other methods, but at this time, it's the most reliable for me. Your needs may vary, 

That said, here's how to use ndiswrapper.
(dragonfyre, I remember something mentioned waaaay back about not wanting to post ndiswrapper stuff here... if it shouldn't be here, please feel free to edit my message)

I used the instructions from ["HOWTO: RT2500, etc. wireless cards"]("http://ubuntuforums.org/showthread.php?t=563547"). I've modified the instructions here to list the steps I took to get it working on our hardware.

1. Install ndiswrapper.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
2. Locate your Windows drivers and copy them somewhere on your Ubuntu partition. Mine were located in:
```
C:\windows\system32\drivers\rt73.sys
C:\windows\inf\rt73.INF
C:\windows\inf\rt73.cat
```
3. Load ndiswrapper driver module
```
sudo depmod -a
sudo modprobe ndiswrapper 
```
4. Edit /etc/modules and add ndiswrapper to the list
```
gksu gedit /etc/modules
```
Add a new line for ndiswrapper
5.Create the ndiswrapper alias
```
sudo ndiswrapper -m
```
6.Blacklist the current drivers
```
gksu gedit /etc/modprobe.d/blacklist
```
Add the following:
```
# Ralink
blacklist rt73
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2x00lib
```
7. Change to the directory where you copied the Windows drivers and install them. (Capitalization matters! If you get errors, make sure you are typing the name of the inf correctly. Or do what I did, and first rename the Windows files to lowercase-only.)
```
sudo ndiswrapper -i rt73.inf
```
8. Verify the drivers are installed
```
ndiswrapper -l
```
You should see something like:
```
rt73 : driver installed
        device (0DB0:6877) present (alternate driver: rt73usb)
```
9. Reboot! You should have a working internet connection now. If you want to verify you are using ndiswrapper:
```
lsmod | grep usbcore
```
You should see ndiswrapper listed, not rt****.

---

### Post by borahshadow on 2007-10-27
> So, in short, I feel like a traitor for recommending ndiswrapper over the other methods, but at this time, it's the most reliable for me. Your needs may vary,
I don't feel like a traitor it is not like you are using windows you are just using something made for windows
the drivers I use are made by ralink which provides opensource linux drivers they might provide windows source if someone asked them but for windows there is basically no need because 99.9% of average windows have no clue what compiling even is
and I'll use open source drivers as soon as their as easy or easier than the windows ones (and use a gui) hopefully in hardy this bug will be fixed and then good by ndis

In feisty they are more reliable too

I guess power cycling every 3 hours is not that bad but mine sometimes happend at 30 min or less don't know why like I said my best guess is that it is local traffic but that might not be true as dragon76 pointed out

dragon76 do your brightness keys still not work because mine do:confused:
maybe your laptop is slightly different then the 2370

ps for all 64bit users I'm thinking about joining the club (figuratively) is there any thing you miss about 32 does gnash work good? currently my test partition is 64bit

---

### Post by pwithem on 2007-10-27
^^Hey, thanks for the detailed response.  Setting to work on it right now and hope to get good results.

---

### Post by pwithem on 2007-10-27
Worked like a charm.  however, it also led me to understand my actual problem was likely ignorance.  I'm going to presume that not more than one wireless config utility can be used at once.  I had installed Wireless Assistant without realizing that the default installed and running KNetworkManager utility was already running the show.  So, I was trying to get Wireless Assistant to connect to my wireless network - which it could clearly see but would fail to connect.  After completing the ndis install and getting the same result, I then realized that the icon/utility indicating my lan connection was KNetworkManager and had been running all along.  So then I used it to configure my wireless and it worked without any trouble.  And, it may have been capable before the ndis install, but I didn't know it handled wireless.  All the same, thanks for the ndis directions; it was very easy to set up and I know I have a working alternative now.

---

### Post by dragon76 on 2007-10-27
lawr_rawr, I only have 1.5Mbs dsl here so I haven't noticed the wireless being slow in that regard, but I did try to transfer some gutsy images off of the server to the laptop to take with me last night and it was going to be painful so I just plugged in the network cable and did it that way. I thought that it might have been my wrt54g as it doesn't have the greatest throughput but after thinking about it... it was being choked way more than it has ever been with my wifes xp laptop.

pwithem: having both networking gui's running at the same time is a guaranteed way to lock up the rt73 driver in my experience.

borahshadow: my brightness keys work perfectly now. I am running the gnome power manager under kde. If you follow the link in my earlier post to the launchpad bug you can see that this is a bug on not only our laptops but all that are using the "generic" acpi key maps. This bug only affects kde systems. It showed up after 2.6.12 kernel due to the calls for brightness key functions being taken out of hal and now being accessed by the gui's. I personally think that they should go back into hal as otherwise if you don't have a DE running you can't change the brightness with the keys from the command line. If you want the brightness keys to work in kde you have two choices:

1. run gnome power manager
2. use two scripts and alter the acpi scripts - for instructions see the launchpad report

I chose to use gnome power manager as It has a couple of other features I liked and it didn't take up anymore RAM in comparison to the python based kpowermanager that was the installed default. Of course using the scripts you would gain the capability to use the brightness keys on the command line even with no X session running.

64bit: When I decided to try out Gutsy beta I decided to go all the way and switch to 64bit, this was before I had the laptop. I have no regrets at all. Gnash works quite well though I have found a couple of bugs. There is a flash-nonfree package available in the repos for 64bit you could try as well, it of course just does the download and install from Adobe.

I will probably join the ndis wrapper club as well as the hidden ssid issue is a real PITA for me.

Dragon

---

### Post by pjones0404 on 2007-10-28
i just followed the steps listed here for ndis and it works great. i appreciate the guide.

---

### Post by dragon76 on 2007-10-28
Can anyone who is using the windows drivers with ndiswrapper confirm that the switch on the front of the case for turning the wireless on and off works. With the serialmonkey driver the led is turned on and off but the radio itself is always on.

Thanks,
Dragon

---

### Post by dragon76 on 2007-10-28
I'm in luck. The inf, cat, and sys files for the rt73 are in the drivers/wlan directory on my everex restore dvd. I'll give ndiswrapper a go when I hear if the front hardware switch works.

Dragon

---

### Post by lawr_rawr on 2007-10-28
Dragon, you are in luck! The wireless switch on the front works! It takes a moment before NetworkManager notices and indicates there's no connection. When you turn the switch back on, NetworkManager resumes the connection in about 10 seconds. Pretty cool! 

I'm going to have to tackle the ndiswrapper method with my desktop, now. I tried to use it for the first time in about a week, and it was constantly dropping and re-associating. I could get no more than 5min of uptime... using SerialMonkey drivers for RT73 for the USB wifi adapter. 

Glad to hear that ndiswrapper is working for those who've tried it!

---

### Post by dragon76 on 2007-10-28
Well, I tried ndiswrapper with both the drivers that shipped with my system and ones that I grabbed from installing the ralink drivers in an xp install. Both were a no go. I think it might be because I am running 64bit. I don't have access to a windows 64bit install to try to get the 64bit version out of the ralink installer. Maybe I was doing something wrong with ndiswrapper but I don't think so. 

Has anyone had any luck getting ndiswrapper to work under 64bit?

If so, what windows driver did you use?

Dragon

---

### Post by lawr_rawr on 2007-10-28
Might be a 64bit issue... what were the errors you got with ndiswrapper?

---

### Post by borahshadow on 2007-10-28
dragon76: my brightness keys work in kde out of the box:confused::confused:
I decided to go back to 32bit for one more release for 2 reasons
I didn't have 64bit drivers for ndis and... with gutsy's new kernel there is tickless support (google it if you don't know what it is) but only in 32 bit I didn't have very accurate battery benchmarks but it seems like it helps but...
in hardy there should be no wireless glitch so no ndis and no worry about 64bit drivers, gnash will be bette,r and in the newest RC kernel there is tickless support for 64bit :):) which should make it into hardy

if anyone who decides to stay with 64 bit wants to run a battery bench mark we can agree on whether to have screen off network off etc. and then we can benckmark a 32bit tickless .

this is interesting in feisty I no many people used ndis now more are using it I wonder why

ps for 64bit ndis you would need 64bit windows drivers

---

### Post by dragon76 on 2007-10-29
I have been getting 2.5hrs. of battery life very consistantly with wireless on the whole time, brightness all the way down, and doing average surfing, spreadsheet, etc... nothing disk intensive. Please do let me know if you are getting better with the 32bit with tickless support. Extra battery is always a good thing.

I didn't get any errors from ndiswrapper. It showed that the device was found and the driver was loaded. Wireless assistant could not find any wireless devices. Ifconfig, and iwconfig showed no wlan0.

That is very interesting that your brightness keys work out of the box. Please see the launchpad report and add to it so we can help the devs track down what is going on:

[launchpad brightness bug]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337")

I am going to try to get access to a windows xp 64bit install in the next few days to get the ralink installer to puke out the 64bit drivers. Once I have them and see if they work I would be more than happy to share them as the EULA from ralink says that they are freely redistributable. If the battery life is better in 32bit I may step back to that for now if it is a big difference. Do you know if there is tickless support in the realtime kernel? I have been running 64bit RT on my desktop that is soon to replace my failed server. The only problem I have noticed with it is that it hangs when hibernating. I haven't tested since the last set of updates to see if this is still true, though. Gutsy was the first time that system ever successfully hibernated. RT kernel does seem to be a bit snappier to me. I don't truly need RT but am testing for people in our LUG that need it for CAM work and audio recording. Of course neither of them have battery life concerns.

An easy way to do battery benchmarks could be to simply post the graphs that gnome-powermanager creates.

---

### Post by dragon76 on 2007-10-29
Borahshadow: perhaps the brightness key bug only effects 64 bit kernels. Please note your kernel version when you make a reply to the launchpad bug.

I know of no differences between the Averatec and Everex other than bios. I don't have the "s" button (silent mode) it was shown in my user manual... which looks almost identical to the averatec one as well as the twinhead one for the intel version of this laptop. From my understanding and what I have learned elsewhere the header on the motherboard for the s button is present, just no switch on the case. The bios is definitely different as the Everex ships with vista. The averatec has issues with cpu stepping in vista and there are averatec users using the everex bios to fix the problem as averatec says that they do not support vista on this model and won't release a bios update. You can check the averatec forums for details.

As far a ndis or open source drivers for the wireless. I do prefer open source but not at the cost of functionality. I am using ubuntu as it is the os that best meets my needs. I do morally support open source software and try to give back to the community as much as possible. I don't feel that using the manufacturers windows driver in this case is quite as much of a moral issue as their EULA says that the drivers are freely redistributable and you are free to modify them. That is quite an open policy from a manufacturer in my opinion.

---

### Post by borahshadow on 2007-10-29
> **dragon76 said:**
> Borahshadow: perhaps the brightness key bug only effects 64 bit kernels. Please note your kernel version when you make a reply to the launchpad bug.
Maybe but when I had 64bit test install I think it worked to :confused:

> I know of no differences between the Averatec and Everex other than bios. I don't have the "s" button (silent mode) it was shown in my user manual... which looks almost identical to the averatec one as well as the twinhead one for the intel version of this laptop. From my understanding and what I have learned elsewhere the header on the motherboard for the s button is present, just no switch on the case. The bios is definitely different as the Everex ships with vista. The averatec has issues with cpu stepping in vista and there are averatec users using the everex bios to fix the problem as averatec says that they do not support vista on this model and won't release a bios update. You can check the averatec forums for details.

Strange considering the fact that I have a sticker that says vista capable and they offered free vista disks when they came out ( I have yet to take the sticker off it has not bothered me much so far)
> As far a ndis or open source drivers for the wireless. I do prefer open source but not at the cost of functionality. I am using ubuntu as it is the os that best meets my needs. I do morally support open source software and try to give back to the community as much as possible. I don't feel that using the manufacturers windows driver in this case is quite as much of a moral issue as their EULA says that the drivers are freely redistributable and you are free to modify them. That is quite an open policy from a manufacturer in my opinion.
Amen Hard to say it better :popcorn:
I've been doing all of the tests on a test install so today i'm moving my feisty install finally so I'll benchmark it when I get everything set up

---

### Post by dragon76 on 2007-11-01
Ndiswrapper is possible in 64bit with the proper drivers. I was able to get the 64bit versions of the rt73 drivers, even though they installed in system32 and programfiles (x86)... go figure, thanks ralink :confused: The file names and sizes were identical to the 32 bit ones. I ran a diff and they were different so I gave them a shot. They seem to be working just fine with ndiswrapper and the front on/off switch for the wireless now works. We will see how things work out but hopefully there won't be any issues with the random disconnects. The other day it got really anoying, I couldn't keep a connection up for more than 2-5 min. We will also see if this helps battery life when the switch is in the off position. There is no problem with hidden ssid's using ndiswrapper. Throughput is about 5 times faster than the serialmonkey driver. It could still be faster though IMO, but at least it is much more usable and will take full advantage of the 1.5M dsl. The signal strength meter reads lower now, but it is more accurate in my opinion as it more closely matches what other systems are reporting.

Next question... Has anyone tried the drivers from amd for cpu stepping and are they better than the default. AMD says that you have to have powernowd installed so they must work in conjunction with it not in place of it. Maybe just provide more steps.

Dragon

---

### Post by jabeez on 2007-11-01
Hey all, kinda off topic, but I wanna hook this thing up to my upstairs TV to watch stuff of my mythbox downstairs, and the only input left on my TV is s-video, whereas this thing only has VGA out. I've been to both local Radio Shacks and their only solution was a $100 "converter box", but I've looked online and found VGA to S-video/RCA cables for about $5. Has anyone done any tv-out with this thing?

---

### Post by jabeez on 2007-11-02
back again, this time back on topic:) does anyone have the XP wireless drivers that they can email me? I tried using ndiswrapper with the Vista drivers, but it's not working, and the download from Averatec for XP is an exe, which I'm not sure how you extract drivers from one of those.........

---

### Post by borahshadow on 2007-11-02
k just an update on new occurrences with this laptop
using ndiswrapper I actually had one of those disconnects but it was also under some extreme cases (transferring ~ 45GB of files and an uptime on ~1 day)
dragon- I just thought of something that might throw off the battery benchmarks my laptop is now just over 11 months old (one year on the day after thanksgiving) so my battery I'm sure has aged some :(

jabeez- I suppose I can email yo some 32bit drivers (if someone can confirm this is fine I couldn't find the licence (probably in side the exe) but I don't know if there has been a new version of the drivers mine are kinda old (like from edgy/feisty) so maybe someone else should send you theirs? maybe that is why my network disconnected after ~1day
as for the kmilo sound issue I might just download the feisty deb from the feisty repos (as said on the bugreport) or wait a little while and try the gutsy ones)

---

### Post by lawr_rawr on 2007-11-03
> **borahshadow said:**
> k just an update on new occurrences with this laptop
using ndiswrapper I actually had one of those disconnects but it was also under some extreme cases (transferring ~ 45GB of files and an uptime on ~1 day)


I haven't been able to match you for uptime (never leave my laptop on that long!) but I have noticed that wifi doesn't always work after I resume from suspend. When your connection dropped, did you have to cold boot (as we did with default Gutsy drivers) or did you simply restart networking? The few times I lost my connection after suspend, I was able to restart networking (sudo /etc/init.d/networking restart) and restart NetworkManager to get a working connection without rebooting.

---

### Post by lawr_rawr on 2007-11-03
Here's the EULA for the Windows Ralink drivers:
	> ==========================================================
	RALINK Wireless Utility for Windows 98/ME/2000/XP
	Copyright (C) RALINK TECHNOLOGY, CORP. All Rights Reserved.     
	==========================================================

Thank you for purchasing RALINK Wireless product! 

SOFTWARE PRODUCT LICENSE
The SOFTWARE PRODUCT is protected by copyright laws and international copyright treaties, as well as other intellectual property laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.

1. GRANT OF LICENSE. This End-User License Agreement grants you the following rights:Installation and Use. You may install and use an unlimited number of copies of the SOFTWARE PRODUCT.

Reproduction and Distribution. You may reproduce and distribute an unlimited number of copies of the SOFTWARE PRODUCT; provided that each copy shall be a true and complete copy, including all copyright and trademark notices, and shall be accompanied by a copy of this EULA. Copies of the SOFTWARE PRODUCT may be distributed as a standalone product or included with your own product.

2. DESCRIPTION OF OTHER RIGHTS AND LIMITATIONS.

Limitations on Reverse Engineering, Decompilation, and Disassembly. You may not reverse engineer, decompile, or disassemble the SOFTWARE PRODUCT, except and only to the extent that such activity is expressly permitted by applicable law notwithstanding this limitation. 

---------------------------------------------------------------------------
NOTICE
---------------------------------------------------------------------------

Hardware Requirements
---------------------------------------------------------------------------
You must have an RALINK Wireless product.

Software Requirements
---------------------------------------------------------------------------
RALINK Wireless Utilities can be installed on computers running 
Windows 98, Windows ME, Windows 2000, and Windows XP.

RALINK Contact Information
---------------------------------------------------------------------------
RALINK TECHNOLOGY, CORP.

Marketing Info:
Address  : 4F , No. 2 , Technology 5th Road, Hsin-Chu Science Park, Hsin-Chu, Taiwan, ROC
Telephone: +886-3-567-8868
Fax      : +886-3-567-8818
Email    : [email]sales@ralinktech.com.tw[/email]

On the RALINK Web Site you can find the most recent device drivers, 
software updates and user documentation.
WWW:       [http://www.ralinktech.com.tw](http://www.ralinktech.com.tw)

---

### Post by borahshadow on 2007-11-03
> **lawr_rawr said:**
> I haven't been able to match you for uptime (never leave my laptop on that long!) but I have noticed that wifi doesn't always work after I resume from suspend. When your connection dropped, did you have to cold boot (as we did with default Gutsy drivers) or did you simply restart networking? The few times I lost my connection after suspend, I was able to restart networking (sudo /etc/init.d/networking restart) and restart NetworkManager to get a working connection without rebooting.
I usually never keep it on that long but where I was transferring that much data I had to leave it on over night and while I was at school
I don't think I had to cold boot I think I just rebooted but I didn't know that command. I tried removing the ndiswrapper module and putting it back in (which it let me do) but that didn't help.

The EULA sounds like I have to send the .exe too which I no longer have :(
actually jabeez do you still have a windoze partition if so just install the xp drivers (see if they will install in vista they probably won't work) but see if you can trick it into installing and spitting out the files that you need

> Next question... Has anyone tried the drivers from amd for cpu stepping and are they better than the default. AMD says that you have to have powernowd installed so they must work in conjunction with it not in place of it. Maybe just provide more steps.
from the AMD site> This driver is already included in the 2.6.18 or later kernels and does not need to be downloaded again.
I believe that was edgy

---

### Post by paulsiu on 2007-11-08
Hi, 

Ever since i installed Ubuntu 7.10 Gutsy Gibbon, I have been able to suspend to RAM only if I enable the restricted drivers. However, I notice the following problem if I do the following:

1. With the restricted driver installed. Select Suspend to RAM or Supend to disk.
2. resume from suspend
3. logout of the user.

My screne went from 1280x800 to 1024x768, but now the screen shrinks to that size. 

Anyone encounter this problem?

Thanks

Paul

---

### Post by borahshadow on 2007-11-11
Hmm I think I have a serious problem :(:(:(
I noticed that a few times my screen went garbled and I had to hard power off (ctrl-alt-backspace didn't work). I thought this was probably a glitch in the video driver.  Well the other day it happened again and I tried every key combo I could think of nothing worked so I hard powerd off again, but when I went to turn it back on the leds turned on but the screen was black.  I tried this a few more times with the same results finally noticing that the bottom was hot.  I feared that I had fried my CPU so I threw my laptop in the fridge. In a few minutes I took it out and every thing booted up fine but I just had time to log in before it did it again.  Wondering if my fan had problems I ran the fan calibration in the bios and decided to let it sit over night before I used it again. Today I needed to type something so I booted it up and before too long it did it again but I also noticed my fan was not spinning at all :confused:.  Now I wonder if the fan is software controlled or hardware controlled.  I have left this on for ~1day with gutsy while copying lots of files which usually makes my fan spin decent but all of a sudden this has started happening.  Does anybody think it could be hardware failure because the fan worked fine during calibration.
I don't want to send it in for warranty or even know if I can.
I don't think I have any papers for warranty and I have upgraded the ram which ruined the little warranty void sticker (however averatec claims the just the ram won't void the warranty) if I do I need to send it in soon as I bought it 1 year ago on the day after thanksgiving

---

### Post by borahshadow on 2007-11-11
I removed the back plate(this won't void the warranty anymore since I already did it to change ram) and removed every bit of dust that I could with compressed air I then booted back up I noticed when the bios had control that the fan spun but while it was booting up (linux control) the fan didn't I didn't notice if it was as soon as it loaded the kernel or not.
I tried to get lm sensors set up but didn't have time before it did it again here are some pictures I took of the scrreen

EDIT: it happens as soon as the (k)ubuntu splash screen comes up I'm going to leave it off now till I figure out what is wrong

---

### Post by trizuk on 2007-11-11
how did you guys fix the wifi problem and the headphone problem where the music plays from the headphones and the speakers? i am having lots of trouble. btw i am on an evetex st5340t

---

### Post by borahshadow on 2007-11-11
> **trizuk said:**
> how did you guys fix the wifi problem and the headphone problem where the music plays from the headphones and the speakers? i am having lots of trouble. btw i am on an evetex st5340t
Wireless: Ndiswrapper or official (no GUI)
Headphones: you have to manually turn off the fron speakers in the volume control don't know how in gnome

ok I just found that there is a new onofficial averatec forums and there were some people who described problems like mine except it was only the not turning on part anyway I put my original ram back in and ubuntu turns on the fan now :)
I got lm sensors installed and my cores average ~50C which is what they normally do so I'm happy there but I just had a weird problem where my touch pad quit but I'll see if it happens again (man all the problems happen at once )

EDIT now my cores are down ~ 5-10C yay

EDIT I just put my 2GB of ram back in and every thing is fine so far fan works and cores are same temp. :D

---

### Post by trizuk on 2007-11-11
borahshadow, its good that u got your fans working correctly again.
do you have any solution for middle mouse paste? its crazily annoying.

---

### Post by borahshadow on 2007-11-11
what do you mean? do you like it or not want it?

---

### Post by trizuk on 2007-11-12
yea, i dont want it. it messes me up a lot in almost every program.

EDIT:
also i got ndiswrapper to work and everything, but it doesnt show up in the wifi manager. in the nm-applet nor the knetworkmanager. BUT it happened to connect to my wifi.

---

### Post by trizuk on 2007-11-12
sorry for double post

ndiswrapper stops after a while as well. no one else has this issue?

---

### Post by paulsiu on 2007-11-12
> **paulsiu said:**
> Hi, 

Ever since i installed Ubuntu 7.10 Gutsy Gibbon, I have been able to suspend to RAM only if I enable the restricted drivers. However, I notice the following problem if I do the following:

1. With the restricted driver installed. Select Suspend to RAM or Supend to disk.
2. resume from suspend
3. logout of the user.

My screne went from 1280x800 to 1024x768, but now the screen shrinks to that size. 

Anyone encounter this problem?

Thanks

Paul

I am surprise that no one has this problem. I have verified that this happened in Fedora 8 as well. I am currently tracking down the cause of the issue. It am currently theorizing that when I resume, the monitor's EDID is read incorrectly. I may move this to a different thread due to a lack of interest.

Paul

---

### Post by borahshadow on 2007-11-13
> **paulsiu said:**
> I am surprise that no one has this problem. I have verified that this happened in Fedora 8 as well. I am currently tracking down the cause of the issue. It am currently theorizing that when I resume, the monitor's EDID is read incorrectly. I may move this to a different thread due to a lack of interest.

Paul

Well Honestly I'\ Neer have had it because I only log out to shut down normally because I'm the only user

I've only had ndiswrapper quit after ~1day

For the third mouse paste I don't know how to in gnome try to find your clipboard manager in kde it is kilpper there should be a way to change it there personally I love it and mess up when I don't have it on a win computer

---

### Post by paulsiu on 2007-11-13
> **borahshadow said:**
> Well Honestly I'\ Neer have had it because I only log out to shut down normally because I'm the only user

I've only had ndiswrapper quit after ~1day

For the third mouse paste I don't know how to in gnome try to find your clipboard manager in kde it is kilpper there should be a way to change it there personally I love it and mess up when I don't have it on a win computer

Well, I have been experimenting in Fedora 8 and figure out the cause of the problem with the screen, but I am pretty sure that this applies to Ubuntu (I'll double check later when I switch to Ubuntu again). 

Normally, Xorg reads the EDID from the LCD monitor and display the correct 1280x800. The problem is that when I logout after a suspend or hibernate, the EDID gets scrambled and defaults to a 1024x768 screen. To correct the problem, I save the EDID of the monitor when it was good and then use it as a custom EDID in xorg.conf. This works like a charm. I haven't had an issue with shrinking screen since.

---

### Post by Ru$$i@N on 2007-11-19
ooookaaaaay :???:
seems like my previous post got ignored.
Once again. When I boot, right after the grub menu I see white lines spasming all over the screen. Then the splash screen appears and everything goes to normal. Same when I shut down my averatec. Don't know why this happens, but it doesn't on my other machines.

Does anyone know what i'm typing about ? :confused:

---

### Post by borahshadow on 2007-11-19
sorry I don't think I know those lines so I guess I can't help (but at least your not ignored again sorry)

---

### Post by Ru$$i@N on 2007-11-20
> **borahshadow said:**
> sorry I don't think I know those lines so I guess I can't help (but at least your not ignored again sorry)
thanks anyways

---

### Post by Captain Klunk on 2007-11-20
> **paulsiu said:**
> Well, I have been experimenting in Fedora 8 and figure out the cause of the problem with the screen, but I am pretty sure that this applies to Ubuntu (I'll double check later when I switch to Ubuntu again). 

Normally, Xorg reads the EDID from the LCD monitor and display the correct 1280x800. The problem is that when I logout after a suspend or hibernate, the EDID gets scrambled and defaults to a 1024x768 screen. To correct the problem, I save the EDID of the monitor when it was good and then use it as a custom EDID in xorg.conf. This works like a charm. I haven't had an issue with shrinking screen since.

Hi,

I too am having the "shrinking screen" problem.  I have a Averatec 2370 running Fedora 8.  Hey  paulsiu if it is not to much trouble could you post the steps you used to save off the EDID and then use that in the xorg.conf.  

Thanks ...

---

### Post by paulsiu on 2007-11-21
> **Captain Klunk said:**
> Hi,

I too am having the "shrinking screen" problem.  I have a Averatec 2370 running Fedora 8.  Hey  paulsiu if it is not to much trouble could you post the steps you used to save off the EDID and then use that in the xorg.conf.  

Thanks ...

I'll have to get back to you on that one. I thought the EDID was being read properly, but when I attempted to read it using get-edid, I got an error. I may have to copy the EDID file 
from Fedora.

In Fedora, I got the EDID from the Nvidia driver settings. I don't know where that is in Ubuntu? Anyone?

Paul

---

### Post by paulsiu on 2007-11-21
> **Ru$$i@N said:**
> ooookaaaaay :???:
seems like my previous post got ignored.
Once again. When I boot, right after the grub menu I see white lines spasming all over the screen. Then the splash screen appears and everything goes to normal. Same when I shut down my averatec. Don't know why this happens, but it doesn't on my other machines.

Does anyone know what i'm typing about ? :confused:

The white stuff may be from video hardware initializing or deinitializing. I get bits of it initially. Have you try booting with the parameter vga=0 or vga=785.

For some more code for VGA mode, see:
[https://nanders.com/forum/viewtopic.php?p=360&sid=290dbe5d7db11f5d1688daa23449fc04](https://nanders.com/forum/viewtopic.php?p=360&sid=290dbe5d7db11f5d1688daa23449fc04)

---

### Post by paulsiu on 2007-11-21
> **paulsiu said:**
> I'll have to get back to you on that one. I thought the EDID was being read properly, but when I attempted to read it using get-edid, I got an error. I may have to copy the EDID file 
from Fedora.

In Fedora, I got the EDID from the Nvidia driver settings. I don't know where that is in Ubuntu? Anyone?

Paul

You know this is really frustrating. I try to use the option UseEDID "False", but then my screen is blank. I notice that it said my Modeline is invalid and is removing it. I haven't figure out how to turn off the sanity check for that validation. Grr...

Paul

---

### Post by paulsiu on 2007-11-21
Captain Klunk,

I finally figured it out. Here's the steps to fix the screen shrinking problem.

1. Login as a user who can Sudo.
2. Open a command window.
3. Enter the command gksudo nvidia-settings. This brings up the Nviidia settings app.
4. Click on the DFP-0 - (Seiko) and click on the Acquire EDID button. Save it somewhere. I saved mines at /etc/X11/SeikoEdid.bin.
5. Sudo edit /etc/X11/xorg.conf and add the following line to your monitor section:

Option "CustomEDID" "DFP-0:/etc/X11/SeikoEdid.bin"

Now if you suspend/hibernate and then logout, the screen will not shrink.

**What's happening?**
What appears to be happening is that when you boot up the machine, Xorg read the monitor EDID correctly and display the correct monitor settings. After a suspend or hibernate, it also tries to read the EDID. This time, it cannot so it uses the Nvidia default screen, which is smaller than 1280x800. As a result, the screen shrinks.

The work around saves the EDID information to a file, the CustomEDID loads the EDID from this file instead of the device, which works around the problem.

---

### Post by borahshadow on 2007-11-21
I've been experimenting to try to get network to work after suspend but no luck it still quits working almost every time
what I tried is in /etc/default/acpi-support I tried adding ndiswrapper to the module white list and the list of modules to load and unload but it didn't seem to help maybe some of you guys can try it and see if it helps :)

it kinda sticks that network fails basically every time

---

### Post by Captain Klunk on 2007-11-21
> **paulsiu said:**
> Captain Klunk,

I finally figured it out. Here's the steps to fix the screen shrinking problem.

1. Login as a user who can Sudo.
2. Open a command window.
3. Enter the command gksudo nvidia-settings. This brings up the Nviidia settings app.
4. Click on the DFP-0 - (Seiko) and click on the Acquire EDID button. Save it somewhere. I saved mines at /etc/X11/SeikoEdid.bin.
5. Sudo edit /etc/X11/xorg.conf and add the following line to your monitor section:

Option "CustomEDID" "DFP-0:/etc/X11/SeikoEdid.bin"

Now if you suspend/hibernate and then logout, the screen will not shrink.

**What's happening?**
What appears to be happening is that when you boot up the machine, Xorg read the monitor EDID correctly and display the correct monitor settings. After a suspend or hibernate, it also tries to read the EDID. This time, it cannot so it uses the Nvidia default screen, which is smaller than 1280x800. As a result, the screen shrinks.

The work around saves the EDID information to a file, the CustomEDID loads the EDID from this file instead of the device, which works around the problem.

Works perfectly ... thanks! ... 

I also noticed that my normal console was getting corrupted after a resume (CTRL-ALT-F1).  Adding "vga=0f00" to the grub kernel boot parameters seems to have sorted out that problem.  Now if only I could get wireless and sound to work after a resume ... then I would be in business.

---

### Post by borahshadow on 2007-11-21
my sound works but I'm in kde and you can try what I posted above for network that is all I need

---

### Post by pwithem on 2007-11-27
Perhaps changing the subject here a bit, but I've been having some compiz issues.  Basically, I wasn't sure how to get effects such as desktop cube, etc. to work.  After installing everything under the sun (emerald, xgl, anything compiz-fusion related that wasn't already installed) I found that I need to type "compiz" with perhaps an option in an xterm window - or have some startup script.  Then I found that most things would work and I just had to play with ccsm.  Some things did not work however.  

First major problem:  booted up and I got white screen.  I had mouse control and I could rotate the desktop, but everything was white.  By this point, compiz was starting up automatically (cause it was up when I last shut down?), so I was thinking I need to find a startup config file somewhere and tell it to stop running compiz.  I could not find (using non-graphical interface) this.  Then I looked for a compiz config file (what ccsm would create) - although I found many candidates, I couldn't find anything that contained the info I thought it should have.  

Second major problem:  eventually I booted back into X for fun.  Interestingly, I get no compiz, but my xorg.conf has somehow been rewritten!  Now it uses a virtual resolution and it's not at 1280x800.  I cannot restore my 1280x800 resolution because the modeline is now missing. Nvidia drivers load ok though.  Also, the only thing on screen is an xterm window without any border, so I can't move it.  There is no task bar or anything else on the screen.  If I start a new program via the xterm window, it also has no border and just sits there.

So, unless anyone has a silver bullet for my situation, can anyone tell me if there is a "startup" config file, a compiz config file (one containing all the information presented with ccsm), and can someone past me a modelilne for 1280x800?  Thanks!

---

### Post by pjones0404 on 2007-12-02
i am not sure about the issues that you are having with compiz. i use gnome and was able to use the restricted driver and have not had any issues yet.

I do have a separate question though. i am looking to purchase a bluetooth dongle and am curious if anyone out there has a recommendation on one that they use. are there any particular ones that i should avoid or are they all pretty much the same? i would like to use a mouse, my cell phone as a modem, and maybe some headphones if i could get them to work.

thanks.

---

### Post by lawr_rawr on 2007-12-03
Bluetooth adapter: I have a Hawking HBTC2. It worked straight away -- I just had to install a utility for OBEX support for my phone. I have not tried it with any other peripherals, just a Pantech C3b and a Blackberry 8830 for OBEX transfers. 

[Here's the link to Hawking's site.]("http://www.hawkingtech.com/products/productlist.php?CatID=19&FamID=55&ProdID=287")

---

### Post by pwithem on 2007-12-05
I'm using kubuntu, for which I understand some things are just different...

---

### Post by jsweds on 2007-12-08
Recently, I've been unable to connect to new wireless networks with NetworkManager.  I can still connect to the networks I connected to before this started happening.  I'm using ndiswrapper.  Has anyone else seen this happen?  The networks I've been trying are simple unencrypted networks at coffee shops.

---

### Post by borahshadow on 2007-12-08
Yes I had this problem in feisty too with ndiswrapper in feisty I just closed out network manager and used wireless assistant (kde app probably similar for gnome.
I don't have that installed right now and am actually connected to a network network manager wouldn't I just had to go and configure it in the system settings under network (in kde just click on network manager and click configure manually). Network manager .7 should fix some of these things (technically it is still betaish because it is under version 1)

While I'm posting I might mention that I've had some more of those weird overheats again. once was during some intense encoding and a few of the others have just been random. weird because when it overheats the fan is not spinning so sometimes the fan works and other times it does not so mabey my fan is actually bad. But no noticeable damage from them if I turn it off with the power key.

---

### Post by Ru$$i@N on 2007-12-09
> **paulsiu said:**
> The white stuff may be from video hardware initializing or deinitializing. I get bits of it initially. Have you try booting with the parameter vga=0 or vga=785.

For some more code for VGA mode, see:
[https://nanders.com/forum/viewtopic.php?p=360&sid=290dbe5d7db11f5d1688daa23449fc04](https://nanders.com/forum/viewtopic.php?p=360&sid=290dbe5d7db11f5d1688daa23449fc04)

Sorry I haven't respond in 2 weeks.
Thanks for the link. I tried booting with those options, but I still got the same results. However, i tried booting without the splash option. I did get a result - no white lines anymore, no pretty splash screen either :)) oh well, i didn't really need it anyways. NO annoying white lines though. :)

---

### Post by paulsiu on 2007-12-10
> **Ru$$i@N said:**
> Sorry I haven't respond in 2 weeks.
Thanks for the link. I tried booting with those options, but I still got the same results. However, i tried booting without the splash option. I did get a result - no white lines anymore, no pretty splash screen either :)) oh well, i didn't really need it anyways. NO annoying white lines though. :)

I am thinking that the white lines may be unavoidable. They probably appear when the video hardware reinitialize.

---

### Post by paulsiu on 2007-12-10
One annoying problem is that the wireless cuts out mysteriously. It seems to work perfectly fine for a while and then suddenly lose connection. After suffering this a few times, I decided that I have had enough. I downloaded the latest serial monkey driver. Compile and installed it, but it did not work.

After some experimentation, it appears that the driver does not work with Network manager, I have instead have to download an additional utility RTUTIL and then compile that. The utility has some quirks. I think it only scans if you have root permissions. 

In any case, the new driver is far more stable, even if it does not work with network manager. I have been connected for an entire day without a single disconnect problem.

Paul

---

### Post by madman18 on 2007-12-18
Hello Guys,

I'm brand new to this forum and have some experience with linux.  I'm hoping someone could help me resolve an issue I'm having with my wireless.  I've read through the forum and am familiar with the supported driver dropping connections.  Because of this I am currently using the windows driver.  My issue is that after suspend my wireless devise is no longer active.  Is there a way I can reinitialize the device without restarting?  Thanks in advance!

---

### Post by borahshadow on 2007-12-22
> **madman18 said:**
> Hello Guys,

I'm brand new to this forum and have some experience with linux.  I'm hoping someone could help me resolve an issue I'm having with my wireless.  I've read through the forum and am familiar with the supported driver dropping connections.  Because of this I am currently using the windows driver.  My issue is that after suspend my wireless devise is no longer active.  Is there a way I can reinitialize the device without restarting?  Thanks in advance!
Unfortunantly I have not got wireless to work after suspend ether sorry maybe in Hardy we will not have to use the windows driver (ndiswrapper) and the native I'd expect would work on suspend

Speaking of Hardy I just installed kubuntu hardy alpha 2 and thought I'd give a small report.
This is the first time I've installed a release this early but everything seemed fine for alpha 2. Kubuntu does not have a restricted drivers manager as of alpha 2 yet. The volume keys still are the same (they don't work).  Wireless works but I have not tested to see in it drop's connections but at least it has not regressed and become totally broken. 
I hopped that I would not have these strange overheats(hoping that is was a software issue) but I still experienced one. This time the fan was spinning but not fast which was obviously not fast enough. Has no one else ever had on of these overheats? It must be a fan problem except the fan works fine most of the time it just seems to be occasionally that it does not spin of does not spin fast enough and yes I have run the fan calibrator in my bios which seems to work fine.

Anyway that is the news for hardy so far I need to go check if suspend works

---

### Post by dragon76 on 2008-01-07
GOOD NEWS!!!!!  \\:D/

I have been running Hardy since alpha1. The wireless drivers now appear to be fixed. I have not had a disconnect over the last several days since trying the new ones. I will keep you posted.

The brightness keys are also now working fine in KDE.

The volume keys also have been fixed.

Thank you Hardy development team =D>

---

### Post by dragon76 on 2008-01-07
borahshadow:

KDE does have a restricted driver manager. If it does not pop up automatically when it sees your nvidia controller (it did for me, both when installing alpha1 and when upgrading to 2.6.24 kernel) you can go to system setings, go to the Advanced tab and click on "restricted drivers."

The volume keys are working as of updates a few days ago.

As far as the overheat... I have the 1.7GHz x2 in my everex and have experienced no overheat issues even when transcoding raw dv to ffv1. I run an applet called Kima in my KDE panel. I use it to display cpu clock, nvidia temp, cpu temp (average between the 4 sensors) and hdd temp. The nvidia runs hotter than I like and the hdd does also but I have not seen any true overheat issues.

I am not sure if wireless works after suspend, or suspend its self for that matter. I could use iwpriv to reset the ndiswrapper after suspend when using ndiswrapper under gutsy, but I never had any luck with serialmonkey drivers doing the same that I can recall.

Battery life is awesome in hardy thus far. I have been getting a good 3hrs on average use with the wireless on (hardware switch doesn't work with serialmonkey drivers). You could possibly even get better as I was able to get better battery life out of gutsy after some tweaking. I haven't tried any tweaking in hardy yet as I am already getting a bit better than gutsy was after I played with it.

I haven't tried accessing a wireless network with hidden essid yet.

Under gutsy I had a few networks that I could only use wlassistant to connect to and a couple that I could only use network manager to connect to... I never did figure out why, and this was the case with both ndiswrapper and serialmonkey drivers. I haven't been to the networks that required wlassistant in over a month so I can't report on the status of the issue in hardy.

The last update to the nvidia restricted drivers (about 2-3 days ago) makes the screen go funky when resuming from dpms screen blanking. It can be fixed by going to a virtual terminal (i.e. ctrl-alt-F1) and switching back (ctrl-alt-F7). The big problem is that the virtual terminals experience this problem at ALL times, so they are useless. 

Alpha is an interesting ride. The number of updates has slowed down recently but when I first installed alpha1 it was typical to see 80+ updates per day.

Happy Hacking
Dragon

---

### Post by dragon76 on 2008-01-07
I finally got a chance to try accessing a wireless network with a hidden essid in Hardy 8.04 alpha.

Wireless networks with hidden essid's are now accessible using wlassistant but still not when using knetworkmanager. \\:D/

---

### Post by borahshadow on 2008-01-07
This will Sound realy weird but it makes me almost sad to be hearing such good news last friday my wonderful lappy died :(:mad::(:(:(
I don't know if It has anything to do with the overheats but I suspect that my hardware decided to crap out which caused both problems.

I noticed had my laptop on doing some things and looked away to do something else for a minute when I looked back it looked like the screen had turned off so I moved my finger on the touch pad and it would not respond I tried ctrl-alt-bkspace nothing so I was forced to hard power it off on trying to power it back on it would not it would just sit there with the power light on. I didn't know if it was an overheat that caused the screen to turn off because it normally just garbles what is on the screen. Anyway I've had it do this after it overheats before so I was not worried at this point but the next morning after it would have cooled down it was doing the same thing this is when I realized it probably died. Now I've got to get with averatec and see what it will cost to get it fixed.  It conveniently waits 1 month after my warranty expires to die. I looked on google and the unofficial averatec forums and there seem to be other people with the same problem.  Looking back when It first started acting up I should have got on the horn with averatec and at least got on there logs before my warranty was up.  I would encourage any of you to do the same at the slightest glitch get on there logs (everex or averatec) before your warranty is up. It is much more likely to get them to fix your laptop if it is barely out of warranty if you've been on their logs before your warranty was up.

Dragon: I used to be able to encode large things too. My laptop started doing this at about age 11months yours is still a lot newer so it makes sense that yours still works fine. It started with one or two spaced far apart and they were still nice and rare when my warranty expired leading me in to a false sense of security that everything was fine but after my warranty expired they got worse until this.

So congrats on everything working fine so far I feel bad I can't help test anymore buthopefully I can get my lappy fixed before the final release in time for beta (I'm already having a struggle without it). 
So sorry that you all had to read my sad story but maybe if your laptop acts up in any way you can learn from my mistake and send that sucker in.

Bye

---

### Post by dragon76 on 2008-01-07
borahshadow: If you can't get it fixed under warranty and you want another one and are in the USA you can try officemax.com. They have the Everex for $549. Newegg.com has the intel celeron version of the Everex but I am not sure about the AMD It is possible just the cpu is damaged, which is an easy to replace component, and not too expensive either.

---

### Post by borahshadow on 2008-01-07
Thanks I'm aware of the everex at officemax but I'm also just thinking about going without long enough to save up for a nicer laptop such as a Dell of HP  but I am considering the everex at officemax

---

### Post by dragon76 on 2008-01-14
Just an update on Hardy progress with our friendly little laptops.

The nvidia restricted drivers are still broken in Hardy alpha in regards to the glitch when returning from DPMS off state and the virtual terminals being unusable. The wireless has not disconnected on me once though. Networkmanager is now able to connect to the two networks that I used to have to use wlassistant for. Wireless now works after returning from suspend. I have not tried the wireless after returning from hibernate yet but suspect it should work also. I am using the default serialmonkies drivers. My only complaint on them is that throughput seems to be a bit low. The new nvidia driver supports underclocking for the graphics processor but doesn't seem to want to work on my laptop, perhaps a bios issue? Never the less I have been getting over 3 hours of battery life with wireless on and no special tweaking to the os.

Dragon

---

### Post by borahshadow on 2008-01-17
Hi
well I'm no farther towards a new laptop I'm a little reluctant to but an almost identical everex as it could have the same or similar problem. I have a question does anybody see any problem plugging my laptop HDD into my desktop? My desktop has SATA which is nice and it has an Nvidia 6100 on board video. I thought I might have to blacklist ndiswrapper but realized I never had a problem with ndiswrapper loading when the network bug (now Gone :)) made my network card disappear.

---

### Post by jsweds on 2008-01-18
> **jsweds said:**
> Recently, I've been unable to connect to new wireless networks with NetworkManager.  I can still connect to the networks I connected to before this started happening.  I'm using ndiswrapper.  Has anyone else seen this happen?  The networks I've been trying are simple unencrypted networks at coffee shops.

I got wireless working again by using wicd ([http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")) instead of network manager.

---

### Post by jabeez on 2008-01-26
> **borahshadow said:**
> Hi
well I'm no farther towards a new laptop I'm a little reluctant to but an almost identical everex as it could have the same or similar problem. I have a question does anybody see any problem plugging my laptop HDD into my desktop? My desktop has SATA which is nice and it has an Nvidia 6100 on board video. I thought I might have to blacklist ndiswrapper but realized I never had a problem with ndiswrapper loading when the network bug (now Gone :)) made my network card disappear.

You mean the network bug is now gone in upcoming Hardy? My connection still (totally randomly) drops and takes out my wireless adapter with it, using standard drivers. Sometimes it lasts for as long as I need it, even coming back after suspend, other times it lasts a matter of minutes. Pretty frustrating, hope it's ironed out soon, it's sooooo close.........................

---

### Post by borahshadow on 2008-01-26
> **jabeez said:**
> You mean the network bug is now gone in upcoming Hardy? My connection still (totally randomly) drops and takes out my wireless adapter with it, using standard drivers. Sometimes it lasts for as long as I need it, even coming back after suspend, other times it lasts a matter of minutes. Pretty frustrating, hope it's ironed out soon, it's sooooo close.........................

Yes according to dragon
> ...The wireless has not disconnected on me once though. Networkmanager is now able to connect to the two networks that I used to have to use wlassistant for. Wireless now works after returning from suspend. I have not tried the wireless after returning from hibernate yet but suspect it should work also. I am using the default serialmonkies drivers. My only complaint on them is that throughput seems to be a bit low...
Just look at the last several posts on page 37

---

### Post by borahshadow on 2008-02-03
Hi everybody
First off My laptop is back (I think/hope) see [[COLOR="Blue"]_the bottom of this_[/COLOR]]("http://www.averatec-forums.com/index.php?topic=209.0") if you care
Next I think I got networking to work after suspend :) I've suspended 3 times in a row and networking still works.

I found this page [https://help.ubuntu.com/community/WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") I noticed the section on suspend so I went ahead and did it this is what I did.
First I ran ```
sudo nano /etc/acpi/suspend.d/07-network-manager.sh 
``` and then pasted ```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
``` and then exited with ctrl-x and enter
then ```
sudo nano /etc/acpi/resume.d/63-network-manager.sh 
``` and pasted ```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start
```
and exited with ctrl-x and enter

Then make them executable run ```
sudo chmod +x /etc/acpi/suspend.d/07-network-manager.sh 
```
and```
sudo chmod +x /etc/acpi/resume.d/63-network-manager.sh
```

Hopefully network will work after a suspend. I did notice When I come back from suspend I must click on my access point to connect and then shortly it will disconnect just do it again and it should stay connected the second time. That is much better than rebooting.

EDIT: well it is not as reliable as I first thought but it is still better than what I had before which was the network is toast after suspend. Oh and my laptop died again I think I can get it up again after 3 hours (read the link to my problem if you want an explanation) but it is frustrating to have it unreliable

---

### Post by jabeez on 2008-02-07
> **borahshadow said:**
> 
Hopefully network will work after a suspend. I did notice When I come back from suspend I must click on my access point to connect and then shortly it will disconnect just do it again and it should stay connected the second time. That is much better than rebooting.

EDIT: well it is not as reliable as I first thought but it is still better than what I had before which was the network is toast after suspend. Oh and my laptop died again I think I can get it up again after 3 hours (read the link to my problem if you want an explanation) but it is frustrating to have it unreliable

Well getting networking back after suspend works fine for me with default drivers (Kubuntu), but who knows how long the connection will last still...............

---

### Post by lawr_rawr on 2008-02-13
Farewell, Averatechies! This thread was so useful for me since the days of Feisty, but now I'm movin' on. I just got a new Dell XPS M1330, and promptly zapped Vista. It's quite a nice machine, and everything works perfectly with Ubuntu... so if anyone is fed up with their fried Averatec, you might want to go Dell. 

Participating in this thread was a great learning experience. Thanks guys!

---

### Post by dragon76 on 2008-02-20
Hardy is shaping up nicely everyone. Everything is working "out of the box"

The Good!
- brightness keys work in kde
- volume keys work in kde
- in fact all of my function keys are working (I don't have the "s" key that is on the averatec)
- wireless works good, no more disconnects and works after suspend throughput is just a bit low
- hidden essid wireless networks no longer a problem
- no longer need to use wlassistant to connect to certain networks
- Good battery life - I get 3+ hours with brightness down and wireless on

The Bad :(
- nvidia drivers still broken making virtual terminals useless unless x-server is not running, things are so stable (this alpha is better than xp) that I haven't needed a virtual terminal since they were broken though
- bugs still being worked out with java/firefox

Just ask if there is an issue I have forgotten to comment on.

---

### Post by Joshua on 2008-03-09
Does anyone know how to get the Fn-F5 key to work.  I want it to work the way it would work in Windows by default.  Well, I want it to work better than Windows.

First off, I don't want to extend my desktop with it.  I want to be able to hit it once to switch to an external screen and view my normal desktop with a resolution that is appropriate for the external screen.  Then I want to be able to hit it again to view both my laptop screen and the external screen, each with the correct resolution.  Then I want to be able to hit it again to switch back to just the laptop screen in the correct resolution.

Any Ideas?

---

### Post by dragon76 on 2008-03-10
I think I have the modem WORKING!!!!!!!!!!! \\:D/ I got my cell phone to work as a modem a month ago. Yesterday I hacked around working on the internal modem. Last night I appeared to have it working. I will do a bit more testing and write up a how-to to post in the thread.

A special thanks to Borahshadow for this. He sold me his dead 2300 and because I disassembled it I was able to actually get the physical modem to inspect and could go from there. If anyone needs some parts let me know I may have some from this 2300.

Joshua: That hotkey has been working for me since gutsy beta. I have had some struggles with getting screen resolutions right with certain versions of the nvidia driver. Also the projector where we have our local lug meetings gives me fits every single time. Otherwise it always switches... the resolution just sometimes takes some screwing around with for that projector. I have found using the nvidia-settings application to be the most reliable way to set things.

Dragon76

---

### Post by dragon76 on 2008-03-10
The internal modem functions as the laptop equivalent of an AMR modem. It is software based and actually an extension of the audio portion of the nvidia chipset. The chip in the modem is a Motorola SM56 chip. Motorola released a linux driver for this chip but support was discontinued quite a while ago. It is completely compatible with the SmartLink modem drivers, though. The modem relies on both a low-level driver and a high-level driver. The low-level driver is provided by alsa which is installed by default in ubuntu. The high-level driver is provided by slmodemd. There is a version of this driver in the repositories. I however, could not get this version to work with this modem. There are newer versions of the drivers available that do work though, and the good news is that you don't even need to compile them! 8)

The driver uses 3.9MB of ram on my system. You can choose to install the driver so that it starts on boot, or to have it only running when you choose. IF YOU DO NOT WANT THE DRIVER TO START ON SYSTEM BOOT, skip down to the section "Installing the working driver".


[COLOR="Red"]**_****Installing the boot scripts****_**[/COLOR]

Using Synaptic, Adept, or Aptitude install the package "sl-modem-daemon" or:

```
sudo apt-get install sl-modem-daemon
```

This installs the version of the driver that is in the repositories that does not work for the modem card in our laptops. It also installs the scripts to automatically start the driver on system boot though and this is what we are after.

We now need to edit the file "/etc/default/sl-modem-daemon" so that it uses the correct hardware device.

You can open the file using sudo in your favorite text editor such as gedit or kate:

```
sudo gedit /etc/default/sl-modem-daemon
```

--OR--

```
sudo kate /etc/default/sl-modem-daemon
```

Next change the line

```
SLMODEMD_DEVICE=auto
```

--TO--

```
SLMODEMD_DEVICE=hw:0,6
```

Now save the file and exit your editor. This completes the setup of the scripts needed to run the modem driver on boot. Next we need to get the new version of the diver installed, the one that actually works with our modem cards.


[COLOR="Red"]**_****Installing the working driver****_**[/COLOR]

Go to _ [COLOR="RoyalBlue"] [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) [/COLOR] _ and download ["[COLOR="Blue"][COLOR="RoyalBlue"]_SLMODEMD.gcc4.2.tar.gz_[/COLOR][/COLOR]"]("http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.2.tar.gz")

or to download the file to your home directory, in a terminal type:

```
wget linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc4.2.tar.gz ~/
```

Next untar the package with ark or:

```
tar -xf ~/SLMODEMD.gcc4.2.tar.gz
```

you should now have a directory in your home directory called SLMODEMD.gcc4.2

Next we need to copy the file slmodemd to /usr/sbin this will also overwrite the outdated driver if you chose to install the package from the repositories.

```
sudo cp ~/SLMODEMD.gcc4.2/slmodemd /usr/sbin
```

To clean up you just delete the directory SLMODEMD.gcc4.2 and the downloaded tar:

```
rm -r ~/SLMODEMD.gcc4.2
rm ~/SLMODEMD.gcc.4.2.tar.gz
```

The driver is now ready to use.

If you installed the package from the repositories so that the driver starts on boot you can either reboot or:

```
sudo /etc/init.d/sl-modem-daemon restart
```

If you decided not to have the driver start on boot the driver needs to be running in order to use the modem. You either need to: have a terminal open, start the driver and leave the terminal open; or start the driver as a background process.

To start the driver:

```
sudo slmodemd -c USA --alsa hw:0,6
```

To stop the driver just type ctrl-c in the terminal window.

--OR--

To start the driver as a background process:

```
sudo slmodemd -c USA --alsa hw:0,6  &
```

You can now close the terminal or press ctrl-c to get your command prompt back. To stop the driver:

```
fg sudo slmodemd
ctrl-c
```


Now just use your favorite ppp application, such as kppp or wvdial, to connect to a remote network or isp.

If you intend to send faxes (this was my reason for getting the modem working) you need to install the "efax" package. You then need to edit the file /etc/efax.rc in the following way:

Change the line:

```
DEV=ttyS1
```

--TO--

```
DEV=ttySL0
```

I believe that this is the last hardware feature to have working on this wonderful little laptop. All of this has been tested in Kubuntu Hardy 8.04 Alpha 6. I have checked dependencies etc. and it should work equally well in Gutsy 7.10. I have no idea if it will run on older versions of ubuntu. It should also work on Debian as the sl-modem-daemon package is from upstream of ubuntu and the updated binary is universal. The binary is kernel independent. It is only dependent on having gcc4.2 installed AFAIK. There are other versions available at the above link for other versions of gcc.

If you want more info on all of this, read the txt files that are included in the downloaded tar. You can also download the scanmodem utility at the above website and read the info included, as well as that which is generated when you run the script.

Have fun!
Dragon76

---

### Post by dragon76 on 2008-03-11
Ok everyone... Time to put in a vote!

I can not find any input that the system can see when the wireless switch is moved. Since the wireless on/off switch does not work on our laptops I have decided to write a script to turn the radio on and off based on a hotkey sequence. This can help to increase battery life when not using the wireless.

Do you want me to write the script to use a hotkey combination i.e. win+F1

OR

Should I write the script to use the Fn+F4 (sleep key). I personally prefer this as it might be simpler and sleep can be accessed from the menus, powermanager, and the command line easily.

Get your vote in soon...I want to be done with this project in no more than 5 days!

Dragon76

---

### Post by thegreatrobot on 2008-03-28
I recently installed Ubuntu 7.10, and have been having all the same irritating wireless issues that lots of other people seem to be having.

One unusual trend I noticed is that the wireless tends to cut out when I try to visit certain sites; particularly facebook. I first noticed this a couple days ago then spent some time actually experimenting. About 90% of the time I visit facebook, my wireless cuts out, and I need to reboot to get it back working. So Eff you, Facebook!

Is there any reason why this should happen?

Quelle bizarre!

---

### Post by jabeez on 2008-04-02
I've got a question thats been bugging me for awhile, and after just installing Kubuntu 8.04 KDE 4, it remains as it has the last couple versions I've installed on this laptop. The issue is, after installing the Nvidia driver, the resolution reports back the correct 1280x800, but everything is BIG. It all looks great with the default driver, but the Nvidia driver does something funky. Even the KDM login screen looks much bigger than with the default driver. Any ideas? I've always used Kubuntu by the way, and have messed with forcing dpi and others that make it somewhat better, but still not quite right................

---

### Post by jabeez on 2008-04-02
bumpy for above, it's really got me stumped!!!!!:confused:

---

### Post by jabeez on 2008-04-07
Ok, so issue above is workable, but I just installed Hardy Beta and I've got no sound?!?!? It seems to recognize the chipset correctly, but still no sound.........anyone else?

---

### Post by jabeez on 2008-04-13
**crickets chirping**


Wow did all 2370 owners spontaneously combust (or did their 2370's?)? An update for anyone who might check in, I figured out that my sound disappears after coming out of suspend. Weird. Also weird is that I can only suspend once, which it does fine (minus sound issue), but any attempt after that fails. Hmmmm. Other than that Hardy is working pretty well for me, hopefully the few remaining issues get worked out in the next couple weeks. I've also been Googling around for an answer to the large fonts/resolution issue to no avail. Forcing fonts to 96 dpi works kinda, but some things are still pretty big. Hope to hear from y'all soon!!!

---

### Post by pjones0404 on 2008-04-16
i am waiting for the official release before i really mess around with 8.04.

i downloaded the beta and ran the live cd but that was about all. It looks like alot of the issues that i had with previous versions have been resolved. namely the wireless situations as it worked out of the box in the beta.

i look forward to working with everyone that has this laptop once 8.04 comes out. i think that there is just a lull right now since the new version is about to be released and there is not much tweaking left to do on 7.10.

---

### Post by pjones0404 on 2008-04-26
looks like no one has been able to step away from the tweaking long enough to give some impressions. overall i like 8.04. there is not a lot of new things but it seems to work very well. 

my wireless is working out of the box but it is slow. I have a 10 meg connections. when i run a speed test i am lucky if i get 1 meg down. is anyone else having this issue? what can i do to fix this?

thanks.

---

### Post by jabeez on 2008-04-26
Yeah I'm with you on the wireless, it does seem a bit sluggish, but at least it doesn't drop out randomly and take the device with it!!! But that seems to be about all that's fixed, and suspend/video is now borked. It will only suspend once, and even then it takes out sound on resume. Even if I leave it and the screen goes blank, it won't come back and I have to ctl+alt+backspace. GRRRRRR. Gutsy was pretty much perfect on this laptop, if it wasn't for that bizarre and incredibly frustrating wireless issue. One step forward, two steps back.

---

### Post by pjones0404 on 2008-04-26
i have the issue with the video as well when returning from suspend. it also does it when i am shutting down. i hope to get this fixed soon. 

i never realized how many things i had customized until i had to set everything up again. i am still trying to ge tthings back to the way that they were before. 

look forward to someone smarter than me to see what is the issue with the wireless. lol

---

### Post by thegreatrobot on 2008-04-30
This is a fix for something I haven't seen anybody complain about yet, but was driving me mental; when I recovered from suspend my USB's wouldn't work. Anyway, I found a post elsewhere about someone with a similar problem and found out that in the BIOS there's an option called Legacy USB or something like that... Apparently it turns off the USB ports when the aren't being used to conserve battery power. Anyway, when you go into suspend they turn off, and Hardy doesn't turn them back on again. Go into your BIOS menu and disable the Legacy USB option. It makes your USB's work, and also has made the whole suspend/recover process a lot more reliable.

---

### Post by thegreatrobot on 2008-04-30
Also, has anybody noticed their hard drive making funny sounds occasionally in Hardy Heron? It happens about 50% of the time I recover from Standby. Forgive my inability to describe this accurately, but it sounds kind of like it's initializing. I tried booting in XP for a while to see if my Hard Drive was broken, but it wasn't making the noise there. Curious...

---

### Post by pjones0404 on 2008-05-10
just wanted to let everyone know that i was still having issues with the wireless in 8.04. it worked out of the box but had limited throughput. I was only getting approx 700k down. 

i reinstalled ndis wrapper using the steps listed earlier in this thread and my wireless is working again at near top speed. I am now getting the full 10 megs of my connection. 

overall 8.04 is working really well minus this wireless issue as well as a the video driver not resuming from suspend correctly. i have to kill X before i can do anything when resuming.

---

### Post by jabeez on 2008-05-14
> **pjones0404 said:**
> just wanted to let everyone know that i was still having issues with the wireless in 8.04. it worked out of the box but had limited throughput. I was only getting approx 700k down. 

i reinstalled ndis wrapper using the steps listed earlier in this thread and my wireless is working again at near top speed. I am now getting the full 10 megs of my connection. 

overall 8.04 is working really well minus this wireless issue as well as a the video driver not resuming from suspend correctly. i have to kill X before i can do anything when resuming.

Strange, my desktop will come back up after a suspend, but not if I leave it sit and the screen goes black. But suspend does take out my sound, so that's annoying enough. I'm also getting the weird "mini-freezes". Every so often it locks up and nothing will respond, but it only lasts a few seconds. I'm kinda disappointed in Hardy so far, Gutsy was pretty much perfect besides the wireless dropping and taking the card with it. This seems to be a step back. Hopefully it gets better with updates, but I'm considering trying a couple different distros...........

---

### Post by Joshua on 2008-05-14
Has anyone figured out the suspend issue?  Is it affecting everyone?  Like described above, my screen won't come back after it goes to sleep.  In order to get it back, I used to think I had to restart, but I've since found that I can just switch to another login and then back to the graphical interface (not sure what they are called).  Basically I do Ctrl+Alt+F1 and then Ctrl+Alt+F7, and the screen comes back.

Another strange thing is that when I have it plugged into an external monitor, it works fine on the external monitor, but not on the laptop screen.  So I boot up and have separate X screens on the laptop and on the monitor.  When the screens go to sleep, I move the mouse and only the monitor comes back.  Ctrl+Alt+F1 sends them both to the F1 text login.  Ctrl+Alt+F7 brings them both back to the GUI.

---

### Post by mbi0 on 2008-05-24
> **pjones0404 said:**
> just wanted to let everyone know that i was still having issues with the wireless in 8.04. it worked out of the box but had limited throughput. I was only getting approx 700k down. 

i reinstalled ndis wrapper using the steps listed earlier in this thread and my wireless is working again at near top speed. I am now getting the full 10 megs of my connection. 

overall 8.04 is working really well minus this wireless issue as well as a the video driver not resuming from suspend correctly. i have to kill X before i can do anything when resuming.

do you think this will work on a 64 bit version with windows xp 32 bit drivers ?? if yes i will do the ndiswrapper thing :D

---

### Post by pjones0404 on 2008-05-24
to be honest i am not sure. i am still new and would not be able to assist really.

the steps that i followed were provided by someone on this thread. i just followed their instructions not really knowing exactly what it was doing. but it worked and i was happy.

---

### Post by mbi0 on 2008-05-24
> **pjones0404 said:**
> to be honest i am not sure. i am still new and would not be able to assist really.

the steps that i followed were provided by someone on this thread. i just followed their instructions not really knowing exactly what it was doing. but it worked and i was happy.

could you plz repost the post or tell me were to find it i just cant seem to find anything usefull :S even in this thread

---

### Post by pwithem on 2008-05-25
mbIO
Look at page 31 of this thread.

---

### Post by mbi0 on 2008-05-26
thanks for the info :D hope i can get a stable way to work this out its really annoying to have that great connection and only get less than 1/4 of it or sometimes not even that :S

---

### Post by ronux on 2008-06-05
Hello All,

I am new to Ubuntu and I have been using other distros to get my Averatec 2370 working properly with Linux. 

To my great surprise and joy I first tried 8.04 live CD and the wireless was immediately detected and working. This was a major issue with the other distros which they were able to recognize the wireless component but never worked right (no connectivity). 
I decided to create a dual-boot leaving the original Win XP in addition to the Ubuntu distro.

It has been over a month that I have been using this notebook with Ubuntu and so far everything is working well. 
I kept the machine running for days and the wireless connection has been very good. Video, streaming and general use also. 

I would recommend to anyone with an Averatec 2370 to give it a try. I am very impressed about this distro. Totally cool.

Many thanks to the Ubuntu team for their great work!

:)

---

### Post by jabeez on 2008-06-17
Hey all, just wondering if anyone has figured out what happens to the sound coming out of suspend? I'm not sure where to begin looking, I've tried restarting sound server and a couple settings in kcontrol (using Kubuntu obviously) but it won't come back without a restart. Anyone?!?!?!?

---

### Post by madman18 on 2008-07-07
Hey guys -

I'm wondering if anyone has been able to resolve the issue of the screen getting really bright/psychedelic looking during shutdown and suspend.  I started experiencing this issue when I configured the proprietary Nvidia video drivers.  I'm currently running 8.04.  Any help would be greatly appreciated.

---

### Post by pjones0404 on 2008-07-23
i am having the same issue with the screen on shutdown and resume. i had fixed it in gutsy but not in hardy. i am sure it is something in the xorg but i do not even know where to start looking.

i have also recently purchased an apple wireless keyboard and was curious if anyone has had nay luck in getting it to work. i searched around for a bit and it looks like it is a pain to get working correctly.

---

