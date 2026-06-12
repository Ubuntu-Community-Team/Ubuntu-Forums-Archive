---
title: "Intel945GM 1440x900 Resolution Help"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by tempest130 on 2007-05-07
Hi everybody,

I have a brand new Dell Inspiron 640m 14.1 screen with an Intel945GM video card.  I've just installed Ubuntu 7.04 and I want the resolution to be 1440 x 900.  I've read that you need the application 915Resoulution to achieve this.  However I have followed serveral instructions and I can only get as high as 1280x800.  I don't know if this is a limitation of the Intel 945GM chip.  I've got a clean install of Ubuntu 7.04 so I don't know if anyone has tried this with 7.04.  I hope that someone can point me in the right direction.  Thanks.

Sean

---

### Post by jslag on 2007-05-07
When you run 915resolution -l, does your desired resolution show up?
Do you have a modeline for your desired resolution in /etc/X11/xorg.conf?

To the best of my knowledge, those are two of the key elements in the puzzle.

---

### Post by tempest130 on 2007-05-07
I've tried to set the "modline" by following some instructions I saw online and it still didn't work.  I"m not sure really how to start.  Is there someone who has a dell 640m and have got 1440 x 900 with ubuntu 7.04? Anyone has any instructions?

Sean

---

### Post by Hairy_Palms on 2007-05-07
try this, download [http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz](http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz)
extract it, 
then run ./configure, 
then
make
then sudo make read-edid, it should generate a perfect monitor section for you that can be used

it should ggive you a section like this

> Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "TS902W"
        VendorName "DDL"
        ModelName "TS902W"
        # Block type: 2:0 3:fd
        HorizSync 30-80
        VertRefresh 56-76
        # Max dot clock (video bandwidth) 140 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:no  Standby:no

        Mode    "1440x900"      # vfreq 59.887Hz, hfreq 55.935kHz
                DotClock        106.500000
                HTimings        1440 1520 1672 1904
                VTimings        900 903 909 934
                Flags   "+HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
EndSection

notice the htimings and vtimings are 1440 and 900

then put that in your /etc/X11/xorg.conf to replace your current monitor section.

---

### Post by jslag on 2007-05-07
> **Hairy_Palms said:**
> try this, download [http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz](http://john.fremlin.de/programs/linux/read-edid/read-edid-1.4.1.tar.gz)
extract it, 
then run ./configure, 
then
make
then sudo make read-edid, it should generate a perfect monitor section for you that can be used

Or you could just do `sudo aptitude install read-edid` then run `sudo get-edid | parse-edid`.

Unfortunately, EDID is apparently not always useful for widescreens and / or LCDs - I gave this a try for my own setup & got a completely unusable mode.

---

### Post by tempest130 on 2007-05-08
I got this after I ran sudo  make read-edid.  Prior to running the command I installed a fresh copy of 7.04 then I ran some updates, then I installed 915resoulution, which automatically put my resolution at 1280x800 after I CTRL-ALT-BACKSPACE. I have not changed any config files in xorg.conf or the default 915 config file.  When I go to SYSTEM - PREFERENCES-RESOLUTION I see the 1280x800 option.  However when I've installed the package xserver-xorg-video-intel, I get a resolution option for 1280 x 1280.  


Section "Monitor"
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        Identifier "AUO:4412"
        VendorName "AUO"
        ModelName "AUO:4412"
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1280x800"      # vfreq 60.002Hz, hfreq 49.382kHz
                DotClock        71.110000
                HTimings        1280 1328 1360 1440
                VTimings        800 803 809 823
                Flags   "-HSync" "-VSync"
        EndMode
        Mode    "1280x800"      # vfreq 50.003Hz, hfreq 41.153kHz
                DotClock        59.260000
                HTimings        1280 1328 1360 1440
                VTimings        800 803 809 823
        EndMode
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
EndSection

---

### Post by tempest130 on 2007-05-08
Hi everybody,

I've figured out the solution.  I've looked at the specs on this laptop and discovered that the screen is a WXGA screen (max resolution. 1280 X 800).  I thought the screen was WXGA+ (max resoultion 1440 x 900).  

Thank you to all who has responded to my post.  Sorry for the misinformation.

Sean

---

### Post by windowskilla on 2008-02-08
Ive been having problems with mine for awhile, however I finally fixed it, I ran this, then put the configuration into xorg.conf

here is the problem, the display became completely unusable, 

so I did a 

"sudo dpkg -reconfigure -phigh xserver-xorg"

and guess what it freaking found the resolution I had tried so desperately to get working.

previously running at 1280x800x60

now running at 1440x900x60x32bpp (native resolution)

ps 915resolution is installed and loaded but doesn't work

Thing is with this, after rebooting it switched to 640x480, so I went in and edited xorg.conf manually saved and reboot and its stayed at this resolution ever since.

If anyone needs clarification on how or whats installed feel free to ask.

---

