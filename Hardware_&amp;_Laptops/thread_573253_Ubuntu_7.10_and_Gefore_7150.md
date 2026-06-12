---
title: "Ubuntu 7.10 and Gefore 7150"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by luxuguy on 2007-10-11
After hours struggling install Gusty in my Compaq V6500z, which comes w/ a Geforce 7150, I can get the driver to install. HOWEVER, it's acting very WEIRD:

When you startup the laptop, the Login screen display correct resolution. After that, the resolution drop down to 800x600. I can manually change:
1/ Screen and Resolution back to 1280x800
AND 2/ nvidia-settings back to 1280x800 + save to xorg.conf

BUT everytime I restart the machine, this problem comes back. I don't understand why I get the correct resolution first time, then once it get pass the login screen, the res. drops ???

Can anyone help me with this ? I don't want to manually chagne the resolution every time I use Ubuntu.

THANKS,

Luxuguy:popcorn:

---

### Post by cubeist on 2007-10-11
When you change it in nvidia-settings perhaps it is not actually saving it to the xorg file... try "sudo nvidia-settings"

if that doesn't work, try manually editing the xorg.conf file ... don't forget to backup a copy first (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig) this is VERY important because it allows you to boot into recovery mode and change it back if it doesn't work

here is what my xorg.conf file looks like for the screen section, hope this helps
----
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51 [Geforce 6150 Go]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1440x900"
        EndSubSection
EndSection
------------

on a side note, I don't know why I have depth modes for 1 or 15... that makes no sense because depth is always a function of base 2...

---

### Post by luxuguy on 2007-10-11
Hi,
Can you post the "Monitor" section in you xorg file ?

I have a 1280x800 in the Screen, but the monior does not look right. I don't have a "Generic.." one. Instead, I have a Seiko watever and I couldn't get Generic driver to work. I'm wonering what's going on with the LCD panel I have.

---

### Post by cubeist on 2007-10-11
sure,
-------
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-72
        Vertrefresh     43-60
EndSection
------------------

---

### Post by luxuguy on 2007-10-11
It is still not working, which is really weird.

Will there be much difference b/w the released version and the beta+upgrade packages ? Should I wait for the release version ???

---

### Post by cubeist on 2007-10-11
can you post your xorg.conf file and the output of lspci for me and I will see if I can get it working...

---

### Post by luxuguy on 2007-10-12
Thanks cubeist. I removed Ubuntu alreeady. I'll probably come back to it once the final release comes out. Thanks for your help.

---

### Post by luxuguy on 2007-10-12
and other users too ...

---

### Post by nihalz on 2008-03-25
> **luxuguy said:**
> After hours struggling install Gusty in my Compaq V6500z, which comes w/ a Geforce 7150, I can get the driver to install. HOWEVER, it's acting very WEIRD:

When you startup the laptop, the Login screen display correct resolution. After that, the resolution drop down to 800x600. I can manually change:
1/ Screen and Resolution back to 1280x800
AND 2/ nvidia-settings back to 1280x800 + save to xorg.conf

BUT everytime I restart the machine, this problem comes back. I don't understand why I get the correct resolution first time, then once it get pass the login screen, the res. drops ???

Can anyone help me with this ? I don't want to manually chagne the resolution every time I use Ubuntu.

THANKS,

Luxuguy:popcorn:

sorry to bump an old thread...but luxuguy, how did you install the drivers for 7150?
i always get the "x server cant be started error"
any info will be appreciated
thanks

---

