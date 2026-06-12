---
title: "Unable to change screen resolution"
date: 2010-08-02
forum: Hardware
---

### Post by BradleyAtkins on 2010-08-02
Hi I am trying to get my old laptop set up with Ubuntu 10.04 but find I cannot increase the resolution to anything like acceptable, highest is 600x800,

I have been trying to follow the instructions here: -

[http://wiki.ubuntuforums.org/showthread.php?t=958967&page=38](http://wiki.ubuntuforums.org/showthread.php?t=958967&page=38)

without success, I just end up with a blank screen and cannot get back from it without rebooting. 

There is a reference to switching to ttyl by pressing ctrl-alt-f1, this just turns my screen white and I cannot get back to the desktop even with ctrl-alt-f7.

Can anyone tell me how to go about changing the resolution?

Most of the posts refer to an Xorg.conf file and I don't have one

thanks

I have managed to discover the graphics card via lspci command: -

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Can anyone tell me how to discover the different resolutions this card supports? I know it can support higher than 800x600.

Thanks

---

### Post by dacman48 on 2010-08-02
have u installed the latest drivers for ur video card?

---

### Post by BradleyAtkins on 2010-08-02
Hi

Thanks for the prompt reply.:D

No, can you tell me how to identify which ones I need?

---

### Post by dacman48 on 2010-08-02
i cant, but your system can! go to system->admin->hardware drivers. if one shows up, click it and hit install

---

### Post by BradleyAtkins on 2010-08-02
Yes I tried that it says: -

"No proprietary drivers are in use on the system."

I have managed to discover the graphics card via lspci command: -

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Now I am trying to find out what resolutions it supports and how to find the right driver.

Cheers

---

### Post by BradleyAtkins on 2010-08-02
Looking in the package manager I have the latest version of xserver-xorg-video-sis installed. The blurb says it contains the drivers for all sis cards so I guess the answer is yes I have the latest drivers installed.

---

### Post by BradleyAtkins on 2010-08-02
In the end I found a post giving a sample xorg.conf file

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
```

Created the file and pasted this in and now I suddenly have a good resolution. 1280x768, why is beyond me as there seems to be no mention of this resolution in the file...

Anyhoo

Thanks for the replies

---

### Post by nailer542003 on 2010-09-03
Thank you for all that useful information.  I have the exact same problem.  I edited the xorg.conf file and it helped.  It upped the resolution from 800x600 to 832x624  and moved the display from the center with a black border to the upper left corner.  I checked for a more recsent driver.  lspci said my controller was rev 49.  The fujitsu web site has a ver 56 (for win 2000).  
 
I'm new to Ubuntu so I'm wondering if this driver might make a difference and how to install it.  Spacific steps would be helpful.  Thanks

---

