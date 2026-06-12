---
title: "Command to turn on/off a second monitor"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by didli on 2007-01-19
Hi everyone !
As I have two different resolutions for each display on my computer, HP laptop (DFP 1440x900) with Home Cinema Projector (CRT 960x540) on a Geforce GO 7600, I made a two separate screens configuration, with the projector "rightof" my LCD laptop.
The problem is : some wine games "see" my second display, so if I put my cursor near the right border of the first display which has the game running, the cursor leave the game to go to the second display (what is quite logical, I think).
So I'm currently searching for a **linux command** that could **turn on/off** my **2nd display** before I load my games. 
Is it possible ?
Any idea ?

---

### Post by didli on 2007-01-20
Hi !
I think I've found another easiest solution, [_[here]_]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=175&p_created=1101836633&p_sid=qzEO*9si&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NSZwX3Byb2RzPTAmcF9jYXRzPTAmcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD10d2ludmlldw**&p_li=&p_topview=1"), but I need you Nvidia power users to help me configure my xorg.conf. It seems I could tell a specific device to turn off at a request resolution :
> If you want a display device to not be active for a certain
MetaMode, you can use the mode name "NULL", or simply omit the
mode name entirely:
  "1600x1200, NULL; NULL, 1024x768"
or
  "1600x1200; , 1024x768"
But I don't quite understand how I should put it in my xorg in order to have my second screen off.
Here's concerned part of my xorg :
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1440x900_60 +0+0; DFP: 1440x900 +0+0; DFP: 1280x800 +0+0; DFP: 1024x768 +0+0; DFP: 1024x640 +0+0"
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1280x800" "1024x768" "1024x640"
    EndSubSection    
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x800" "1024x768" "1024x640"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT: 832x624_75 +0+0"
        SubSection     "Display"
        Depth       16
        Modes      "832x624"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "832x624" 
    EndSubSection
EndSection
```
Could you help me for this ?
Thanks !

---

### Post by galileon on 2007-01-29
i'm interested in this too, my tablet monitor comes back on after turning off...

---

