---
title: "Ubuntu 7.04 (Feisty Fawn) on a Compaq Presario C571NR"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by peabody on 2007-09-25
[B]I still haven't gotten around to cleaning up this guide, and I probably never will because it's likely that I'll be upgrading to gutsy upon release.

I'm too lazy to update the text below, so I just thought I'd add some quick updates here:

Instead of using the synclient command you can install the gsynaptics package which will give you a touchpad control panel in your preferences

There are problems with compiz and suspend.  I would recommend not using compiz (desktop effects) if you need functional suspend.  It will seemingly work in compiz, but intermittently fail.

I have since tested wpa, it works fine.

Wireless has issues coming back up from sleep sometimes.  Attempting to switch to another wireless network and then back seems to fix this.

Adding position_fix=1 to the snd-hda-intel module parameters makes audio recording work in the recordmydesktop program

I finally found a fix for recording in audacity.  Open audacity, go to Edit>Preferences.  Under Audio I/O, set both the playback and recording device to "ALSA: HDA Intel: CONEXANT Analog (hw:0,0)".  Then under Quality, set the default sample rate to 48000 Hz.  Now quit and reopen audicity.  Make sure the Int Mic switch is checked under the gnome volume control.  Now recording should work.

I've since used directions the following post to upgrade to xrandr extension 1.2 and I can now use xrandr to dynamically clone my desktop on the vga out:
[http://ubuntuforums.org/showpost.php?p=3451365&postcount=8](http://ubuntuforums.org/showpost.php?p=3451365&postcount=8)
Note that this requires using the xserver-xorg-video-intel drivers which is contrary to my advice below.

I have gotten the tickless kernel and power top working by using the script in this thread:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
and using this package:
[http://www.getdeb.net/search.php?keywords=powertop](http://www.getdeb.net/search.php?keywords=powertop)
[/B]

I took a gamble on this laptop just a few days ago as the price was just too good for me to pass up (there's probably better deals, but heck, it was under $500).  I am happy to report that (after a very long struggle) I have been victorious in getting a stable install of Ubuntu 7.04 on the beast with nearly every hardware feature supported.  Never been so happy to nuke a Vista install.  I documented the experience so I wouldn't forget anything in case I ever had to reinstall.  I'm posting this in hopes it helps somebody trying to use Ubuntu on the same machine.  It's not the easiest of installs, but once everything is up and running, the thing just purrs (not to mention it runs about 100x faster than when it was chugging along with Vista!).

I'm willing to attempt to answer any questions regarding the laptop and Ubuntu.  This guide is messy because I constructed it quickly over the last three days as personal notes instead of as a walk through.  If people would like me to clean this up and turn this into something more informative, let me know.

Main problems...sound and dvd burning mostly.  They work, but I'm still having slight annoyances with them.

What's working: Just about everything else but I did not test the following:
Modem
S-video
Wpa on wireless (should probably work once wireless is working according to the wiki page).

Outline of the install goes like this:

Install Ubuntu from LiveCD
Reboot
Plug into wired network and install necessary software for the Broadcom card
Configure the Broadcom wireless card
Reboot
Configure X
Reboot
Download latest alsa and compile and install
Configure Sound
Reboot

My checklist of stuff to configure for the post install...
Turn off mouse tapping for single-click
Remember to change paper size on printers to US Letter (c'mon can't the install figure this out when we tell it our timezone?).
Install openssh-server package for remote login.
Patch i810switch tool to work with i945 adapters and recompile ([https://bugs.launchpad.net/ubuntu/+source/i810switch/+bug/92528](https://bugs.launchpad.net/ubuntu/+source/i810switch/+bug/92528)).  This makes it so I can use the vga out without futsing with xorg.conf.  However, it does not work very well with the i810 driver.  It's still useful to use when you've got a clone or dual setup running, it will let you turn your lcd or external monitor on or off.
Setup firestarter which needs a fix to prevent network manager conflict (details here: [https://help.ubuntu.com/community/Firestarter?highlight=%28firestarter%29](https://help.ubuntu.com/community/Firestarter?highlight=%28firestarter%29)).

Wireless works once the necessary steps for enabling the Broadcom card were followed on the Ubuntu wiki here (use step 2b): [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29).  It works perfectly with network manager, which was a huge surprise to me because I've had nothing but trouble with network manager in the past with cards with native drivers, let alone one hacked into compliance with ndiswrapper.

Sleep/suspend for the laptop seems to work flawlessly, network connection is restored upon wake-up, albeit a bit slowly (takes a minute for it to get back up sometimes).

Hardware acceleration works flawlessly.  Games and compiz seem to work right out of the box.  Xv accelerated video playback works, but not while running compiz however.  I may look into opengl output plugins for my video players.  Xinerama dual display works, although apparently not with Dri, so no compiz on Xinerama either.

It took me a while to find a way to turn off the tap-to-click feature of the builtin synaptics touchpad (I HATE tap-to-click, it is incredibly stupid, I don't know anyone who likes it).  It's not a feature of the gnome mouse control panel.  Googling proved fruitful as I found a couple things to add to my xorg.conf.  I added the following line in the "Synaptics Touchpad" input device section:

Option        "SHMConfig"

Then I rebooted and ran this from a terminal to turn off the tapping feature

synclient TapButton1=0

This line of code can be run at login via the sessions control panel to keep this bad feature permanently turned off.  I was pleasantly surprised to discover that the vertical scroll wheel on the touch pad worked (not the horizontal though).

In summary, I was able to verify that all of the following items work:

Networking:
Ethernet: No problems here, worked with the live cd and a fresh install.
Wireless: works after following the installation instructions on the Ubuntu wiki.  For step two, I chose section 2b.  I followed the instructions to the letter.  Seems quite stable as it will continue to work after a resume from suspend, after manually turning it off by pushing the wireless button.  Works directly with network manager; literally no problems once up and running.  NOTE: I did not test wpa as I don't use that on my home network, but my guess is that it probably works.
Modem: I did not test the modem.  I hear it's a winmodem and there are apparently some hairy problems with it.  I haven't had to deal with dial-up in a while, so hopefully this won't come back and bite me in the *** some day.

Video:
Intel i950 graphics adapter: Fresh install only gets resolution of 1024x768 (acceleration and suspend worked though).  Two things can be done to fix this, installing the 915resolution package (recommended), or installing the xserver-xorg-video-intel package and changing the driver name from i810 to intel.  I highly recommend using 915resolution as I couldn't get xinerama working with the xserver-xorg-video-intel driver (server segfaulted).  However, playing back high resolution videos ( >= than 1024x768 ) causes video players to seg fault in the i810 driver.  The intel video driver doesn't have this problem, so it's a toss-up based on your needs.  Myself, I wanted Xinerama for hooking up to projectors.  Bummer is the two methods are mutually exclusive; when installing one driver, the other driver will be automatically uninstalled.  Card gives full 1280x800 resolution with dri.  Hardware acceleration was good.  Compiz works, though not with Xv.  Xinerama and clone setups worked (without dri, though with Xv playback).  I followed this guide for that:
[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)
Video out worked fine, I did not test the s-video out yet, I will update this post when/if I can.  My guess is that it probably works fine.

Power/Sleep/Buttons/Suspend/Hibernate:
Power Button doesn't seem to do anything while on, volume up/down and mute buttons work flawlessly.  Wireless button works flawlessly.  Suspend works flawlessly with properly configured video.  Hibernate worked flawlessly with properly configured video (and seemed fast for a hibernate too).

Sound: I experienced the most issues here (felt like it anyway, even though everything mostly works now).  Sounds worked from a fresh install (after updates applied), but there were two big issues: 1) speakers didn't mute upon plugging in headphones, and the mic seemed to have issues.  I fixed the speaker but the mic still has issues.  I followed the instructions on this page: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).  The key seemed to be setting my module options for snd-hda-intel to "model=laptop" (put a line at the end of the /etc/modprobe.d/alsa-base file).  I'm not sure that I even needed the new alsa, as I tried the module thing after installing it.  That solved both problems for the most part.  Volume level is a little low.  Full-cranked volume is pretty loud, but it tapers off quick.  Half volume is almost inaudible.  I had to go into the Volume Control and pretty much enable everything to get my mic recording, but full-duplex recording off the mic works now in skype.  I'm still having problems with the mic in Audacity and Jokosher.  I can't get any sound in Half Life (or wine in general for that matter).

Note: Do not use alsa later than 1.0.14.  I tried the very latest 1.0.15rc2 (just to be safe) but it seemed to have multiple issues including lots of "popping" and feedback.

Note: kernel updates overwrite the new alsa-driver install, so that will have to be reinstalled after every kernel update.

DVD-Writing:
The built-in gnome burner seems to work fine, but of course that burner sucks so I installed k3b right away.  **Edit: The following isn't true, K3B does work, just not for burning CD images for some reason.  There seems to be a bug in launchpad that might be related to this**: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/51939](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/51939)

_K3b does not work at all for some reason.  I've tried switching the programs settings to cdrskin, that didn't fix it.  There seem to be lots of errors messages on the dmesg console while k3b tries to burn too.  I'm still investigating and may file a bug report.  Brasero works however, and I'm fairly happy with it, but it seems to burn more slowly than I want.  Doesn't seem to report burn speeds properly either._

Despite the problems however, I've been very happy with this setup.  On the whole, if you're looking for a cheap, modern, Linux laptop, and you don't need firewire/ieee1394 or a pc-card slot, you can't go wrong with this machine folks.  15.4" WXGA screen, Intel dual-core 1.74Ghz, DVD-Writer, 1gig ram, 80 Hard drive.  Built sturdy yet lite.  Under $500 even after California sales-tax.

---

### Post by pvilleSE on 2007-10-07
Thank you for your hints.  I have not done everything yet but like you said I'm not to worried about getting everything working since gusty is only 11 days away.  I got my wireless working good.  The other thing I really want working now is the sound, I followed the instruction from you link and set the model=laptop but my sound still does not work.  Did you do anything else that you might have forgotten to mention.

Thanks for any help

**edit: When I booted today the sound is working now, so I don't know why it didn't work yesterday after I rebooted.  All well, thanks again for your guide.**

---

### Post by peabody on 2007-10-08
> **pvilleSE said:**
> 

**All well, thanks again for your guide.**

I'm really glad I was able to help :).  No one had responded to the thread, so I was beginning to think no one else had this laptop, glad to see someone else out there with it.

Let me know if you end up with intermittent suspend problems, and whether or not you get suspend working with compiz consistently.  Now that I've been using this laptop for some time now, I've noticed that suspend seems to work about 90% of the time, but certain things seem to make it crash (having openoffice.org Writer open seems to be a bad thing, oddly enough).  I just converted to the suspend utility mentioned in this guide: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855).  I'll let you know how that goes.

Also, I got sound in wine working by installing the alsa-oss package and running my games via the aoss wrapper program.

Edit: I didn't convert to the s2disk utility because hibernate didn't seem to work with it.

Edit2: Nevermind, s2disk works.  I was having problems because I had setup an encrypted swap partition.  I undid that since I didn't think it was that important and now s2disk is working for me.

---

### Post by Impact4ever on 2007-10-16
Hey, Thanks for the notes, it came handy in putting the system together. i just needed to make a few new tweeks but other than that your guide helped out a lot.:guitar:

---

### Post by Pawcatuck on 2007-12-15
Hi Peabody,

Just to let you know, I bought one of those laptops a few weeks ago (also under $500, even with our sales tax, which probably rocks as hard as California's) and had my introduction to Vista and the future of computing. That experience caused me to soak up a shot of courage and install Ubuntu 7.04.

It's been painless, and a lot of fun. I've even managed to move most of my job over to Ubuntu. I can actually boot up and start working within a couple of minutes. I thought those days were done when I finally had to let go of DOS 5.

I haven't had any problems with suspend, and I have OOo Writer open a lot. But I've got the bare bones Gnome desktop going here.

I haven't been able to check out whether the WiFi really truly works because I haven't been to the library lately to get on their public WiFi network. If I run into any unexpected trouble, I'll refer to the pointers you kindly posted. Thanks for taking the time to write all that up!

---

