---
title: "Dell XPS m140 stuck at 1024x768"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by stbrenner on 2007-02-27
Hi,

I installed Edgy and love it except for my screen resolution.  Despite repeated attempts to install 915?resolution and select the mode, modify my xorg.conf file with the driver for i810 and restart the x server, I'm still stuck at 1024x768.  This is driving me crazy.

---

### Post by m3741 on 2007-02-28
Can you post your /etc/X11/xorg.conf?

Also, what video card do you have and do you know what your display's native resolution is? Or what resolution you want to run at anyways?

And one last question, what arguments are you passing to 915resoution?

---

### Post by idzeeboo on 2007-06-18
I have the exact same problem with my Dell XPS M140.  I want to run 1280x800 and the xorg file already has that setting (24 bit) but it still displays 1024x768!!  I am assuming it is because of the "Generic Monitor" setting.  What can I change the monitor driver to in order to get more choices for resolution?

Here is a copy of the relative portion of my xorg.conf file:
--------------------------------------------------------------------------------
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
-----------------------------------------------------------------------

Thanks for any help you can give!

---

