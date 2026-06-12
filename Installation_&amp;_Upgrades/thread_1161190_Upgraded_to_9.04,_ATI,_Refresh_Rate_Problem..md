---
title: "Upgraded to 9.04, ATI, Refresh Rate Problem."
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by starnich on 2009-05-16
Hello All,
I recently upgraded Ubuntu to 9.04, had it all working ok before upgrading, now having refresh rate problems.

Have ATI Radeon HD3850 AGP card, downloaded and installed drivers from AMD, new for April, not sure what version, installed all ok etc.

I had previously edited the xorg.conf file (before upgrading) to get a higher refresh rate, ie 75hz instead of 60 and worked ok, since upgrading I havn't been able to do this as easily.

I have tried ading the horizontal sync and vert refresh 'bits' and various mode lines with @ sign and an underscore as fould in help posts elsewhere, still didn't work.

Now have blinding headache looking at screen at 60hz!

I am a noob to Ubuntu, but not beyond a bit of editing of files etc.

Here is my xorg.conf file:

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        HorizSync       30.0 - 80.0
        VertRefresh     50.0 - 120.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
I have tried putting in the 'mode' lines under display ie: (Mode 1280x1024@75 or 1280x1024_75), this didn't work either way, I was able to get the higher refresh before upgrading and yes my monitor is capable of 75 hz, and the vert refresh and horz sync figures are right, just at a bit of a loss now.
Cannot select 75 hz in ati catalyst control ot the display option under 'system', any help much appreciated, off to find ibufren, thanks.

---

### Post by starnich on 2009-05-17
?

---

### Post by HavocXphere on 2009-05-17
The modeline thing needs to go into 2 places in the xorg.

Like so:
[http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401](http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401)

(With your own settings of course).

---

### Post by starnich on 2009-05-17
Thanks Havoc,

Have tried that, the xorg.conf now looks like this:

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier      "HP A4033A"
        Option          "VendorName" "HP"
        Option          "ModelName" "A4033A"
        HorizSync       30.0-80.0
        VertRefresh     50.0-120.0
        Modeline        "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "HP A4033A"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1280x1024_75"
        EndSubSection
EndSection

Does anybody think its something to do with the ATI driver???

---

### Post by starnich on 2009-05-17
Does anybody know how to fix this problem or should I be talking to ATI/AMD about this?

Have been working on this for 4 days now and getting very frustrated.

This is a simple matter of a refresh rate on a monitor!!!!!!

Does anybody know what has been changed between versions to prevent a simple line edit in xorg.conf being accepted??????

Anybody with some technical knowledge please give us a hand, not feeling very happy with Ubuntu anymore arrrrrrrrrrrgrgrgrgrggrrg

---

### Post by HavocXphere on 2009-05-17
> **starnich said:**
> Thanks Havoc,

Have tried that, the xorg.conf now looks like this:

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier      "HP A4033A"
        Option          "VendorName" "HP"
        Option          "ModelName" "A4033A"
        HorizSync       30.0-80.0
        VertRefresh     50.0-120.0
        Modeline        **"1280x1024@75"** 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "HP A4033A"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   **"1280x1024_75"**
        EndSubSection
EndSection

Does anybody think its something to do with the ATI driver???
Those two kinda need to be exactly the same. The bottom one is a reference to the top one.

I think that sometimes the ati driver doesn't use the xorg.conf settings and I think this is meant to force it:
aticonfig --initial --input=/etc/X11/xorg.conf
Not too sure about this step though...so do some research first & make a backup of xorg.conf first.

---

### Post by starnich on 2009-05-17
Thanks for that, have corrected the mistake, still no joy,
also tried the command line you suggested, got:
Bad file descriptor

---

### Post by Dakiraun on 2009-05-29
The problem is in the drivers.  The AGP 8350 was never officially supported by AMD/ATI as they had not intended for that GPU family to be made into AGP cards.  The various manufacturers that make ATI cards were the ones that decided to make an AGP version anyway, and in doing so, it requires special "hotfix" drivers to work correctly in Windows.  AMD does put out these drivers, but they are unofficial, unsupported and only available for Windows so far. :(

As far as I know, no one has written anything that gets these cards to work correctly in Linux or BSD.  Sucks because my main system used to be Ubuntu until I got that card.

---

### Post by starnich on 2009-06-02
Very sorry to hear that.
I got this from ATI/AMD:

Dear Customer,

Your service request : SR #{ticketno:[8200201665]} has been reviewed and updated.

Response and Service Request History:

Although we have driver for Linux posted on the ATI website, we do not troubleshoot driver or multimedia issues in Linux directly. We work closely with the Linux community to provide support options. On our website we do have link to several Linux support sites that may help you. I have included the link below to this website. All Linux help is self help online.

Our web site offers several links to Linux support web sites that may help you.

You may click on the link below and go to its website to find information that might be helpful to your case. Our Engineers are informal contributors.
[http://wiki.cchtml.com/index.php/Main_Page\]("https://rimon.safe-mail.net/cgi-bin/Safe-mail.net/display?mime/url.html&http://wiki.cchtml.com/index.php/Main_Page@5c")
This is also a very good article from a third party
[http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000140000000000000000]("https://rimon.safe-mail.net/cgi-bin/Safe-mail.net/display?mime/url.html&http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html@23SECTION000140000000000000000")

If you are experiencing problems with our latest driver release, or if you have suggestions about how to make our drivers better, please take the time to submit your feedback.

[http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36]("https://rimon.safe-mail.net/cgi-bin/Safe-mail.net/display?mime/url.html&http://www.amdsurveys.com/se.ashx@3fs@3d5A1E27D23CFE9B36")


In order to update this service request, please respond, leaving the service request reference intact.

Best regards,

AMD Global Customer Care

useless

---

### Post by Dakiraun on 2009-06-11
Yeah - I'm not surprised.  They read about as far as "Linux driver" in your request and posted an automatic response.  To be honest, I was surprised they even made the unofficial hotfix drivers for XP.  Oh well.

---

