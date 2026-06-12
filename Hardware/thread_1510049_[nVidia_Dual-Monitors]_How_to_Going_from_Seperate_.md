---
title: "[nVidia Dual-Monitors] How to: Going from Seperate X Windows to TwinView"
date: 2010-06-15
forum: Hardware
---

### Post by Rapture2k4 on 2010-06-15
Greetings!

I've had a heck of a time figuring this out on my own, but now that I did, I thought I'd post it.

So, you've installed 10.04 Lucid Lynx and tried to setup dual monitors by using the "Seperate X Windows" option in the NVIDIA X Server Settings. Now you want a proper dual-monitor configuration. I'm not sure if this is a bug or not, but changing the settings to TwinView without doing the following procedure gives a "Failed to set metamode" error. In any event, the juicy bits:

Step 1: Open a terminal and do a 'sudo nvidia-xconfig' to reset your nvidia settings. You can find the terminal app in the Applications->Accessories menu.

Step 2: Open the s app via terminal by typing 'sudo nvidia-settings'

Step 3: Click on the "X Server Display Configuration" and then select the secondary monitor.

Step 4: Click on "Configure" and at the pop-up window select "Disabled" and click Ok. Now click Quit.

Step 5: Type 'sudo /etc/init.d/gdm restart' to restart X-Server. Login to your account again.

Step 6: Do steps 2 and 3 again.

Step 7: Click on "Configure" and choose TwinView this time. Adjust your resolution for the second monitor if need be. Click on the primary monitor and check the box labeled "Make this the primary display for the X screen". Click "Save to X Configuration File" and click "Ok". Now quit the NVIDIA X Server Settings app and restart X-Server again (step 5). BAM! Dual monitors!

I hope someone finds this helpful.

-Rapture

If need be, I'll redo this with pretty pictureseses.

---

### Post by waffleguy4 on 2011-05-01
Running Ubuntu 11.04 and am unable to use dual monitors with the Nvidia X Server and Unity. I tried your steps several times with no success. Any suggestions? Thanks!

---

