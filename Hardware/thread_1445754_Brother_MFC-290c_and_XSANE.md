---
title: "Brother MFC-290c and XSANE"
date: 2010-04-03
forum: Hardware
---

### Post by mothdragon on 2010-04-03
Hi, this is my very first post here, so I hope it's in the right place... 

I have wanted for a very long time to have a devoted linux box and now I do!

I'm running Ubuntu 9.04 at the moment, but eagerly awaiting 10.04. In the mean time though I needed to get all of my devices running. I have just spent the last several hours trying to get my MFC-290c All-in-one Scanner portion to work properly from my actual user account rather than the root.

For reasons beyond the scope of this post, XSANE typically runs from the root, instead of the user account. For many devices this has been resolved in many locations on the net, but I wasn't able to find a direct fix for my device... At least not right away. In the end I was able to find the information tucked away on the Brother website, on a page that literally displayed for about 3 seconds, before being replaced with a relatively useless site... I was able however to find the solution by grabbing it from that "only open for 3 seconds" page...

For Ubuntu 9.04 the steps are as follows:
    1. Open "/lib/udev/rules.d/50-udev-default.rules" file.
    2. Edit "0664" to "0666" in "libusb device nodes" section.

    Before the edit---------------------------------
       # libusb device nodes
       SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0664"

     After the edit----------------------------------
       # libusb device nodes
       SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0666"

     3. Restart the OS.

For Ubuntu 9.10 the steps are as follows:
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
    The lines to be added---------------------------
    
       # Brother scanners
       ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

    3. Restart the OS.

Now as I do not have 9.10 running on my system I cannot at this time verify that this will work for 9.10, however I assume it will, because the solution for 9.04 from the same source does in fact work :)

Cheers!

---

