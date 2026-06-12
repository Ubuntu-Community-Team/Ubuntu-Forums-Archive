---
title: "HP dm1z with AMD Fusion APU"
date: 2011-03-14
forum: Hardware
---

### Post by roberts3000 on 2011-03-14
I am thinking of buying this laptop. I was just wanting to know others experience running ubuntu on it.

Thanks

---

### Post by devguy on 2011-03-15
What works great out of the box:
[LIST]
[*]Bluetooth
[*]Sound
[*]Ethernet
[*]USB
[*]Keyboard
[*]Webcam
[/LIST]

What works with some effort
[LIST]
[*]Graphics (and HDMI video/audio)
[LIST]
[*]Install Catalyst 11.2 in Maverick
[*]Disable Gnome screensaver to avoid freezing
[*]Offers proper handling of fan speed as well
[*]Suspend and hibernate also seem to work correctly
[*]I'd also advise clicking on Tear-free desktop and disabling Vari-bright in the Catalyst Control Center.
[/LIST]
[*]Wifi
[LIST]
[*]There's a guide [in here]("http://ubuntuforums.org/showthread.php?t=1645716&highlight=dm1z&page=5") to help you get going.
[*]Works great with WPA2 afterwards, but requires a redo of the process for each new kernel update.  I'd advise you to install Ubuntu, use the ethernet port to get to the most recent 2.6.35 kernel, and then follow the guide.
[*]Native support should be in the 2.6.39 kernel (please backport this to Natty Canonical!!!!!!!)
[/LIST]
[*]VAAPI
[LIST]
[*]Install [these]("http://www.splitted-desktop.com/~gbeauchesne/") libs after Catalyst 11.2, and then follow [this]("http://forum.xbmc.org/showthread.php?t=86581") guide to get support in XBMC.
[/LIST]
[*]Virtualization
[LIST]
[*]Need to enable SVM in the BIOS, and then you have proper support in Virtualbox.
[/LIST]
[*]TRIM support on SSDs
[LIST]
[*]Follow [this]("https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu") guide.
[/LIST]
[/LIST]

What still is not working right:
[LIST]
[*]Clickpad
[LIST]
[*]Super jumpy by default, with only left mouse button working, no-multitouch, click and drag is impossible, and tapping in the upper left doesn't disable clickpad.
[*]You have two routes to take: have a physical left click only, but two-finger scrolling, and two tap right click; or no scrolling, but a physical left and right click.  Both fix the jumpiness (for the most part), but still no getting click and drag or clickpad disabling support.  I opted for the first choice, and [here's]("http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/") a guide.
[*]Doesn't seem to be fixed in Natty either (but oddly, some people have had better luck with Lucid).
[/LIST]
[*]Natty Alpha 3 "try out without installing mode"
[LIST]
[*]The installer itself functions fine (select it from the boot menu on the live CD), but the actual testing of the desktop hangs once it loads (you can see the wallpaper, but nothing else works).
[/LIST]
[*]Severe mouse lag in Wolfenstein: Enemy Territory (even with USB mouse)
[LIST]
[*]I bet this is just something my fault and may not be DM1z specific (works fine on my desktop with same mouse), but I can't seem to get it fixed for the life of me.  Any ideas?  Only happens with this game, and even USB mouse works great on desktop.
[/LIST]
[*]Microphone/Headphone hybrid port
[LIST]
[*]What a dumb decision by HP to put this on there...  Anyway, if you plug a headphone in there, it works fine and properly disables the speakers.  However, there doesn't seem to be anyway to tell Ubuntu to use it as a microphone port instead.
[/LIST]
[/LIST]

Not Tested:
[LIST]
[*]Card Reader
[/LIST]

Experience:
[LIST]
[*]Wolfenstein: Enemy Territory (aside from mouse issue) runs great on this machine (occasional slowdown with super wide-open spaces) with default settings at 1366x768
[*]Dolphin-emu:  Runs like crap, even with everything on low with 640x480 (tested on Super Smash Bros: Melee) even with dual-core optimizations.  Might be playable in Windows with the DX11 
[*]plugin, but haven't tried.
[*]XBMC: plays 1080p h.264 files fine (even through hdmi) with VAAPI, but CPU usage is still around 30-40% for me (anyone find that a little high?).
[*]Adobe Flash: Using plugin 10.2 (haven't tried 10.3), very smooth all the way through 720p.  1080p is a slideshow.  C'mon Adobe, add VAAPI support as well as x86-64 support.
[*]Oracle VirtualBox: Installed TinyXP inside (yes, I have a legal unused license of Windows XP, but I wanted a slim version) for Netflix/Silverlight, as well as iTunes (for my iPhone).  Netflix runs great in 480p mode with VirtualBox guest additions installed, but no go for HD.  iTunes sucks all around in performance, but to be fair, it is the same thing natively in Windows.  Boo Apple.
[*]Battery life: around 5-6 hours browsing with wifi/bluetooth on, and screen on medium brightness.
[*]Speaker Quality: much better than most netbooks (has stereo Altec Lansing), but still not great.
[*]Noise/thermals: at the desktop/browsing, the fan is pretty quiet.  Run anything 3d intensive, and the fan kicks up high in seconds (using Catalyst 11.2).  Stays quite cool throughout (even while gaming).
[*]Keyboard is the best I've ever used on a laptop before.  Well done HP.
[*]Charger: gets alarmingly hot while charging this laptop.  Be aware!!!
[/LIST]

Tested using Ubuntu 10.10 AMD64

---

### Post by roberts3000 on 2011-03-15
Wow, thats an awesome post. Thanks.

I have been trying to decide between the dm1z and the dm3t (13.3in core i3, intel GPU) for weeks now.

Does suspend or hibernate work?

---

### Post by devguy on 2011-03-15
> **roberts3000 said:**
> Wow, thats an awesome post. Thanks.

I have been trying to decide between the dm1z and the dm3t (13.3in core i3, intel GPU) for weeks now.

Does suspend or hibernate work?

I didn't try suspend or hibernate before installing Catalyst, but afterwards, they both seem to function fine.

As for the DM3t, it has a bigger screen with a lower resolution, the Core 2 will handily beat the e350 in CPU performance, the e350 GPU will handily beat the optional GeForce 105m (the Intel GPU standard is worthless), battery life shouldn't be much difference, and the touchpad on the DM3t has separate buttons, but I hear it is still awful.  Not too mention, I purchased my DM1z for ~$400 after coupons and California tax/recycling fees.  The DM3t is significantly more expensive.

---

### Post by t0adman on 2011-03-21
Hey guys,

I running the 11.04 Daily Build for AMD 64-bit from my pen drive on my dm1z-3000 and I'm noticing everything you mentioned **devguy**, except my Bluetooth won't work.  When I click on Preferences it opens up the window and says Bluetooth is disabled with a big button in the middle that says Turn on Bluetooth.  When When clicked it grays out and does nothing.  Mouse (Logitech Bluetooth travel mouse) in discovery mode, etc and worked fine in 10.10.

Thoughts?

---

### Post by i_grok on 2011-04-05
Just reporting that I have everything up and running in Ubuntu 10.10 thanks to this thread.

AMD has released a new Catalyst driver. I'm running version 11.3 with no problems so far.

I thought WIFI was working fine with unpatched drivers, but WEP was broken. The stock RT5390 driver worked with WPA2, but there was a lot of spew in dmesg... Now running the openSUSE patched drivers and WEP works.

---

### Post by c3lticmatt on 2011-05-30
You say installing catalyst gives fan control. I have installed catalyst but can find no settings for fan speed. Some people have mentioned turning on ACPI in BIOS for other HP laptops but I have not managed to find such a setting on this laptop. Any assistance would be appreciated; the fanspeed stays high all the time at the moment despite the APU temperature only being ~40C.

---

### Post by djjustin on 2011-06-03
[QUOTE=devguy;10562797]
[LIST]
[*]Disable Gnome screensaver to avoid freezing
[/LIST]

What did you do to disable this? I'm having user-switching problems with the ATI driver and suspect gnome-screensaver.  Uninstall/install xscreensaver seems like a drastic option.

---

### Post by mo_roodi on 2012-11-29
Have you had any problems running external monitors from your DM1?

I've bought mine about 5 months ago and I've not been able to get the catalyst drivers to work properly and I'm wondering if anyone else has come across the same problem. 

Basically here's the deal: 
  - Using the laptop screen works a treat. 
  - Using a single external monitor on it's own works a treat.
  - Extending the desktop across the laptop screen and an external monitor (19" 1280x1024) complains that the selected resolution is greater than the supported resolution. 
  - Using 2 external monitors (with the laptop screen disabled) - 1x 19" 1280x104 and 1x 17" 1280x1024 - complains about the resolution being too high. 

To further complicate matters if I run the open source driver I can use my monitors in any configuration I like without any problems (but I don't get the nice hardware acceleratedness that the AMD drivers give me). 

Does this make sense and if so has anyone come across this issue? Did you manage to fix this issue?

M

---

