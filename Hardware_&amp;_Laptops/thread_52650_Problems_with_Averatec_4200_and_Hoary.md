---
title: "Problems with Averatec 4200 and Hoary"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by djester on 2005-07-28
Okay, so this laptop has been a beast.  
Here are my most pressing problems.  

Issue 1:

I've got the 1280x800 res working, but only with the vesa driver.  The Laptop uses the new Intel 900 GMA graphics chip and that should work at least with the i810 driver, but when I change my xorg.conf to say:

Section "Device"
        Identifier      "Generic Graphics Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        96000
EndSection

I get a blank screen.  Then I figured I'd play with my Monitor config to read:

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       31.5-80
        VertRefresh     36.5-75
        Option          "DPMS"
        Modeline        "1280x800_60.00" 83.46 1280 1344 1480 1680 800 801 804 828
        -HSync +Vsync
EndSection

If I comment out the HorizSync and The VertRefresh I get a screen that goes bright white from black with all sorts of weird colors. I know there's just something that I'm missing, but I don't know what.  

Issue 2:

I managed to install Hoary by turning off acpi.  So after I got the os installed I decided to try and get acpi enabled.  Found that it freezes during boot when loading powernowd so I ran rcconf and disabled powernowd and then reenabled acpi.  So it works kind of.  What I need now is to get the SpeedStep working, but I have now idea how to do that.  I believe that I need the powernowd to run inorder to use it.  (The laptop has a Pentium M 1600 Mhz. btw)

I don't really know what kind of data I should post to help you guys the most so just let me know and I will post it.  I'm not a newb, but I'm very far from expert.  I'm just stuck with some humdingers, and I apreicate any kind of help that anyome can give.

---

