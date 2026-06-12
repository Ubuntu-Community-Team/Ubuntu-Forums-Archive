---
title: "gateway mx3215"
date: 2009-12-18
forum: Hardware
---

### Post by bbygngrndth on 2009-12-18
Decided to give an overview of the problems/solutions with the Gateway Mx3215 laptop with Ubuntu 9.10 upon a new install.  Probably no one using an oldie like this with 9.10 but oh well.
  - 1. wireless internet
  - 2. sound
  - 3. resolution

!. First off, all you need to do to get the wireless working is install with the laptop plugged in to a hardwired connection.  When you are finished, open up System>Administration>hardware drivers. Get the Broadcom driver. waaaaaaay easier than older ubuntu versions.  Once its installed, unplug ethernet cable and reboot. should work, but if not, go to System>Administration>Network Connections and create the connection. If you've installed already, you can probably set up a wired connection  and go to synaptic package manager to find the driver.... if not well, it only takes like 30 minutes to re-install anyway.

2. This was actually very counterintuitive, yet also incredibly easy in older versions. had to play around for a few with 9.10.  right-click on the speaker icon (if your resolution is still off, then right click on the top bar, select the preferences, unexpand the bar) go to preferences for the sound. at the bottom there is a drop down, select
                 Analog Stereo Output + Analog Stereo Input
Then select the Output tab. Another drop down at the bottom, select,
                 Analog Output / No Amplifier
I cant remember if a restart is needed, but i dont think so.

3. This one sucks.  Go to Accessories>gedit Text Editor
Type all of this:
# xorg.conf (X.Org X Window System server configuration file)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
            Identifier    "openchrome"
EndSection

Section "Monitor"
            Identifier    "Configured Monitor"
EndSection

Section "Screen"
            Identifier    "Default Screen"
            Monitor        "Configured Monitor"
            Device        "Configured Video Device"
Subsection "Display"
        Modes      "1280x768"
         EndSubSection

EndSection


copy and paste that as your best bet. Anything with a (#) in front doesnt do anything, so leave whatever notes for yourself that way.  name and save it as xorg.conf by selecting file sytem and the directory:
                etc/X11
reboot and it should be fine.

Good Luck!
If I overlooked anything sorry. I'll keep an eye and help anyone that needs it.

---

### Post by t3chnique on 2010-05-20
thank you very much! I've been having problem getting the correct resolution to work on this particular laptop.:popcorn:

---

### Post by porjos on 2010-06-10
Thanks a lot! This really helped a friend of mine out!!! The techniques you provided we're intuitive and streamlined.

---

