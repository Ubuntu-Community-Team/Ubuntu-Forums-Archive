---
title: "'Detect Displays' stopped working for external LCD"
date: 2008-05-27
forum: Hardware
---

### Post by 655 on 2008-05-27
As of this morning, the 19'' Acer LCD monitor I have connected to my laptop's VGA-out is no longer being detected properly in Screen Resolution panel.

The monitor works, but instead of being detected as "Acer 19''", it is listed as "Unknown," and is capped at an upper resolution of 1280x800 (as this is not a widescreen monitor, the picture is squashed).  Normally it enables a max res of 1280x1024.  I have to drop down to 1024x768 to get a functional image.

What could have caused the "detect displays" to stop working?  

Since upgrading to Hardy, one of the things I'd been really delighted with was that the Screen Resolution panel was finding the proper displays for my screens out of the box, which I'd struggled with in the past  (my laptop has the shoddy Intel 82852/82855 GM integrated video chipset, and I am no wizard at editing the xorg.conf).

I noticed this change after installing some updates and rebooting; there were some upgrades to the main kernel, but... any correlation?

---

### Post by bastineman on 2008-06-05
I am having the same issue after upgrading from 7.10 32bit -> 8.04 x64 (clean install) on my Dell Latitude D830. I use the dock/port replicator with a 2408WFP connected via DVI.

I used to be able to dock and undock using nvidia-settings to detect the external LCD and enable it. Now, when I dock, detect displays does nothing. However, if I restart gdm/X CTRL-ALT-BKSPC and run nvidia-settings "detect displays" DOES work. The X restart is a bit annoying. I don't use nvidia-settings to save an xorg.conf file - I have a static xorg for just my laptop LCD and set my dock LCD every time.

Anyone?

---

### Post by 655 on 2008-06-05
I don't have an nvidia card, so when I talk about the 'Detect Displays' option, I am referring to the System > Preferences > Screen Resolution, aka gnome-display-properties.

Nevertheless, what was causing me problems in the end was the fact that I was, despite controlling the two screens via the software panel (which allows you to turn them on or off), also toggling the VGA-out button on the laptop with the use of the function keys, in addition to yanking out the VGA cable at random when I wanted to move the laptop around the house (I don't use a dock).  This last bit shouldn't cause problems in and of itself, but upon reconnecting the VGA cable, I would often forget and resort to 

Since the settings for resolution and dual- or single-display were being saved in my case, the system would appropriately switch to external monitor display and turn off the laptop monitor once gdm started up.  These settings are not reflected in POST, during boot-up, and I would sometimes use the Fn-key to try to toggle the VGA-out before hitting the login screen, which caused problems.

After restarting a few times and standardizing my method for controlling the two displays (by the software panel only), things stabilized and the monitor was properly detected and its concomitant resolution enabled.

But as to the specific nature of your problem, I'll reiterate that my problem did not occur immediately upon upgrading to 8.04, just weeks into its use.  As far as I know, the gnome Screen Resolution thing wasn't in 7.10.

Some thoughts:

A) Have you tried using the gnome display detection instead of the nvidia-settings?  Again, I don't have an nvidia card myself, so forgive me if there is something I don't know about here that is forcing you to use it.
B) Is there a reason you have a static xorg.conf for your LCD and are editing the second display's settings each time?  The file should accomodate for settings for multiple displays in a way that is non-invasive to your primary display's settings. But it seems like you have specific reasons for this.
C) Are you docking with the system already on, and then restarting gdm?  Have you tried setting the laptop in the dock and turning it on cleanly, and seeing if the external display is picked up?  If you're having to restart gdm, it sounds like maybe the second display is not being detected if it's not connected from the start.  As to why that functionality has changed since your upgrade...... :confused:

Sorry for the meager contribution, but hopefully it helps.

---

### Post by Unix_Slayer on 2008-06-05
> **655 said:**
> I noticed this change after installing some updates and rebooting; there were some upgrades to the main kernel, but... any correlation?


Happened to me also when I upgraded from kernel 2.6.24.17-generic to 2.6.24.18-generic.

---

### Post by 655 on 2008-06-05
Oh, ok.  Guess it was just a kernel upgrade, then.
Disregard my previous conjecture - must have been a false positive.

---

### Post by bastineman on 2008-06-05
nvidia-settings does NOT detect displays after "hot-dock" like it used to in 7.10 32bit

nvidia-settings DOES detect displays:
- after CTRL-ALT-BKSPC after docking
- warm & cold boot whilst docked


I keep a pretty generic xorg config as far as displays goes because I seem to be on and off the dock alot. If I am traveling and I reboot, I just need to laptop internal LCD. nvidia-settings did let me enable twin view for the dock-connected LCD WITHOUT a gdm restart. I would then disable twinview/ext LCD before hot undocking.

Having issues with the synaptics touchpad driver forgetting its settings(speed/scrolling) after docking/undocking. Restarting gdm fixes that too.

This is a clean 8.04 x64 install, not an upgrade - as in partitions were formatted.

Frustrating...

---

### Post by Unix_Slayer on 2008-06-06
You have to just re-install the NVidia driver, and it fixes what the kernel broke.

---

### Post by mindhaq on 2008-06-09
> **bastineman said:**
> I am having the same issue after upgrading from 7.10 32bit -> 8.04 x64 (clean install) on my Dell Latitude D830. I use the dock/port replicator with a 2408WFP connected via DVI.

I used to be able to dock and undock using nvidia-settings to detect the external LCD and enable it. Now, when I dock, detect displays does nothing. However, if I restart gdm/X CTRL-ALT-BKSPC and run nvidia-settings "detect displays" DOES work. The X restart is a bit annoying. I don't use nvidia-settings to save an xorg.conf file - I have a static xorg for just my laptop LCD and set my dock LCD every time.

Anyone?

I read on an official Dell Linux forum (sorry, can't find the link anymore) from a Dell employee that there was a bug with randr in the (then) current driver, and that it will be fixed in the next 173.x release. That is now available, at least on nvidia.com.

For now, I can only confirm the problem with a D830 plus port replicator. Using the normal resolution switcher, this never worked at all (which is caused by randr), with nvidia-settings only once per X start.

I hope that there will be an update via the official repos for Hardy soon (or is that something that will never happen, and I have to it differently)?

---

### Post by Unix_Slayer on 2008-06-09
> **mindhaq said:**
> I read on an official Dell Linux forum (sorry, can't find the link anymore) from a Dell employee that there was a bug with randr in the (then) current driver, and that it will be fixed in the next 173.x release. That is now available, at least on nvidia.com.

For now, I can only confirm the problem with a D830 plus port replicator. Using the normal resolution switcher, this never worked at all (which is caused by randr), with nvidia-settings only once per X start.

I hope that there will be an update via the official repos for Hardy soon (or is that something that will never happen, and I have to it differently)?


NVidia is a work in progress. They will fix it. At least the driver is not a beta, as in regards to randr..... there is probably a workaround. I haven't run into that problem as yet.

---

### Post by mindhaq on 2008-07-31
Small update on this matter ("detect display" and cloning in nvidia-settings after hot-docking):

With envy-ng driver version 173.14.05, after enabling clone, compiz performance got really bad. Switching desktops with the cube locked the screen in the rotating cube for at least 30 seconds before I could move the mouse again.

With 173.14.09, detect displays stopped working altogether.

Sad thing: the screen resolution widget from Gnome doesn't detect my internal display, let alone an external one. Dispite the new driver.
And trying to roll back to the "official" 169er driver just cost me 4 hours of xorg errors, installing, uninstalling, rebooting and what not. Result: my Laptop will now only boot with the latest envy driver, because of some version mismatch when I apt-get the "official" restricted driver.

As much as I dislike windows, and I'm not going back there - this is something that really works very well there.

---

### Post by bastineman on 2008-07-31
> **mindhaq said:**
> Small update on this matter ("detect display" and cloning in nvidia-settings after hot-docking):

With envy-ng driver version 173.14.05, after enabling clone, compiz performance got really bad. Switching desktops with the cube locked the screen in the rotating cube for at least 30 seconds before I could move the mouse again.

With 173.14.09, detect displays stopped working altogether.

Sad thing: the screen resolution widget from Gnome doesn't detect my internal display, let alone an external one. Dispite the new driver.
And trying to roll back to the "official" 169er driver just cost me 4 hours of xorg errors, installing, uninstalling, rebooting and what not. Result: my Laptop will now only boot with the latest envy driver, because of some version mismatch when I apt-get the "official" restricted driver.

As much as I dislike windows, and I'm not going back there - this is something that really works very well there.

I have experienced almost identical mindhaq. I am running 173.14.09 - tried to revert to 169.12 due to the compiz hangs while in twin-view. I AM able to "detect displays" in nvidia-settings after hot-docking if I restart gdm, but with the compiz hang issues I can only use one display at a time.

I can "recover" from a compiz hang while in twin-view by going to another terminal and back (CTRL-ALT-F5, CTRL-ALT-F7).

I will not go back to Windows either, but this HAS TO GET FIXED. nVidia needs to open up, or get their crap together.

---

### Post by mindhaq on 2008-08-01
bastineman, sad  to hear you got the same problems. But as they say, "A problem shared is a problem halved." :-({|=

I'd really like to roll back to the 169 driver and forget about envy. As stated above the newer driver version just made me problems without solving anything.

Just removing the packages in Synaptic didn't work, resulting in the dreaded "API mismatch: the NVIDIA kernel module has version 169.x, but this NVIDIA driver component has version 173.x" kind of error.

Will it work by **purging** instead of just *removing* all nvidia stuff? Maybe I'll try on the weekend, and post my results...

---

### Post by bastineman on 2008-08-14
Updated to 173.14.12(envy). No change or improvement. Still have compiz hangs in twinview and no "detect displays" functionality in nvidia-settings after hot docking - X restart required.

---

### Post by mindhaq on 2008-08-15
I used envy to uninstall the Nvidia driver, rebooted and installed nvidia-glx-new version 169.12

Now I'm back to some rather minor problems with TwinView enabled in xorg.conf, and not always having a second display connected:
 * Gnome login screen is only visible in half, as it seems to stretch across another (non-existing) screen.
 * Hot-enabling a second screen results in a graphically corrupt area exactly the size of the Gnome Toolbar.

But the following works again:
 * Detect displays in nvidia-settings
 * No performance problems with Compiz enabled in Dual-Screen.

I'll stay with this version for now.

---

### Post by robinwilson2 on 2008-08-30
I haven't seen anything that 'exactly' matches my situation - but I've read a couple of your notes that are 'close'. Unfortunately, I'm a relative 'noob' to this stuff (in reality, I'm a Unix guy from way back - but I'm new to all the driver stuff in Ubuntu). So I'm not sure I know how to apply what you've written to my "slightly different" situation.

Anyway, I have D830 laptop (notebook) with the NV Quadro 135M (on the board). I have a mini-dock port replicator that has a VGA and a DVI output on it. When I installed the 173.x NVidia-new-glx drivers, my machine will not recognize the DVI monitor (in fact, it shuts off the power to it (so that the normally 'green' power light goes into the 'power save' mode and turns orange on the monitor). I _think_ my laptop display comes on though, but with the machine in the dock, I've been too lazy to actually look. (I will note that I appear to have a desktop that goes off of 1 edge of the VGA attached monitor - which is why I think the laptop display is on.)

I'm not real proficient at hacking the xorg.conf file, so I'm not sure what I would change to make it recognize the DVI attached monitor. But the DVI port _works_ when I use the free nvidia driver (but then I can't use 'twinview' for the other - VGA - monitor).

This is essentially my last stumbling block to quitting Vista. Somebody please have mercy on me and help out - so I can become a Linux bigot too! ;-)

---

### Post by excalq on 2008-09-08
I just got a D830 as my new work computer, and I'm having the same problems. I've always been able to figure things out eventually, so I'll keep hacking on this problem. If I find a good solution, I'll give a shout out. 

Unfortunately this will probably involve messing around with my laptop and dock at my desk after my boss is gone in the evening, so it doesn't look like I'm wasting time at work trying to make Linux work... they are still skeptical of my use of Linux, but at least tolerate it. ;)

---

### Post by robinwilson2 on 2008-09-09
Thanks for the note. I haven't had much time to work on it for the last couple of days, so I have made zero progress so far. Ultimately, the issue seems to be one with the driver. (I've read reports that it "used to work", but I can never tell if that's related to the 2 outputs on the mini-dock, or just the dual monitor display.)

Anyway, let us know if you figure out an xorg.conf (and driver combination) that works.

---

### Post by excalq on 2008-09-09
**Ok, Got it to work, finally!!!**

First the specifics of the situation:
I'm running Ubuntu 8.04, Hardy Heron, and I have a Dell D830 laptop attached to a Dell Docking station. The docking station is attached to two Dell 2007WFP Flat Panel LCDs (both are 1680x1050 resolution). One LCD is attached DVI, the other to the VGA port on the dock.

The laptop is running an Nvidia GPU, and I'm running the binary driver version 169.12, which was automatically installed by Hardy Heron (using the "Hardware Drivers" manager).

I achieved a nearly working configuration using the nvidia-settings tool, then hand tweaked the xorg.conf file until I got it to work. Unfortunately I could not get Twinview to work, so I had to set up X with 3 screens (the builtin LCD, and the two monitors).

This allows dual monitors to work while docked, and allows the builtin LCD to be used with undocked. Both automatically use the correct resolution.

Use the configuration in the attached xorg.conf, and enjoy!

**Hot Docking and undocking is possible, but X MUST BE RESTARTED**. Also, you must switch to a TTY console (CTRL-ALT-Fn) before docking or undocking. After switching, then docking or undocking, go back to X (CTRL-ALT-F7) and hit CTRL-ALT-BACKSPACE to kill and restart X. Xorg should then restart. **If you stay in X, while docking or undocking, your system will lock up**, requiring a reboot. When you switch to a console or back to X, it is likely that your screen will stay blank until you return to X and restart it with CTRL-ALT-BACKSPACE. 


Here is the xorg configuration:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      2  "Screen1" LeftOf "Screen0"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

# External LCD Monitor
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

# External LCD Monitor
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

# Laptop's LCD
Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
EndSection

```

---

### Post by robinwilson2 on 2008-09-10
I'll be giving this a try in a little while. But first - did you have to install anything (other than the nvidia driver)? Like 'xinerama'? (I couldn't find it in the package manager previously...)

Also, I noted that you used the older nvidia driver (the newer one is 173.x I think...)... Did you find that the older one worked while the newer one did not?

Thanks again for the info - as soon as I try it out I'll let you know whether it worked for me.

---

### Post by excalq on 2008-09-10
I didn't actively install anything other than the NVidia driver. There are some xinerama libraries that were automatically installed by Hardy (I installed this system 4 days ago, and haven't had the chance to install or tweak much beyond the vanilla install on 8.04.1). 

That's odd that the Ubuntu driver tool installed an older version of the nvidia driver. I just let that utility handle the driver install, since that's typically worked well in the past, and is super simple to do. So, no, I haven't tried the newer driver.

---

### Post by robinwilson2 on 2008-09-11
OK, I got it working with both "external" displays... (Um, er,... "I" being 'excalq', not me...)

The only small 'gotcha' I seem to have is that I couldn't get Compiz to load (no big deal, but a little curious), so I can't get all the cool 'effects' on the desktop yet. I'll keep hacking on it.

BTW, I had to modify the xorg.conf from 'excalq' to fix a bug in it... Where it had a blank line in the "ServerFlags" section followed by a comment on the xinerama stuff - I removed the blank line and the comment - then it works.

---

