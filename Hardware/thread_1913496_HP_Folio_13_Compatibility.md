---
title: "HP Folio 13 Compatibility"
date: 2012-01-22
forum: Hardware
---

### Post by rclowery on 2012-01-22
Greetings,

I've searched the forums, but I haven't been able to find any information on the HP Folio 13. I'm wondering if anyone has any experience reports with Ubuntu 11.10 using this device, and if so, what problems have you had, if any?

Thanks!

---

### Post by mswysocki on 2012-01-22
I recently installed ubuntu on my new hp folio, so far after a bit of troubleshooting I have gotten it working for just about everything I need.

There is no driver that I know of for the touchpad though the default driver works well enough for 2 finger scrolling and 2 finger right click.

The wifi driver gave me a bit of trouble but I was able to solve the problem using instructions from this post:
[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

Another issue that I have had is the default brightness is at its lowest setting and I have been unable to change the default brightness setting. The brightness hotkeys on the keyboard still do not work. I had to install the OS on lowest brightness (which is barely usable) but I was able to get through it.

Also this is my first real attempt at using linux so I'm still a bit new but I have been able to figure it out with a pretty positive experience.

---

### Post by rclowery on 2012-01-22
Thanks for replying.

Your problems are fairly typical, especially with wifi, brightness issues, and function keys.

I've been running successive versions of Ubuntu on a Toshiba laptop for the past few years and the function keys still do not work. 

Though, I have a work around for brightness control that you might consider trying. It may not work for the HP Folio, but a variation on this code may do the trick. You can look around the forums for other versions.

Try inputing this into the terminal:

```
sudo setpci -s 00:02.0 F4.B=Number
```

Put a number after the equals sign between 0 and 100.

---

### Post by rclowery on 2012-01-23
Actually, I thought of something else you can try to fix your other problems. Since your computer is brand new, you should consider upgrading the kernel to the latest version. It might contain some of the missing code that will allow you to access your computer's full hardware capabilities. If you are running the latest release of Ubuntu (11.10) it will not have the current kernel. If you want to wait until the next release (12.04), it will have the current version, or you can do it manually now.

Try this link:

[http://ubuntuforums.org/showthread.php?t=1872537]("http://ubuntuforums.org/showthread.php?t=1872537")

---

### Post by shenrik on 2012-01-24
Hi,

I'm currently on a Live Desktop Ubuntu 11.10, 64-bit, booted from an USB. Am experiencing very bad signal and an extremely slow wireless connection (which amazingly enough worked after just updating a driver that Ubuntu recommended me in a pop-up window!)

Is the connection bad because Ubuntu is running from the USB, or is this something I can have trouble with even after doing a full installation?

And since it doesn't seem to be that many who's running Linux on HP Folio yet; which laptops are pretty similar on the inside, so that it would be a good idea to include their names when searching for solutions to problems?


Hepp!

-shenrik

---

### Post by ts3 on 2012-01-24
> **shenrik said:**
> And since it doesn't seem to be that many who's running Linux on HP Folio yet; which laptops are pretty similar on the inside, so that it would be a good idea to include their names when searching for solutions to problems?
-shenrik

Rather than looking for a similar laptop it might be easier to look up the particular device that's giving you trouble, e.g. the graphics card, the wireless chipset etc.  Running the command

```
lspci
```

in terminal (ctrl + alt + T to open terminal) will give you some basic idea of what you have on your laptop.  

If you think you might have a problem with the wireless I'd suggest having a back-up option for research & troubleshooting such as wired (ethernet cable), another computer or a smartphone.  

My experience is fairly limited (less than 3 months on linux) but I had to do some troubleshooting for the wireless early on and while it was a pain, I also learnt a lot about my system, how to use the terminal etc.  It can be a rather steep learning curve but once you get to know the basics it's amazing what power you have over your system (something you don't have on proprietary OSs).

Good luck and post questions as/if they come up.  

Cheers :)

---

### Post by rclowery on 2012-01-24
> **shenrik said:**
> Hi,

I'm currently on a Live Desktop Ubuntu 11.10, 64-bit, booted from an USB. Am experiencing very bad signal and an extremely slow wireless connection (which amazingly enough worked after just updating a driver that Ubuntu recommended me in a pop-up window!)

Is the connection bad because Ubuntu is running from the USB, or is this something I can have trouble with even after doing a full installation?

And since it doesn't seem to be that many who's running Linux on HP Folio yet; which laptops are pretty similar on the inside, so that it would be a good idea to include their names when searching for solutions to problems?


Hepp!

-shenrik
Shenrik,

How did Ubuntu update your driver if your wireless was not working? Were you connected by ethernet? If so, did it actually run an update process to make sure your software was up to date? The reason I am asking is that I've never heard of Ubuntu updating itself before an installation.

---

### Post by inaneimp on 2012-01-30
> **rclowery said:**
> Actually, I thought of something else you can try to fix your other problems. Since your computer is brand new, you should consider upgrading the kernel to the latest version. It might contain some of the missing code that will allow you to access your computer's full hardware capabilities. If you are running the latest release of Ubuntu (11.10) it will not have the current kernel. If you want to wait until the next release (12.04), it will have the current version, or you can do it manually now.
 
Try this link:
 
[http://ubuntuforums.org/showthread.php?t=1872537](http://ubuntuforums.org/showthread.php?t=1872537)
 
I had the same problem as previously reported (HP Folio 13 screen @ minimum brightness when installing 11.10). Has anybody tried the solution above? Does it work?
 
I found the brightness unusable when I attempted to install 11.10.

---

### Post by cms2337 on 2012-01-31
I am having the same problem... I had to turn up the brightness by using a flashlight and turning up the brightness in the screen settings before i installed. Every time i reboot the folio the screen brightness setting is never saved and have to use a flashlight to turn it back up. 

For the past few days i've just been hibernating instead of shutting down. Its a real pain that the setting isnt being saved and the brightness buttons on the keyboard dont work.

I fixed the wifi problem by using these steps:

> **jskandhari said:**
> SOLUTION
Did some hit and trial and finally got my BCM4313 to work.
None of the Previous threads directly related to BCM4313 helped so here I am mentioning my steps.

Firstly went over to Synaptic Package Manager
>Remove all the Installed Packages related to BCM & BCM 43 // Do check STA in Additional Drivers is deactivated if not please do so before Removing Packages

>Then check whether **bcma** is blacklisted ( in file /etc/modprobe.d/blacklist.conf ) if not then type in terminal
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

>Similarly check whether **brcm80211** is blacklisted ( in file /etc/modprobe.d/blacklist.conf ) if not then type in terminal
```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

>Reboot

>Goto Synaptic Package Manager
In search simply type **bcm43** ( to easily find all the Packages required to install )
Select the Following Packages for installation ( latest version )
1)bcmwl-kernel-source
2)broadcom-sta-common
3)broadcom-sta-source
4)firmware-b43-installer

It will prompt for additional packages required simply accept them too.

>Reboot

This time round No Wifi is being displayed in the Network Section and if you check
```
rfkill list
```
It also won't be displaying the wifi card will display bluetooth only ( if any )

>Goto Additional Drivers
Activate Broadcom STA

By now your Wireless would be active and ready to connect but still on the safer side

>Reboot

Now if you check Synaptic firmware-b43-installer won't be marked as installed // Mentioning just in case you face with any problems can apply your own Hit and trails.


I still have yet to test if the HDMI-out and the bluetooth work.

The HP Folio is a cool ultrabook, its so close to being ubuntu friendly.

---

### Post by reedwade on 2012-02-02
I got the backlight working by setting  acpi_backlight=vendor as described here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=45271](http://forums.linuxmint.com/viewtopic.php?f=42&t=45271)

This fixes the "no lights at start up" not the brightness function keys.
--

The only remaining problem I have is suspend doesn't work -- it will suspend but then wakes back up immediately. 

--

Such a sweet sweet laptop, I expect it'll be pretty popular once more people have had a play with it so I'm expecting we'll have more help with this soon.

---

### Post by cms2337 on 2012-02-02
> **reedwade said:**
> I got the backlight working by setting  acpi_backlight=vendor as described here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=45271](http://forums.linuxmint.com/viewtopic.php?f=42&t=45271)

This fixes the "no lights at start up" not the brightness function keys.


That works.. i no longer have to hibernate all the time.
--

> **reedwade said:**
> 
The only remaining problem I have is suspend doesn't work -- it will suspend but then wakes back up immediately. 

Suspend does work for me when i click on the gear at the top right then Suspend. However, when i set my laptop to suspend when the lid is closed it doesn't, it just blanks the screen.

--
> **reedwade said:**
> 
Such a sweet sweet laptop, I expect it'll be pretty popular once more people have had a play with it so I'm expecting we'll have more help with this soon.

i know!!!

---

### Post by gryning on 2012-02-03
Hi all,

I have also risked being an early adopter of the Folio 13. Backlight is the first major problem, screen becomes usable weith 'acpi_backlight=vendor' as above. I can add that there is strange behaviour when using Fn+F2 and Fn+F3, xev reports a stock F2 or F3 press for this combination and nothing for a press without the Fn key.

Perhaps some of the problems sit within the key mapping, although I understand the Fn key itself should not register with X, I would expect F2 and F3 to function as normal.

Can anyone help diagnose this further?
Thanks
c

---

### Post by gryning on 2012-02-03
It seems that the Fn key is inverted by default all all media functions are working without the Fn key depressed. I should note that the brightness keys appear to be the only one's that do not function.

---

### Post by gryning on 2012-02-03
Partially resolved: Within the system bios 'Action Keys Mode <Disabled>' will set the Fn key back to normal behaviour. This may have crept on as part of the F.05 bios upgrade.

'showkey' reports:
F1 = 59
F2 = 60
F3 = 61
F4 = 62
F5 = 63
F6 = 64
F7 = 65
F8 = 66
F9 = 67
F10 = 68
F11 = 87
F12 = 88

Fn + F1 = 125,59
Fn + F2 = <nothing> (no change to backlight)
Fn + F3 = <nothing> (no change to backlight)
Fn + F4 = 25
Fn + F5 = <nothing> (keyboard light toggles)
Fn + F6 = 165
Fn + F7 = 164
Fn + F8 = 163
Fn + F9 = 114
Fn + F10 = 115
Fn + F11 = 113
Fn + F12 = <nothing> (Wireless device does not toggle)

---

### Post by gryning on 2012-02-03
Feels like I'm narrating my life here atm, but...

I'm using a USB booted version of 12.04 for most of my testing, verifying against 11.10 where I can. To answer a post earlier in the thread; suspend and wifi are both fine on 12.04.

My main oustanding issues are:
* touchpad
* brightness control

I have some concerns about power usage and reporting, but need to more to confirm.

---

### Post by hanbo on 2012-02-06
Can you guys telll me whether the hdmi output works with an external monitor out of the box?

I am considering to buy this laptop, but hdmi is essential for me.

---

### Post by gryning on 2012-02-06
I used it for no more than 5 minutes, but it seems to work in both mirrored and extended modes straight out of the box using 12.04 live USB image, I have not tried 11.10.

---

### Post by Klarvet on 2012-02-14
Hi All,

First of all, Thanks for your help!

I bought yesterday the HP Folio 13 and installed straight away Ubuntu and used the fixes from this post.

I did this:

**# Brightness**
gksudo gedit /etc/default/grub
replace GRUB_CMDLINE_LINUX=&#8221;&#8221; with GRUB_CMDLINE_LINUX=&#8221;acpi_backlight=vendor&#8221;
sudo update-grub
Restart

**#Wirelles**
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source firmware-b43-installer -y

btw use a very strong light for the first installation (brightness is pretty ****** up)


I've still have problems with my touchpad. I can't right click and I'm unable to move folders / select them...

does anyone now how to fix? I've already tried different settings (mouse) but two finger scroll / right click doesn't work... :(

Thanks for your help.

---

### Post by b_b on 2012-02-18
Hi, i've just pirchased this woot laptop and recived it yesterday. First of all, thanks for the acpi_backlight trick. Very usefull if you don't want to make all the installation process in the dark ;)

Here is the list of the problems i've encountered and how i solved it :

[http://labo.eliaz.fr/spip.php?article94](http://labo.eliaz.fr/spip.php?article94)

For now here is the liste of things that works :

- Clickpad/Trackpad works well fo left and right click buttons, two fingers scroll is ok and i can right click with a two fingers click.
- Screen backlight is ok with acpi_baclight option added to grub (luminosity is stucked to 100% but i can change it by going in System settings > Screen).
- Backlight keyboard works well and i can activate/desactivate it with fn+F5

And now the things that still doesn't work :

- Media key to change screen luminosity ( fn+F2/3 )
- Media keys for media player ( fn+F6/7/8 )
- Media key to turn on/off wireless ( fn+F12 )

There is still one thing that bore me, i'll try to explain it with my poor english. The bottom area of the trackpad (where click buttons are located) is sensitive to movement. So if i press the left button and try to slide the cursor to select a text it d'ont works. i have to use tap+tap and slide to select text for now. It would be great if the click buttons where not considered as part of the trackpad area, don(t know if i am clear on that point ^^ Anyway i'll try to do it, and update the web page pointed above if i succeed on that point.

++

---

### Post by vjust on 2012-02-19
Nice info in this thread.   I am close to taking the plunge.  Are you folks using it in 'single-boot mode', i.e. after nuking the Windows install?

thats what i'd like to do :-)  Guess my question shows I am a bit chicken.

---

### Post by b_b on 2012-02-19
Yes i'm using it on single boot mode, i've never launched win$ and erased all the disk content before lauching ubuntu installation.

Unfortunatly HP doesn't provide a way to get back money for the preinstalled os on their laptops... Sad too see that some manufacturers are still playing that kind of mistake...

---

### Post by gryning on 2012-02-19
vjust, I am using this as an installed version now, which is the default. The clickpad takes some getting used to, but the multitouch options and some configuration in compiz workaround the main difficulties.

* two finger scrolling
* single tap for left click
* double finger tap for right click
* double tap without release on the Window title bar allow you to drag.
* double tap without release on edges allow you to resize.

In short, physical clicking and dragging fails miserably, but you can work around clicking with 'gestures'.

Outstanding:
* Backlight on boot.
* acpi keys.
* Power usage is considerably higher than windows, possibly linked to the above.
* Battery lifetime and charging info is 'intermittent'.

If anyone can tell me where to submit data for a 'bug report' or to assist in development please message me here. I have tested with linux-image-3.3rc4 and none of these issues behave differently, so nothing upstream for us just yet.

---

### Post by jediborger on 2012-02-21
Can anyone post approximately how long the battery lasts even with the ACPI/brightness issues mentioned above?

I noticed on Planet Ubuntu that the kernel team has applied a patch to kernels 3.2.0-17.26 and up that should enable a low power idle mode for Sandy Bridge processors, which I believe this laptop has. I'm curious to see what the battery difference is between Oneric and Precise.

---

### Post by Caradoc on 2012-02-21
I just installed 11.10 on my HP Folio 13.  The "acpi_backlight" tip works fine.  Not using anything from 12.04.

What's working:
[LIST]
[*]Wireless
[*]Backlight (with grub patch)
[*]Suspend when triggered manually
[*]Audio seems fine
[*]Seems to have about 5hrs of life if bightness to ~40%
[*]Volume buttons
[*]keyboard light button
[*]Physical button and tap click works
[/LIST]

What's not working:
[LIST]
[*]Two finger scroll is inconsistent
[*]Trackpad keeps getting activated when typing
[*]Suspend on lid close
[*]Brightness buttons
[*]Wireless switch button
[*]Physical clicking and dragging is doesn't work at same time
[/LIST]

---

### Post by AkiraXXX on 2012-02-22
I am using the HP Folio 13-2000 series laptop.  I tried booting Ubuntu 11.10 from USB and had no video (black screen) although I did hear the tell-tale music one hears upon successful boot.  So, I assume things were working in the background, but my screen was black.  The same thing occurred with Linux Mint 12.  

I don't know if there are internal differences of any real substance between the 2000 series and what others may be using.  Or, perhaps others are using the 2000 without issue and this is peculiar to me?

Anyway, I guess I will wait a bit.

---

### Post by Caradoc on 2012-02-22
The backlighting is completely off by default.  Try either shining a bright flashlight at the screen so you can barely see what's going on, but can see it well enough to get to the Screen options and reset the backlighting, or add "acpi_backlight=vendor" in the Grub boot string as listed above.  That should at least get you going.

As another note, install "gpointing-device-settings" seems to load a menu setting to better set things like palm detection for the Synaptics trackpad, and it's behaving better.  These can also be set manually using "synclient", but I haven't really experimented much yet.

---

### Post by AkiraXXX on 2012-02-27
No luck with the flashlight route as the screen was still pure black.  I tried the addtion to Grub, but as it was Grub4DOS, the command was not recognized.  Ah well, it won't be long until the new version is released.

Thanks for help.

---

### Post by ububtusincev8 on 2012-02-29
Got my Folio 13 yesterday, had a similar experience as others have stated. The grub mod did not work for me, and I had a python script that did the trick, until I upgraded Python (lol). Finally, this little fix seems to do the trick:

add this line to rc.local:
echo 10 > /sys/class/backlight/acpi_video0/brightness
Works well. My wireless card seems fine. The only issue I have left is the mouse which is not fully functional, but an external one plugged in does the trick for now until I can play with it some more. I may do the 12.04 upgrade just to see how well that works.

---

### Post by sportsdude81 on 2012-03-02
Got mine two days ago and you must install(build them first) the drivers from the broadcom website.  The wireless signal is 10x better then the STA driver from the ubuntu repo.  

Have 10.04 on mine and I am getting dodgy speeds and connectivity with the built in gigabit Ethernet.  Seems to be much slower then gigabit during speed tests and downloads constantly timeout and have to be restarted.

Anybody else seeing this?

EDIT:

Seems to be an outdated driver again.  You can download the newest from here [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

download the one for your kernel. Mine was "LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)". To find your kernel version do
```

uname -a

```

Then just untar it and they give you a nice little script to remove the old module, build it, and install it.  So just run (This is in the README):
```

sudo ./autorun.sh

```

---

### Post by sportsdude81 on 2012-03-03
> **ububtusincev8 said:**
> Got my Folio 13 yesterday, had a similar experience as others have stated. The grub mod did not work for me, and I had a python script that did the trick, until I upgraded Python (lol). Finally, this little fix seems to do the trick:

add this line to rc.local:
echo 10 > /sys/class/backlight/acpi_video0/brightness
Works well. My wireless card seems fine. The only issue I have left is the mouse which is not fully functional, but an external one plugged in does the trick for now until I can play with it some more. I may do the 12.04 upgrade just to see how well that works.

Alright the super bright back light is starting to **** me off.  Anybody have any (I mean any) way of adjusting it.  I am using Lucid and I don't have acpi_video0/brightness in my /sys/class/backlight folder.  It seems kind of ridiculous that the only way to adjust the backlight is with the hardware keys.

---

### Post by sportsdude81 on 2012-03-03
Back again.  This time with no audio.  Tried to install alsa 1.0.24 but that didn't work either.  Was wondering what configuration you guys have 11.10 ```
/etc/modprobe.d/alsa-base.conf
```

---

### Post by ububtusincev8 on 2012-03-03
> **sportsdude81 said:**
> Back again.  This time with no audio.  Tried to install alsa 1.0.24 but that didn't work either.  Was wondering what configuration you guys have 11.10 ```
/etc/modprobe.d/alsa-base.conf
```

Pulse audio worked out of the box for me in 11.10 for both speakers and headphones. I did have to turn the sound up though, by default it was set to 0. Just light the backlight. :)

---

### Post by sportsdude81 on 2012-03-03
> **ububtusincev8 said:**
> Pulse audio worked out of the box for me in 11.10 for both speakers and headphones. I did have to turn the sound up though, by default it was set to 0. Just light the backlight. :)

Sorry Forgot to mention I am trying to get it to work in 10.04.  Why am I doing that you ask...?  It is work related, but I will probably switch to 11.10 in few weeks.  Was wondering if 11.10 was using the 1.0.24 Alsa driver and what it was set to.  Would you mind doing

```
cat /etc/modprobe.d/alsa-base.conf | grep intel
```
```
cat /proc/asound/version
```

would be much appreciated.  Want to save me the trouble of installing 11.10 for the moment if I can :).  Thanks again.

---

### Post by arabxptyltd on 2012-03-13
I have just received and installed Ubuntu 11.10 on my HP Folio 13.
While I have updated grub with the necessary backlight fix, and my machine boots and I can login with a working screen, as soon as my desktop goes into screensaver mode, I am left with an unusable system with no backlight setting.  

I know no way to fix other then rebooting, which makes the machine useless to use.

Any suggestions appreciated.

---

### Post by iwbailey on 2012-03-14
I think this backlight not turning on after going down for power saving relates to the following bug... 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652)

I updated to the 3.0.0-16-generic kernel (most recent update) and that behaviour has stopped.

---

### Post by arabxptyltd on 2012-03-14
Thanks, I am running a current 11.10 with all updates, kernel is 3.0.0-12.
Will test this out.

---

### Post by arabxptyltd on 2012-03-14
For those reading this thread, this is my current experience with Ubuntu 11.10 (3.0.0-12) on a new HP Folio 13.

1. Follow the reported screen brightness problem and grub fix in this thread.
2. Wireless and sound works out of the box
3. External screen with HDMI cable works out of the box
4. Keyboard backlighting with F5 works fine.  I updated my Bios F.05 to set Action Keys Mode to <Disabled> so that this now works with Fn+F5.

Issues

[FIXED - Upgrade Kernel] 1. Screen brightness goes to black after screensaver kicks in.
2. Cannot use the trackpad for any click/drag operations, e.g. cut/paste or move window (which is very annoying). Using an external mouse.

I have a hack for the brightness/function key problem. Place the following script in /usr/local/bin and chmod 755 


```
$ cat /usr/local/bin/brightness 
#!/bin/sh
MAX=`cat /sys/class/backlight/intel_backlight/max_brightness`
CUR=`cat /sys/class/backlight/intel_backlight/brightness`
MIN=0

SIGN="+"
[ "$1" = "decrement" ] && SIGN="-"
INC=`expr $MAX / 10`
NEW=`expr $CUR $SIGN $INC` 
[ $NEW -gt $MAX ] && NEW=$MAX
[ $NEW -lt $MIN ] && NEW=$MIN
echo $NEW >  /sys/class/backlight/intel_backlight/brightness

echo "Set Brightness to $NEW of $MAX, was $CUR"
exit 0
```There is one permission problem, you need to run this once for this script to work.

```
$ sudo chmod 666 /sys/class/backlight/intel_backlight/brightness

```Now, /usr/local/bin/brightness will increase screen brightness by 10%, and /usr/local/brightness decrement will decrease screen brightness by 10%.

Furthermore I mapped these via the System Settings | Keyboard | Shortcuts to F2 and F3.   I am unable to map to Fn+F2,Fn+F3. Perhaps somebody with more experience in this field can solve that issue.

---

### Post by arabxptyltd on 2012-03-14
Woot, I can confirm the following kernel upgrade to 3.0.0-16 solves the brightness loss after screensaver

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo init 6
```> **iwbailey said:**
> I think this backlight not turning on after going down for power saving relates to the following bug... 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652)

I updated to the 3.0.0-16-generic kernel (most recent update) and that behaviour has stopped.

---

### Post by theresaanna on 2012-03-20
Thanks, everyone, for the info listed so far. I'd be lost without it.

I'm completely new to running Linux outside of a VM so this is a new world for me. Bought my Folio last weekend and, after some failed attempts to fix many of the issues that have already been mentioned in this thread, have wiped attempt #1 and just done a fresh reinstall of 11.10. 

I have had the same problem with the backlight and the instructions listed earlier and outlined nicely in this post: [http://labo.eliaz.fr/spip.php?article94](http://labo.eliaz.fr/spip.php?article94) did the trick. The trackpad is spotty no matter what I do, so I'm using an external mouse. 

Sometime between upgrading my kernel from 3.0.0-12 to 3.2.11 and attempting to fix my wireless card based on the suggestions in this thread, things went wrong. I should mention that on this attempt my wireless seems serviceable, even if the signal is surprisingly weak. When I installed the first time, it kept dropping. After upgrading the kernel and attempting to blacklight bcma and also run the realtek driver script the card stopped being recognized at all. I should have taken more distinct steps so that I could be sure where things went wrong.

Upgrading the kernel *did* fix the suspend problem.

I have no answers just yet but will share if I find any!

---

### Post by theresaanna on 2012-03-20
I'm looking at full bars on my wireless connection and its now picking up the networks I'd expect, so I hink I fixed my weak signal problem. What I did:

I compiled steps that made sense from [this thread]("http://ubuntuforums.org/showthread.php?t=1889170"), which I think was linked earlier.

To start, I followed these directions

> [FONT=Arial][SIZE=2]
[SIZE=2]If you have this problem (no wifi or very weak signal) on a laptop  equipped with Broadcom 4313 wireless, seems the place to start is  checking which drivers Ubuntu is running for it - so go straight to  terminal[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=2](CTRL+ALT+T in Ubuntu) and type[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Arial][SIZE=2]lshw -C network[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]If the driver shown is something like “bcma” or “brmcsmac” Ubuntu isn't loading the right driver [/SIZE][/FONT][FONT=Arial][SIZE=2] (sort this out please!) [/SIZE][/FONT]I found two drivers on my system:

> 
description: Wireless interface
product: BCM4313 802.11b/g/n Wireless LAN Controller
vendor: Broadcom Corporation

description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
So that wasn't the problem.

I installed three packages from Ubuntu Software Center, in order. These may be redundant given the above, but I am new and playing it safe-ish.

> [FONT=Arial][SIZE=2]search "bcm" and reinstall bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common[/SIZE][/FONT]I restarted here to test and my wireless card was MIA again. I then remembered that these drivers are incompatible with some other modules. Last time I tried, I found bcma on my system, so I ran 

```
[FONT=Courier New]lsmod | grep "b43\|ssb\|bcma\|wl"[/FONT]
```...and indeed found bcma. I ran ```
rmmod bcma
``` and then opened /etc/modprobe.d/blacklist.conf.** I commented out "blacklist BCM43xx" **and added "blacklist bcma". Why would 11.10 ship with a module blacklisted when its still of use to some? The comment above the blacklist directive is ```
# replaced by b43 and ssb.
```Restart... victory!

---

### Post by theresaanna on 2012-03-21
Update: kernels 3.2.11 and 3.2.12 definitely break my wireless. After installing the kernel and restarting, the machine no longer sees wireless options in the task bar. I haven't delved any deeper.

---

### Post by theresaanna on 2012-03-22
I feel like I'm talking to myself, but I want to record all of this information for others that may come along!

I uninstalled kernel 3.2.11 and my wireless is good again. Got a DVI <-> HDMI cable today and can confirm that an external monitor works with no problems.

The *only* thing that I can't live with at this point is the trackpad. I will report back about whether the patches in this post from earlier in the thread work: [http://labo.eliaz.fr/spip.php?article94](http://labo.eliaz.fr/spip.php?article94). The one thing that I'm not going to try is going to 12.04 since I had such bad luck upgrading to kernel 3.2.12. Not having two finger scroll is a big deal, but I'm hoping that living without it is temporary.

---

### Post by jayrod on 2012-03-24
I installed b43-fwcutter and firmware-b43-installer, and got something like a not supported message.

I then did the following from [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/905388/comments/5](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/905388/comments/5):

> 2. Add the following two lines at the end of your /etc/modprobe.d/blacklist.conf file
blacklist bcma
blacklist brcmsmac
3. Create file /etc/pm/config.d/config with one line:
SUSPEND_MODULES="$SUSPEND_MODULES brcmsmac"
4. rebootEasy, stronger Wifi signal.

---

### Post by theresaanna on 2012-03-24
So, in case anyone else, like me, didn't realize, you can still move windows around with the trackpad despite the lack of grab and drag. There's tap and drag. Basically, you double tap the top bar of a window, move the window, then tap once to release. Its a little funky, but it works. 

Also, checking "Two-finger scrolling" in System Settings works! Hooray for trackpad adjustment progress.

FWIW, I've been playing around with options for the trackpad. Do:

```
synclient /usr/share/X11/xorg.conf.d/50-synaptics.conf
```To test things out. You have to enable SHMConfig, here are some instructions on these things: [http://askubuntu.com/questions/50201/how-to-enable-shmconfig](http://askubuntu.com/questions/50201/how-to-enable-shmconfig)
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

The only remaining thing that's a killer for me is that the battery life SUCKS. 3 hours tops. Must find a fix. I'm also having problems with my Canon iP4820 printer, but one thing at a time.

---

### Post by matizzz on 2012-03-26
The tips and tricks in this thread have been extremely useful for me. In addition i used a python script ([http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/](http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/)) to set the brightness to 70% at startup. Furthermore I added the pcie_asm=force option to the grub configuration to see if this would increase the battery life (ubuntuforums.org/showpost.php?p=11461609&postcount=11). This trick has proven to be working for the HP probook and elitebook. 

With the brighness setting on 70% and the grub trick the power usage is still at almost 16 Watt, giving at max 3.5 hours of usage. This is still low compared to a system running on Windows, which gives almost 7 hours of battery with similar settings ([http://www.notebookreview.com/default.asp?newsID=6377&p=4](http://www.notebookreview.com/default.asp?newsID=6377&p=4)). Did someone test the battery life with Ubuntu 12.04?

What is still not working for me is 2-finger scrolling

---

### Post by BigFatTony on 2012-03-30
the following commands simulate the brightness fn-keys. one could create a keyboard shortcut as a work-around...

```
xdotool key XF86MonBrightnessDown
```
and
```
xdotool key XF86MonBrightnessUp
```

of course, xdotool must be installed. :D

hope it helps...

---

### Post by krige on 2012-04-05
After having created the 4 Windows recovery disks I was able to free the 18GB recovery partition and install on it Ubuntu 12.04 beta 2, 64-bit.

1. I fixed the display off at startup problem by following these instructions:
[http://labo.eliaz.fr/spip.php?article94](http://labo.eliaz.fr/spip.php?article94)

2. I fixed the two fingers scroll from System Settings / Mouse and Touchpad / Two-finger scrolling. Also there I set the Acceleration and Sensitivity bars at mid range.

3. As for the WiFi problem I wasn't able to fix it using jayrod suggestion, that is using the following instructions:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/905388/comments/5](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/905388/comments/5)

So I used the jskandhari solution posted by cms2337 earlier on this same topic:
[http://ubuntuforums.org/showpost.php?p=11654697&postcount=9](http://ubuntuforums.org/showpost.php?p=11654697&postcount=9)
But differently from those instructions:
- I had to install Synaptic Package Manager from Ubuntu Software Center, as was not present in 12.04;
- no packages related to BCM & BCM 43 were already installed and needed to be removed;
- the "Broadcom STA wireless driver", in Additional Drivers, was already activated and in use.

4. I wasn't able to fix the brightness functions keys not working; as a workaround I am using the "Brightness and Lock" application to change the screen brightness.

Everything else is working pretty well.

As a personal comment I would like to add that I am impressed with the speed and reactivity of Ubuntu on this laptop. It boots within 8 seconds and shuts down in 2. It appears to be faster even than my way more powerful desktop computer. I am not sure whether it's because of the new Ubuntu version, or of the SSD on the laptop, or both.

---

### Post by theresaanna on 2012-04-05
krige - I am running 11.10 but am also impressed with the speed of this machine. I have a Macbook Pro at work with an i7, double the ram of this machine but it is noticeably slower to me now on disk-heavy operations. The SSD is a huge win.

The only ongoing issue that I'm having that is a big deal is the battery life. I've been meaning to start Googling on that issue and trying things out - maybe this weekend. I don't think I even get two hours out of the battery as it is with routine use. It really sucks.

---

### Post by krige on 2012-04-07
> **theresaanna said:**
> The only ongoing issue that I'm having that is a big deal is the battery life. I've been meaning to start Googling on that issue and trying things out - maybe this weekend. I don't think I even get two hours out of the battery as it is with routine use. It really sucks.

I haven't been using the laptop on battery for long time yet, but I can tell it appears here on mine I should get at least 4 hours out it: I have been using it on battery for one hour and half and it says I have 2.5 hours left.

What bothers me mostly instead on this laptop is the fan noise, a bit too loud for my liking.

I have found another issue: despite the "when the lid is closed" option, in the power options, is set to suspend, when I close the lid the laptop does not suspend. Also, when suspended pressing the power button it resumes from suspension by itself after several minutes. These may actually be related to using the 12.04 beta2, rather than some issue with the laptop itself.

---

### Post by theresaanna on 2012-04-07
> **krige said:**
> I haven't been using the laptop on battery for long time yet, but I can tell it appears here on mine I should get at least 4 hours out it: I have been using it on battery for one hour and half and it says I have 2.5 hours left.

Mine will usually report somewhere just under four hours on a full charge, but I don't get that. Somewhere along the way it just starts dropping rapidly.

> **krige said:**
> What bothers me mostly instead on this laptop is the fan noise, a bit too loud for my liking.

That's strange - its mostly silent for me. 

> **krige said:**
> I have found another issue: despite the "when the lid is closed" option, in the power options, is set to suspend, when I close the lid the laptop does not suspend. Also, when suspended pressing the power button it resumes from suspension by itself after several minutes. These may actually be related to using the 12.04 beta2, rather than some issue with the laptop itself.

I can confirm that I need to manually suspend the machine before closing the lid or it will stay on and drain the battery. That being said, even when suspended for a few hours and the lid closed it will still drain my battery and die.

---

### Post by matizzz on 2012-04-08
> **krige said:**
> 
What bothers me mostly instead on this laptop is the fan noise, a bit too loud for my liking.


For me it's the same. In a silent room you still hear that the fan is most of the time on. I've been looking at fan control, but i don't get the fan detected by lm-sensors. Anyone got more luck with that? Use these instructions at your own risk : [http://askubuntu.com/a/46135](http://askubuntu.com/a/46135)

---

### Post by sultanoswing on 2012-04-08
I run Arch Linux (x86_64) on the Folio 13. 

I agree with what others have posted, it's a nice, thin, fast machine. You may not get 7 hours out of it (or the 9 that HP claims!), but on Arch (running Gnome-shell) I'm able to get around 5 hours work done. I haven't done any special tweaks to try to get it to last longer and I run it at 100% brightness. I'm thoroughly impressed by how quickly Arch boots on this - much faster than what others are reporting when using Win 7.

I've compiled an HP Folio 13 wiki page on the Arch Wiki pages which may be of interest to Ubuntu users with this laptop: [https://wiki.archlinux.org/index.php/HP_Folio_13](https://wiki.archlinux.org/index.php/HP_Folio_13)

I would expect that the remaining things which don't yet work soon will i.e. all Fn keys, trackpad LCD and tap on-off.

---

### Post by whereisw on 2012-04-11
This thread is very helpful to me for setting up Ubuntu on Folio 13.  Below were what I ended up tweaking to get Ubuntu 12.04 beta 2 64bit running on my Folio ...

*** inside /etc/default/grub file**
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i915.i915_enable_rc6=1"

```

Be sure to run 'update-grub' after modifying the file.  I got the acpi_backlight tip from this thread.  The i915 RC6 parameter is explained in _[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)_.  This is probably the most beneficial power saving tweak on that page.

*** add the following line in /etc/rc.local**
```

echo 2294 > /sys/class/backlight/intel_backlight/brightness

```

The value 2294 roughly corresponds to 50% brightness on my laptop and 0 will completely turn off the back lighting of Folio 13.  I got this tip from _[http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot](http://askubuntu.com/questions/3841/desktop-doesnt-remember-brightness-settings-after-a-reboot)_.  With brightness default to 50% and enabling i915 RC6 option, a fully charged battery seems to last more than 5 hrs.

*** what worked out of the box**
- wifi
- multimedia keys
- keyboard backlight

*** what's not working**
- brightness up/down keys (scancodes not registered in 'xev' or 'showkey' commands)
- wifi on/off switch key (scancodes not registered in 'xev' or 'showkey' commands)
- suspend on lid close (despite that lid state is correctly reflected in /proc/acpi/button/lid/LID0/state when the lid is closed and suspend works fine when triggered manually via the menu)

Here is a good reference on mapping keyboard keys: _[https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys#Check_for_scancodes](https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys#Check_for_scancodes)_

---

### Post by gryning on 2012-04-12
As part of testing for:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/974568](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/974568)

I noticed that the 3.4 kernel has a much more accurate prediction and more timely behavior when updating battery status/lifetime for this device.

---

### Post by F00RAX on 2012-04-12
I love you so much "theresaanna". My new laptop is mostly working now.
I'll tell you about my experience of installing Ubuntu 12.04 on my HP Folio 13 soon...

See you et merci ("I'm french speaker !")

---

### Post by krige on 2012-04-14
> **matizzz said:**
> In a silent room you still hear that the fan is most of the time on. I've been looking at fan control, but i don't get the fan detected by lm-sensors. Anyone got more luck with that?

As workaround I disabled the "Fan Always On" option in the BIOS setup (press ESC on startup / F10 / System Configuration).

---

### Post by cathalinag on 2012-04-20
I just got my HP Folio 13 and am trying to install Ubuntu 11.10 unsuccessfully. I read all the comments in this forum but doesn't seem like anyone has had the same problem I am running into.

I got the image in my USB drive but when I try to boot up to install I get one line of text:
"Syslinux 4.06 EDD 4.06-pre-1 Copyright... H. Peter Anvin et al"

That's all. Then nothing happens.

I am using a 4Gb Sandisk cruzer. I deleted the U3 functionality already since this seemed to be a known issue in previous versions but it didn't fix the problem. Before deleting U3 I used to get a second line of text with the word "boot:" and a prompt. 

If anyone knows what's happening or what I am doing wrong, thanks for your help. :KS

---

### Post by krige on 2012-04-20
> **whereisw said:**
> *** what's not working**
- brightness up/down keys (scancodes not registered in 'xev' or 'showkey' commands)
- wifi on/off switch key (scancodes not registered in 'xev' or 'showkey' commands)
- suspend on lid close (despite that lid state is correctly reflected in /proc/acpi/button/lid/LID0/state when the lid is closed and suspend works fine when triggered manually via the menu)

How about we all write to HP and ask to add support for these and other possible missing features in Ubuntu?

---

### Post by theresaanna on 2012-04-28
> **F00RAX said:**
> I love you so much "theresaanna". My new laptop is mostly working now.
I'll tell you about my experience of installing Ubuntu 12.04 on my HP Folio 13 soon...

See you et merci ("I'm french speaker !")
So glad to hear it! Looking forward to hearing about your experience with 12.04.

Speaking of which, has anyone just upgraded from 11.10 -> 12.04? I'm weary about doing so but would LOVE it if it solved some of my outstanding issues. I've got some strange Flash player problems, can't seem to get any printer to work and the battery life still drains quickly. Granted, I haven't had much of a chance to invest serious time into investigating these problems. It would be nice if any of them were fixed for free in 12.04, though!

---

### Post by krige on 2012-04-28
> **theresaanna said:**
> I've got some strange Flash player problems

Try installing the [Flash-Aid add-on for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search") and run its wizard.

---

### Post by theresaanna on 2012-05-03
> **krige said:**
> Try installing the [Flash-Aid add-on for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search") and run its wizard.

Amazing! That sorted it out with such minimal effort. And in Chrome, too, not just Firefox, so I'm assuming that its a system-wide fix. Thanks, krige!

---

### Post by theresaanna on 2012-05-09
So, I just upgraded to 12.04 (64 bit) and kernel 3.2.0-24-generic and so far, so good! I wasn't able to print from my Canon iP4800 prior with any driver that I could find but I can now! Looks like my battery life has improved, too. 

Also, good news on the trackpad front! I can click, hold and drag now instead of having to double tap and then drag which only works for a certain distance.

ETA: Also some bad news on the trackpad front. I seem to have lost right click in most cases.

---

### Post by b_b on 2012-05-13
Hi, i've also experimented touchpad problems with new version of xserver-xorg-input-synaptics shipped with oneiric. 3 finger taps for middle click doesn't work anymore with xserver-xorg-input-synaptics 1.6.0-0ubuntu1~precise1.

Give a try to this :

```
synclient LockedDrags=0 TapButton3=2
```

Update about why this changed and how to fix it : [http://labo.eliaz.fr/spip.php?article94#precise](http://labo.eliaz.fr/spip.php?article94#precise)

++

---

### Post by krige on 2012-05-13
> **theresaanna said:**
> ETA: Also some bad news on the trackpad front. I seem to have lost right click in most cases.

Tap with two fingers for right click. I even like it more than the hard click :)

---

### Post by b_b on 2012-05-14
Hi, i have not lost the two fingers tap for right click. You may recover it with that command :

```
synclient LockedDrags=0 TapButton1=1 TapButton2=3 TapButton3=2
```++

---

### Post by trivialpackets on 2012-05-15
I was just looking at this laptop for an ubuntu laptop, glad to see it's a possible good fit!

---

### Post by theresaanna on 2012-05-19
I found a fix to bring back trackpad right click functionality in 12.04: [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18)

---

### Post by blfc on 2012-05-19
Hi there. Just bought an HP Folio 13 and found this thread to install Ubuntu 12.04 on it. I did the following:

Insert my usb-creator-gtk created pendrive with Ubuntu 12.04 amd64 desktop iso
Turn on machine, press ESC on boot, select F9 to boot menu
Quickly hold shift to get a boot prompt
Type live-install acpi_backlight=vendor and hit enter (no F6 or anything like that, just type live-install or live and add the parameter)
Ubuntu installed smoothly (I put 60MB for /, 60MB for /home and the rest for swap)

After installed, my first reboot got a black screen. After some pain I could get into the grub menu to manually add (again) acpi_backlight=vendor. Successfully boot so this time I edit /etc/default/grub to include the acpi_backlight=vendor on GRUB_CMDLINE_LINUX variable (dont forget to run update-grub after that)

Wireless OK, no need to fix anything. Suspend from menu is working. Bright/MM/wifi buttons not working. Volume buttons OK. Didnt test the HDMI yet

Bluetooth was recognized, I can scan my cell phone (and my cell phone can see the Folio machine) but transfers fail in both ways. Need to investigate that a bit more.

The trackpad is simply a piece of junk, I tried some of the suggestions on this thread and it is partially working. Also need to revisit it latter

I could not get ALT TAB to switch between windows, too, but I think this is an Ubuntu 12.04 problem, not HP fault. I am using gnome-classic wm (dont like Unity)

About hibernate: pm-hibernate suspends the machine but it will only resume correctly if you dont have encrypted swap space as stated [here](http://housegeekatheart.blogspot.com.br/2011/09/modify-encrypted-swap-partition-in.html) and [here](https://help.ubuntu.com/community/SwapFaq). To enable back disabled hibernate menu option [do as said here](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

I disabled fan and lower screen bright to extend battery life. Should I do some cpufreq tweaking too?

---

### Post by matizzz on 2012-05-22
Hi,

I am having some issues connecting the laptop to an external monitor using HMDI. I successfully connected it to an projector using HDMI. And to this monitor (HP, 23 inch) it works when I use a HDMI -> VGA converter. Now I try to use an HDMI -> Display port cable to connect it, but the monitor is not detected. 

Has anyone similar experiences or knows a way to debug this? 

Thanks a lot!

---

### Post by spidernik84 on 2012-05-25
Hi everyone,
I'm also using 12.04 on a Folio 13-2000. In addition to the well known touchpad and backlight problems, I had a very nasty issue that haunted me for half a day.
Somehow, I managed to hard-block the wireless card.

The output of rfkill list all showed this:

```

<output omitted>
2: hp-wifi: Wireless LAN
soft blocked: no
hard blocked: yes
<output omitted>

```

Resetting the status with rfkill unblock all did nothing. Curiously, unloading hp_wmi with rmmod hp_wmi immediately restored functionality. So I blacklisted that module and the wireless stopped working completely after reboot.
I re-enabled hp_wmi and still, hard blocked.

The solution was to reset the bios. None of the broadcom drivers are fixing the problem since this model (folio 13-2000) is equipped with an Intel Corporation Centrino Wireless-n 1030 (rev 34), and not a Broadcom chip.

Hope this helps someone googling around, because I couldn't find any solution regarding this odd issue.

---

### Post by ozonito on 2012-06-12
hi. Another Folio 13 user!!!

I installed Ubuntu 12.10 Alpha.

- Touchpad OK (2 fingers and both buttons)
- Fn keys not changes from ubuntu 12.04
- Screen black at starts (only works in trouble mode - graphics safe)
- Wifi OK.

Excuse my english,..):P

Best wishes From [Wasesores]("http://wasesores.com")

---

### Post by shenrik on 2012-06-12
How is the battery time coming along? Anyone want to do a quick test?

---

### Post by krige on 2012-06-12
> **shenrik said:**
> How is the battery time coming along? Anyone want to do a quick test?

What application do you suggest to make the test?

---

### Post by shenrik on 2012-06-13
Oh, just thought if someone could check how long it lasts when used "normally". That is, surfing, some flash videos, no heavy programs. Perhaps check highest vs. lowest screen light.

Or use a program of course, if thats easier.

Would be much appreciated :)

---

### Post by JackxLonsdale on 2012-06-13
I have been getting between 4-6hrs: really depends on how flash heavy your internet usage is. 

I use flashblock and firefox and if I don't look at any flash then maybe more than 6hrs with screen on 2nd lowest setting

If I have lots of flash videos and a brighter screen 4hrs - though the plus is that I don't think I have had much less than that!

---

### Post by Dej611 on 2012-06-18
Hi guys,

reading this topic I have been able to install Ubuntu 12.04 on my Folio 13.
Everything worked until I installed Skype and then upgrade.

I had this issue with the older version of Skype (2.2 beta) and either with the new one ( 4.0 ).

After the system upgrade firefox stops to work and then all applications just stop to interact: it looks their loading blinking on the bar but after few seconds it stops blinking and then nothing.
If I restart it stuck to:
* check battery state [ok]

and no more activity.

I tried with recovering the system, fixing broken packages, check the filesystem, start and older version but no solution...
If I start a tty1 while in stuck I can start the X server but what I get is no more than the mouse arrow.
If I start in recovery mode it stuck at the same point, but if I start a shell (tty1) from there and then write startx it loads the desktop but no interaction is allowed: of better, I have the same behaviour with blinking icons described before.

Tried also:
* sudo dpkg-reconfigure lightdm
* installing gdm and switched to it from lightdm
* set acpi=off in grub
* reinstalling grub

The kernel version that is not working is:
3.2.0-25-generic

The only previous version I have is:
3.2.0-23-generic

Anyone experienced the same issue?

---

### Post by alex wingnut on 2012-06-26
I have struggled for a few days now to reduce power consumption and fan noice. My battery lasts for about 7 hours now (normal browsing with wlan) and the fan is always off with few exceptions.

First step is of course to disable "fan always on" in BIOS and set the brightness to something significantly lower than max via brightness GUI or in rc.local (I use 800) as suggested earlier.

Second, even though changes in the power supply are recognized by the kernel and registered in /sys/class/power_supply/ACAD/online, an event is not always fired to upower, resulting in full power consumption when on battery (bug #994745). I have no solution to this bug yet but for those who prefer powersave over performance, I can recommend these workarounds to provide a more battery friendly permanent power profile:

Scale cpu's at boot in rc.local (default for me was performance):
[http://ubuntuforums.org/showthread.php?t=944190]("http://ubuntuforums.org/showthread.php?t=944190")

Set /sys/bus/pci/devices/*/power/control to auto (instead of on) for all devices that support it:
[http://serverfault.com/questions/279527/powertop-reports-bad-runtime-pm-for-pci-device]("http://serverfault.com/questions/279527/powertop-reports-bad-runtime-pm-for-pci-device")

I also used some of the advices from wiki.ubuntu.com ([https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)).
[LIST]
[*]Turn off bluetooth (obvious)
[*]Enable ALPM (risky)
[*]Enable rc6 (default was -1??)
[/LIST]

enjoy!

---

### Post by Nixie Pixel on 2012-07-05
Thanks to the good people of this thread, I've successfully installed 12.04 and resolved the screen brightness issue! I've set it to max brightness at boot and mapped the keys to CTRL-F2/F3. Not ideal, but until the function key problem is fixed it will do.

I'm noticing that I have some wireless performance issues. I'll randomly lose the ability to connect to servers for 15-30 seconds even though my wireless connection is supposedly active. I'm using the latest dist-upgrades and the 3.2.0-26 kernel. Any ideas about what could be causing that?

Thanks!

---

### Post by gryning on 2012-07-06
Disabling wlan0 power saving should sort this for you...

---

### Post by lobstar on 2012-07-07
Deleted

---

### Post by Nixie Pixel on 2012-07-09
It looks like it's calling my wireless connection eth0. And power management is off.

---

### Post by omicronkappa278 on 2012-07-11
OK:
 
This procedure for 12.04
 
[B]# Brightness
[/B]gksudo gedit /etc/default/grub
replace GRUB_CMDLINE_LINUX=”” with GRUB_CMDLINE_LINUX=”acpi_backlight=vendor”
sudo update-grub
Restart
 
Is an issue for me.
 
I am installing via a USB stick made with the windows Pendrivelinux installer. When I run the installer, I get to the option screen and I can hit "TAB" and add "acpi_backlight=vendor" and run it from a USB disk and install Ubuntu without issue. Once it is done, I cannot seem to find a way to boot to the installed version of Ubuntu and add this line to grub... So I booted back to the USB Live and added the line to grub.cfg on the hard drive... but I cannot run "sudo update grub" because it runs on the USB live version... I cannot see when Ubuntu boots up normally to even try to login and do any of this.
 
What do I do?

---

### Post by lobstar on 2012-07-11
Have you tried holding down the shift key while booting into the newly installation? That should bring up the grub menu and you can do the edit here.

---

### Post by omicronkappa278 on 2012-07-11
> **lobstar said:**
> Have you tried holding down the shift key while booting into the newly installation? That should bring up the grub menu and you can do the edit here.

There it is... got it. OK, when I boot in now the graphics are stuck at 1024x768... What now?

---

### Post by vkdir on 2012-07-13
I have a Folio 13 and just installed 12.04.  I had a wireless issue where it said "wireless is disabled by hardware switch".  Resetting the BIOS cleared my issue.  Now my problem is that suspend works but then doesn't bring back the trackpad.  Any ideas how to fix?

---

### Post by Copper Bezel on 2012-07-14
Is the trackpad just gone, or is it simply disabled through synclient? If you toggle something in gpointing-device-settings, does it come back?

You can send commands to Synclient on wake by creating a script and changing a setting in dconf, [here.](http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/) (The article names 11.10, but it's the same in 12.04.)

---

### Post by lobstar on 2012-07-16
> **arabxptyltd said:**
> 

```
$ sudo chmod 666 /sys/class/backlight/intel_backlight/brightness

```



I have to do this every time the machine has been restarted. 

Anyway to make it persistent?

---

### Post by vkdir on 2012-07-18
> **Copper Bezel said:**
> Is the trackpad just gone, or is it simply disabled through synclient?

It was a transient issue.  I haven't been able to reproduce the problem.  If it happens again, I'll try what you said.  Thx!

---

### Post by lobstar on 2012-07-28
I am having trouble with unsecured networks. I can connect to them but no connection to the internet.

Secured wifi works fine.

Anyone else having these problems?

---

### Post by blfc on 2012-09-01
> **gryning said:**
> Disabling wlan0 power saving should sort this for you...

Here is how to do that and it really solved the issue: [http://ubuntuforums.org/showthread.php?t=1686641](http://ubuntuforums.org/showthread.php?t=1686641)

Now one that I could not find a solution. If I remove the power cord ubuntu wont notice and still appears as charging. This way, when power go down it wont hibernate automatically

Other problem on hibernating is that ubuntu sometimes wont notice the power level being low thus not entering hibernate state. Any clues on how to solve that?

---

### Post by sportsdude81 on 2012-09-04
any body getting dropped packets and have their wireless internet drop in and out?  I did the fix for wifi and it worked fine until the latest update

---

### Post by Caradoc on 2012-09-05
I think most of the wireless problems come with Ubuntu recognizing the r8168 Ethernet controller as a r8169, and loading the wrong drivers.  This will work sometimes, but with some routers/connections it will keep going up and down, and either not connect, have slow bandwidth, or just suck power.

This problem is not unique to the HP Folio.  Do a google search to find other threads with the solution. "lspci" will show your network hardware.  I've forgotten where I got my copy of the r8168 driver, but [this thread]("http://ubuntuforums.org/showthread.php?t=1958899") seems to have it's own copy.

  --Caradoc

---

### Post by sportsdude81 on 2012-09-05
> **Caradoc said:**
> I think most of the wireless problems come with Ubuntu recognizing the r8168 Ethernet controller as a r8169, and loading the wrong drivers.  This will work sometimes, but with some routers/connections it will keep going up and down, and either not connect, have slow bandwidth, or just suck power.

This problem is not unique to the HP Folio.  Do a google search to find other threads with the solution. "lspci" will show your network hardware.  I've forgotten where I got my copy of the r8168 driver, but [this thread]("http://ubuntuforums.org/showthread.php?t=1958899") seems to have it's own copy.

  --Caradoc

I thought the r8168 was the NIC and the BCM4313 was the wireless hardware.  Ones broadcom and one is realtek so I don't think they are related.  Although I linked to the driver for the fix you mentioned for the nic previosly on this thread, so I got that under control.  

I believe I fixed my problem by following the directions on the first page of this thread and also adding this to the blacklist.conf:

```

blacklist brcmsmac
blacklist ssb
blacklist b43

```

got this from this arch linux wiki [https://wiki.archlinux.org/index.php/HP_Folio_13]("https://wiki.archlinux.org/index.php/HP_Folio_13")

---

### Post by giuscri on 2012-09-23
Hi there!, I'm quite new in Linux (annoying note).
I've just bought an HP Folio13 and tried how Ubuntu works on this machine.
Useless to say, with SSD hard drive and Linux, this machine flies for everyday usage.
Yet what I've noticed is that the battery sucks when runs Ubuntu.
 
I did not expect that: I've always thought power management was great on Linux and Macintosh computer -actually I found out the problem is likely to be in the drivers.
 
Now: because I bought this notebook especially to use it on-the-road I'm not really interested in an operative system if the battery lasts less than how it could last (or at maximum I might consider the choice of using it only if that is the only one chance).
 
I'd like you to ask if in these months -by using and improving it- you've found out which are the great tools one should use on this notebook to make it working ok, as far as the battery is concerned.
 
Truth to be told, I don't really need performance. What I really expect from Linux on this machine is a fast usage of the terminal and of a simple text editor (e.g. gedit).
 
All the rest is not really important. To cut the long story short, I could avoid the performance of this notebook in favour of the battery life.
 
Post scriptum: if you've found another Linux distribution that fits better on this notebook please let me know. :)
 
Thank you so much,
 
Gius

---

### Post by gryning on 2012-09-29
Most of the power usage issues are fixed with 3.4 and 3.5 kernel. I'm using 12.10beta2 with no issues, but anything with a recent kernel will probably improve your power consumption.

---

### Post by nelkz on 2012-10-04
Hiya Guys' n girls
been a long time since i used ubuntu, but recently got the folio13 and wanted to give it another go so.

went for 12.04
duel boot using windows installer

wifi fine
touchpad fine
screen (using nomodeset)
but stuck using 1024x768 resolution
cant get true 1366.x768 res

have the mesu utils installed
propriatory drivers are then and the intel graphics driver is in use
i have tried fix's for other graphics cards but still cant get it?

shows as vesa:intel sandybridge
experiance : standard

any ideas?
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  


thanks in advance
Nelkz

---

### Post by krige on 2012-10-28
Has anyone upgraded to Ubuntu 12.10?

---

### Post by krige on 2012-11-01
> **krige said:**
> Has anyone upgraded to Ubuntu 12.10?

Ok, I did it.

So far I haven't noticed any difference, except the appearance of these two general bugs affecting any Ubuntu 12.10 installation, not strictly related to the Folio 13:

1. A problem with the Dropbox indicator icon:
[https://forums.dropbox.com/topic.php?id=68578](https://forums.dropbox.com/topic.php?id=68578)

2. When opening a LibreOffice document directly from nautilus the menu bar is not displayed:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1064962)

---

### Post by berygod on 2012-11-07
Problem with brightness on startUp for the HP Folio 13 with Ubuntu 12.04
(worked for me)



 -Install xdotool: sudo apt-get install xdotool
- create a “myfile.sh” with the content:


```


 #!/bin/bash
myBrightness=2442;
currentBrightness=`cat /sys/class/backlight/intel_backlight/actual_brightness`;
count=$(( $currentBrightness – $myBrightness )) ;
while [ $count -gt 0 ]
do
         xdotool key XF86MonBrightnessDown
         let currentBrightness=`cat /sys/class/backlight/intel_backlight/actual_brightness`;
         let count=$(( $currentBrightness – $myBrightness )) ;
done

```


 - give it permisions: chmod 777 myfile.sh
- make it execute on the startup (startup applications>add)
- Note:  use your own myBrightness value for custom brightness.

---

### Post by soef on 2012-11-24
Hi there, I thought I would join in.

I just received my HP Folio, wiped it, and installed xubuntu 12.10.

My experience is fairly good. I had to adjust grub boot lines to get the right brightness and I used this link for a workaround for brightness control and going to suspend when closing the lid:

[https://github.com/deliciousrobots/ubuntu-hp-folio-13](https://github.com/deliciousrobots/ubuntu-hp-folio-13)

The only issue I have at the moment is the fan noise. I don't know how it responds in that other OS, but I think not all acpi settings are optimal... Does anyone have any ideas on how to reduce the fan noise?

---

### Post by chris.t on 2012-12-03
> **soef said:**
> Hi there, I thought I would join in.

I just received my HP Folio, wiped it, and installed xubuntu 12.10.

My experience is fairly good. I had to adjust grub boot lines to get the right brightness and I used this link for a workaround for brightness control and going to suspend when closing the lid:

[https://github.com/deliciousrobots/ubuntu-hp-folio-13](https://github.com/deliciousrobots/ubuntu-hp-folio-13)

The only issue I have at the moment is the fan noise. I don't know how it responds in that other OS, but I think not all acpi settings are optimal... Does anyone have any ideas on how to reduce the fan noise?

Re the fan - change the BIOS setting (can't remember which one now, but will be obvious) to stop it from running all the time.

---

### Post by krige on 2012-12-03
> **soef said:**
> I used this link for a workaround for brightness control and going to suspend when closing the lid:

[https://github.com/deliciousrobots/ubuntu-hp-folio-13](https://github.com/deliciousrobots/ubuntu-hp-folio-13)

That's interesting! How did you find it? Is it working fine?


> **soef said:**
> The only issue I have at the moment is the fan noise. I don't know how it responds in that other OS, but I think not all acpi settings are optimal... Does anyone have any ideas on how to reduce the fan noise?

Try disabling the "Fan Always On" option in the BIOS setup (press ESC on startup / F10 / System Configuration).

---

### Post by Elxyer on 2013-01-27
Hello everyone I just wanted to make a post for anyone who has or wants to upgrade to the most current version of Ubuntu 12.10 as of 1/27/2013

I have had to only follow a few steps to get my folio 13 running very well. 

Here are all of the things I did (thanks to this forum group! :D)
I just wanted to put everything in one place for those just coming in.


**1. Back-light on at start:**

open terminal and type ```
sudo nano /etc/default/grub
``` find the line that says ```
GRUB_CMDLINE_LINUX=""
``` and in-between those quotes type ```
acpi_backlight=vendor
```press: control-X, Y, and Enter to save the file you just edited.

**2. Fix Brightness Keys:**

open terminal and type ```
sudo apt-get install xbacklight
```type Y to confirm the installation.

You can close the terminal now.

Next open up Keyboard Shortcuts by going to 

System Settings>Keyboard>Shortcuts

click *Custom Shortcuts*

We are going to make two new shortcuts:
press the add shortcut button (+)

name:```
Brightness Up
```
command:```
xbacklight +10
```

create a second shortcut

name:```
Brightness Down
```
command:```
xbacklight -10
```

**3. Two Finger Scrolling**

Go to System Settings>Mouse and Touchpad>Touchpad

Select Two-Finger Scrolling.

**4. WIFI running as it should be 100% !**

you have to follow these steps in this exact order.

Open terminal and type

```
sudo apt-get install linux-headers-generic
```
then
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and finally
```
sudo modprobe wl
```

and then restart.

hopefully, if you were having problems with both wifi and wired internet, they will be running great.

Thanks everyone for helping me to get my folio 13 up and running better than ever!! And I hope this will help someone else in the future!=D>

And hopefully everything else that I didn't cover was already mentioned in this forum!

---

### Post by stefannagy on 2013-02-07
Hi,

I have a HP Folio 13-2000, I am a Debian user and I wrote a&#8230; well, let's call it a [collection of hardware-related bug reports]("http://wiki.debian.org/InstallingDebianOn/HP/Folio%2013%20-%202000/Wheezy").

I have a question for all **Folio 13-2000** users. Could you please try to reproduce a bug? If you want some background information please have a look at these two (closed) bug reports:
- [Debian Bug 52111]("https://bugzilla.kernel.org/show_bug.cgi?id=52111")
- [Kernel Bug 695634]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=695634")

Now, the thing is that you wouldn't know about this bug since the default values in Ubuntu send your notebook into hibernation when the battery reports 300 seconds remaining power. I'm affected by this bug since Debian uses the default GNMOE vales, which means my notebook would be sent into hibernation when the battery reports 120 seconds remaining power. Somewhere between 240 and 300 seconds the reported values won't change anymore. So the battery reports that I have 4 minutes and some seconds left when the battery drains and my notebook suddenly shuts down (and I loose all my unsaved data).

Now this is how you should be able to reproduce this bug:
- Open dconf editor.
- Move to *org.gnome.settings-daemon.plugins.power*
- change the following values: *time-critical* to *300* and *time-action* to *120* (remember the original values so that you are able to reset them later).
- Let your battery drain (be careful to save all data when battery level gets low) and please report back what happens.

It would be really great if you could tell me whether you can reproduce this bug (which means your notebook doesn't go into hibernation, instead your battery just drains) or if your notebook is successfully sent into hibernation (as it should be).

Thanks!

EDIT: **Forget it, I was wrong**: the default settings in Ubuntu seem to be *time-critical* = *300* and *time-action* = *120* as well. I don't really get why nobody seems to be affected by this bug. I can reproduce it not only on Debian and Ubuntu, but also in Windows 7 if I change the setting for critical battery action to 3% - and not only on one but **two** Folio 13-2000...

I believe it's a BIOS bug. But this seems unlikely since obviously nobody else out there is affected by this bug... If someone with a Folio 13-2000 has this problem, please answer me and make me happy :)

---

### Post by jayrod on 2013-02-23
[[COLOR=#000000]stefannagy[/COLOR]]("http://ubuntuforums.org/member.php?u=258396"), this is a great compilation.  Thanks.

While you are probably right, I have no need to change my battery alarms (I think the default is 5% for critical under Windows 7), nor do I care to ever let my battery get that low.  That said, if it ever does, I will change it to 3% for you :)

---

### Post by stefannagy on 2013-02-23
> **jayrod said:**
> While you are probably right, I have no need to change my battery alarms (I think the default is 5% for critical under Windows 7), nor do I care to ever let my battery get that low.  That said, if it ever does, I will change it to 3% for you :)

Yes, I think you're right: Windows 7 uses the percentage change (whereas GNOME uses the remaining time for its notifications and ciritcal battery actions by default) and will send your notebook into hibernation at 5 percent. When you try to reproduce this bug in Windows 7, maybe it's a good idea to set the critical battery value not to 3, but to 2 percent (further tests led me to the conclusion that the reported percentage will - at least sometimes - reach 3, but never 2 percent).

Since my warranty ends next week I tested this over the last two weeks and got in contact with HP support. They 'solved my problem' by telling me that I souldn't change the Windows default settings for the critical battery action and that my notebook 'works as designed'... ](*,) So the Folio 13-2000 is defective by design and since the vendor defines this BIOS bug as some kind of feature there's no hope that it will get fixed.

BTW: Since you seem to have a notebook with a Broadcom Wi-Fi adapter (see your posting #43 in this thread) I don't think it's an HP Folio 13-**2000**, probably your sub-model isn't affected by this bug at all.

Cheers,
Stefan.

---

### Post by wbar2 on 2013-02-24
The backlight part worked for me. Just make sure to run "sudo update-grub" after editing the command to update the files.

The brightness keys part also worked, but I have to press the Fn key with F2 and F3 to get them to work. Is there a way to reverse that?

Also wireless worked out of the box, so I didn't need to edit anything. When I first used a live usb it didn't work, but during the install it all of a sudden cut on.

Lastly, your two-fingered scrolling fix did the trick.

> **elxyer said:**
> Hello everyone I just wanted to make a post for anyone who has or wants to upgrade to the most current version of Ubuntu 12.10 as of 1/27/2013

I have had to only follow a few steps to get my folio 13 running very well. 

Here are all of the things I did (thanks to this forum group! :D)
I just wanted to put everything in one place for those just coming in.


**1. Back-light on at start:**

open terminal and type ```
sudo nano /etc/default/grub
``` find the line that says ```
GRUB_CMDLINE_LINUX=""
``` and in-between those quotes type ```
acpi_backlight=vendor
```press: control-X, Y, and Enter to save the file you just edited.

**2. Fix Brightness Keys:**

open terminal and type ```
sudo apt-get install xbacklight
```type Y to confirm the installation.

You can close the terminal now.

Next open up Keyboard Shortcuts by going to 

System Settings>Keyboard>Shortcuts

click *Custom Shortcuts*

We are going to make two new shortcuts:
press the add shortcut button (+)

name:```
Brightness Up
```
command:```
xbacklight +10
```

create a second shortcut

name:```
Brightness Down
```
command:```
xbacklight -10
```

**3. Two Finger Scrolling**

Go to System Settings>Mouse and Touchpad>Touchpad

Select Two-Finger Scrolling.

**4. WIFI running as it should be 100% !**

you have to follow these steps in this exact order.

Open terminal and type

```
sudo apt-get install linux-headers-generic
```
then
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and finally
```
sudo modprobe wl
```

and then restart.

hopefully, if you were having problems with both wifi and wired internet, they will be running great.

Thanks everyone for helping me to get my folio 13 up and running better than ever!! And I hope this will help someone else in the future!=D>

And hopefully everything else that I didn't cover was already mentioned in this forum!

---

### Post by stefannagy on 2013-02-25
> **wbar2 said:**
> The brightness keys part also worked, but I have to press the Fn key with F2 and F3 to get them to work. Is there a way to reverse that?

The default setting for the notebook's function-keys is 'Action Keys Mode': '<Enabled>' which means you don't have to press Fn+F9 to reduce volume for example (but only F9). If you want to press F9 (and not the action key), you'd have to press Fn+F9.

You can change this behaviour for all function-keys in BIOS: press ESC at startup, F10 to enter the BIOS Setup Utility and then navigate to System Configuration. Set 'Action Keys Mode' to '<Disabled>'. After that, the function keys work normally: when you press F9 you really get F9, when you press Fn+F9 you reduce volume.

I guess you don't want to change the behaviour for all keys but only for the brightness-keys – but that won't work.

PS: For more information about this issue see [bug #974568]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/974568").

---

### Post by wbar2 on 2013-02-27
Thanks! I had actually seen that option in the BIOS, but hadn't played with it. I think I will leave it setup the way it is right now. Thanks again for the help!

> **stefannagy said:**
> The default setting for the notebook's function-keys is 'Action Keys Mode': '<Enabled>' which means you don't have to press Fn+F9 to reduce volume for example (but only F9). If you want to press F9 (and not the action key), you'd have to press Fn+F9.

You can change this behaviour for all function-keys in BIOS: press ESC at startup, F10 to enter the BIOS Setup Utility and then navigate to System Configuration. Set 'Action Keys Mode' to '<Disabled>'. After that, the function keys work normally: when you press F9 you really get F9, when you press Fn+F9 you reduce volume.

I guess you don't want to change the behaviour for all keys but only for the brightness-keys – but that won't work.

PS: For more information about this issue see [bug #974568]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/974568").

---

### Post by suprman2020 on 2013-03-03
Currently using the 13.04 alpha(?) on the 1029wm model. Brightness, media, and wireless keys don't work. Closing laptop does not suspend but suspend works manually. Broadcom wifi doesn't work all that well until you fix it. And you still have to add those parameters to grub so the backlight can turn on at boot. Seems like most of the problems from 12.10 still exist in 13.04 currently. This is using 3.8.0-9 kernel.

---

### Post by wbar2 on 2013-04-09
deleted

---

### Post by krige on 2013-04-25
I have installed Ubuntu 13.04 on top of the previously installed Ubuntu 12.10 on my HP Folio 13. Here are my first impressions.

**What works out of the box**
[LIST]
[*]the wireless card works on my model (1000el);
[*]closing laptop lid suspends the system and opening it turns the system back on;
[*]the power indicator correctly shows when plugged or on battery;
[*]the volume function keys work;
[*]the media function keys work;
[*]the two finger scrolling works, but it's still not enabled by default: to enable it you still need to go to System Settings > Mouse & Touchpad > Touchpad and select Two-Finger Scrolling;
[*]all the things which worked on the previous version, like the bluteooth, the webcam, the touchpad, the speakers, etc.
[/LIST]

**What works with some tweaking**
[LIST]
[*]screen back-light is off: to fix it append "acpi_backlight=vendor" to GRUB_CMDLINE_LINUX in etc/default/grub. There is a bug opened for this issue on Launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780625);
[*]the two special keys for brightness +/- and the wireless adapter toggle don't work: to fix it append "acpi_osi=" to GRUB_CMDLINE_LINUX_DEFAULT in etc/default/grub. There is a bug opened for this issue on Launchpad [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/994745](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/994745);
[/LIST]

Summing up, this is what you need to do:

```
sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

sudo update-grub
sudo reboot
```


**What does not work**
[LIST]
[*]the touchpad on/off toggle on the top-left corner of the touchpad doesn't work;
[*]the brightness level is not maintained from one session to the next: it is set to maximum at every boot;
[*]the speakers maximum volume is still way much lower than in Windows.
[/LIST]

**General notes about Ubuntu 13.04**
[LIST]
[*]multiple desktops are missing;
[*]Eclipse has not been updated to the most recent version Juno 4.2, it's still the old Indigo 3.8;
[*]Gnome has not been update to the most recent version 3.8, it's still the old 3.6;
[*]LibreOffice has been updated to the most recent 4.0.2.
[/LIST]

Here is a screenshoot of my partition layout:
[ATTACH=CONFIG]241898[/ATTACH]

---

### Post by Sabonmu on 2013-04-26
I've just installed Ubuntu 13.04 in the recovery partition, dual boot with Win 7 64 bit, on my HP Folio 13.
ABSOLUTELY BRILLIANT!!!
I was only going to run live, to see what worked, what didn't, but everything: screen, wifi, keyboard, external screen, sound, blue tooth mouse, Worked!
So I installed the 64 bit version of 13.04 on the 10Gb revovery partition, formatting to ext3.
Rebooted, held my breath, and Win 7 was there and booted fine (I need it to print on my multi print scanner).
Whoopee!
Next, installing Gnome desktop, already done Synaptic.
I remember the problems I had with 12.04: blank screen, not recognition of Win 7.
This is slick!

---

### Post by martincernvall on 2013-04-28
> **Sabonmu said:**
> I've just installed Ubuntu 13.04 in the recovery partition, dual boot with Win 7 64 bit, on my HP Folio 13.
ABSOLUTELY BRILLIANT!!!
I was only going to run live, to see what worked, what didn't, but everything: screen, wifi, keyboard, external screen, sound, blue tooth mouse, Worked!
So I installed the 64 bit version of 13.04 on the 10Gb revovery partition, formatting to ext3.
Rebooted, held my breath, and Win 7 was there and booted fine (I need it to print on my multi print scanner).
Whoopee!
Next, installing Gnome desktop, already done Synaptic.
I remember the problems I had with 12.04: blank screen, not recognition of Win 7.
This is slick!

Thank you for this info!

Could you please be a little bit more specific on your installation procedure? And could you please submit a screenshoot of your partition layout?

Thanks in advance!

---

### Post by krige on 2013-05-01
Appending "acpi_osi=" to GRUB_CMDLINE_LINUX_DEFAULT in etc/default/grub fixed both the problem of the two special keys for brightness +/- and the wireless adapter toggle not working in Ubuntu 13.04.

```
sudo gedit etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

sudo update-grub
sudo reboot
```

---

### Post by JackxLonsdale on 2013-05-01
I have tried the acpi_osi= change in grub with 13.04 but do not seem to be able to get it to work for me. Additionally suspend on lid close does not seem to work either..?

---

### Post by jayrod on 2013-05-05
> **JackxLonsdale said:**
> I have tried the acpi_osi= change in grub with 13.04 but do not seem to be able to get it to work for me. Additionally suspend on lid close does not seem to work either..?

Worked for me to get the brightness controls working under Ubuntu 13.04 on an HP Folio 13 1020us.

---

### Post by JackxLonsdale on 2013-05-31
Managed to get it working after I updated the BIOS. Followed the instructions on the Debian wiki if anyone was wondering how to do this: [http://wiki.debian.org/InstallingDebianOn/HP/Folio%2013%20-%202000?highlight=%28%28InstallingDebianOn%7CHP%7CFolio+13+-+2000%29%29]("http://wiki.debian.org/InstallingDebianOn/HP/Folio%2013%20-%202000?highlight=%28%28InstallingDebianOn%7CHP%7CFolio+13+-+2000%29%29")

---

### Post by density on 2013-06-26
A few days ago, i installed ubuntu 13.04 on my HP folio, and I noticed that the power indicator is not working, and is strange because in 12.04 worked perfectly fine. Also, the acpi_osi modification in grub does not work for the suspension with lid closed. Later i'll try the fix suggested by JackxLonsdale

---

### Post by azevedo on 2013-07-02
> **JackxLonsdale said:**
> Managed to get it working after I updated the BIOS. Followed the instructions on the Debian wiki if anyone was wondering how to do this: [http://wiki.debian.org/InstallingDebianOn/HP/Folio%2013%20-%202000?highlight=%28%28InstallingDebianOn%7CHP%7CFolio+13+-+2000%29%29](http://wiki.debian.org/InstallingDebianOn/HP/Folio%2013%20-%202000?highlight=%28%28InstallingDebianOn%7CHP%7CFolio+13+-+2000%29%29)


Hey JackxLonsdale, thanks for you post! Before reading it I had tried to uptade the grub with no success. Almost hopeless i gave my last try updating the bios and now the action keys are working perfectly. My old BIOS was F.14. I hope it work as well for the rest of you guys

---

### Post by sportsdude81 on 2013-08-11
> **elxyer said:**
> Hello everyone I just wanted to make a post for anyone who has or wants to upgrade to the most current version of Ubuntu 12.10 as of 1/27/2013

I have had to only follow a few steps to get my folio 13 running very well. 

Here are all of the things I did (thanks to this forum group! :D)
I just wanted to put everything in one place for those just coming in.


**1. Back-light on at start:**

open terminal and type ```
sudo nano /etc/default/grub
``` find the line that says ```
GRUB_CMDLINE_LINUX=""
``` and in-between those quotes type ```
acpi_backlight=vendor
```press: control-X, Y, and Enter to save the file you just edited.

**2. Fix Brightness Keys:**

open terminal and type ```
sudo apt-get install xbacklight
```type Y to confirm the installation.

You can close the terminal now.

Next open up Keyboard Shortcuts by going to 

System Settings>Keyboard>Shortcuts

click *Custom Shortcuts*

We are going to make two new shortcuts:
press the add shortcut button (+)

name:```
Brightness Up
```
command:```
xbacklight +10
```

create a second shortcut

name:```
Brightness Down
```
command:```
xbacklight -10
```

**3. Two Finger Scrolling**

Go to System Settings>Mouse and Touchpad>Touchpad

Select Two-Finger Scrolling.

**4. WIFI running as it should be 100% !**

you have to follow these steps in this exact order.

Open terminal and type

```
sudo apt-get install linux-headers-generic
```
then
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and finally
```
sudo modprobe wl
```

and then restart.

hopefully, if you were having problems with both wifi and wired internet, they will be running great.

Thanks everyone for helping me to get my folio 13 up and running better than ever!! And I hope this will help someone else in the future!=D>

And hopefully everything else that I didn't cover was already mentioned in this forum!

Are you having signal and speed problems with the Wifi.  It connects great but it only shows 2 bars and i am 6 ft away from the WAP.

---

### Post by Elxyer on 2013-09-06
Alright!

So here I was I have done up to date (9/6/2013).

I first updated to 13.04 with minor complications (such as /boot being too full) so i just removed old files that were taking up space.

The hot-keys are now working perfectly (brightness and wifi toggle), but I first had to update BIOS just as JackxLonsdale suggested.
My folio model is 'Folio 13-1029wm' and for others who are updating their BIOS make sure you follow the guide exactly, just use the proper firmware for your specific folio model.

I also made some little adjustments:
follow this microcode update after updating the BIOS [https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

---

