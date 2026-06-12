---
title: "Wacom Intous not working right"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Aithnea on 2007-05-11
Hello all,

I've got a wacom intous that I use for doing my artwork on my laptop.  It worked great in Dapper but since I've upgraded to Fiesty it's not working right.  My stylist has to be touching my tablet to be able to get it to move across the screen (something that I didn't have to do in Dapper) and when I got into both the GIMP and Inkscape to configure the device they tell me that I don't have one.  I've gone into Synamptic to check that I do have the drivers installed and it tells me that I do.  I have even tried uninstalling them and reinstalling them and still have the same problem.  I checked the boards but couldn't find a post with someone having the same problem.

---

### Post by twisted_steel on 2007-05-11
Did you check the devices in your /etc/X11/xorg.conf?  I just installed my Graphire 4 tablet under feisty and couldn't get it to work until I changed the lines in there.  It was pointing to "/dev/wacom" for the stylus, eraser, and cursor identifiers instead of "/dev/input/wacom"  Here's an example of how it should look:

```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "eraser"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "cursor"
        #Option         "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
```Just save the file, log out, and hit CTRL+ALT+Backspace to restart X.

---

### Post by Aithnea on 2007-05-12
I did try that and in Dapper that had worked but not in Fiesty.  I even tried changing it to event2 and then event3 when it didn't work.

---

