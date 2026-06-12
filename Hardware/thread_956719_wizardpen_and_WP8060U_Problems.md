---
title: "wizardpen and WP8060U Problems"
date: 2008-10-23
forum: Hardware
---

### Post by fullerjas on 2008-10-23
I'm having issues setting up my WP8060U USB Tablet.  I've gone through the how-to ( [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) ) a number of times.  The tablet seems to be recognized, in that I can use the buttons and the double-tap feature, however, I can't use it to move the pointer---it just stays still all the time.

When I run  sudo /etc/init.d/rc.local start , it says Tablet present! - Tablet-driver enabled. 

However, when I run xinput list , the tablet does not show up in the list of running inputs (but, as a check, I removed the Synaptic Touchpad in xorg.conf, and it disappeared from the list like it should).

Here are the pertinent sections in xorg.conf:

Section "InputDevice"
        Identifier      "Tablet"
        Option  "Name"  "UC-LOGIC Tablet WP8060U"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "616"
        Option          "TopY"          "30"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
EndSection

--------------

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"

        Inputdevice     "Synaptics Touchpad"
        Inputdevice     "Tablet"        "SendCoreEvents"

EndSection

------------------

Also, when running the command cat /var/log/Xorg.0.log | grep "wizardpen" , I get the following errors:

(II) LoadModule: "wizardpen"
(WW) Warning, couldn't open module wizardpen
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (module does not exist, 0)
(EE) No Input driver matching `wizardpen'

------------------

If anyone has a suggestion, I'd really appreciate it.
Thanks.

---

### Post by DoctorMO on 2009-01-27
Are you still having problems with this?

---

