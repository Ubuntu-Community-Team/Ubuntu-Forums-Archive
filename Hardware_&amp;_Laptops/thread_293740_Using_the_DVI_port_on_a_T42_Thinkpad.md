---
title: "Using the DVI port on a T42 Thinkpad"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by Johnny5Net on 2006-11-05
Hi, 

I run Dapper on a T42 Thinkpad with a port replicator which has a VGA and DVI port. Currently I use the VGA port and connect it to a 19" LCD screen (1280x1024) which has a DVI input, but I want to use the DVI port. Also, I need to be able to switch resolutions between the internal LCD screen (1024x1768 ) to the resolution of the external LCD screen (1280x1024) without restarting X (today i use xrandr to do the switch).

My current relevant xorg.conf section:
[INDENT]Section "Device"
        Identifier      "ATI"
        Driver          "radeon"
        # accelration
#       Option          "AGPFastWrite" "1"
        Option          "AGPMode" "4"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        # enable PowerPlay features
        Option          "DynamicClocks" "on"
        # use bios hot keys on thinkpad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
        # enable radeon specific xinerama
#       Option          "MonitorLayout" "LVDS, TMDS"
        Option          "MergedFB" "true"
        Option          "CRT2Position" "Clone"
        Option          "CRT2Hsync" "50-75"
        Option          "CRT2VRefresh" "30-82"
        Option          "MetaModes" "1024x768-1280x1024 1024x768"
        Option          "MergedNonRectangular" "true"
        BusID           "PCI:1:0:0"
EndSection[/INDENT]

I have tried to change or mask everything I could think about and I have searched the forums and found nothing to help me about it, only one message was on this subject and it didn't helped. Also I've googled on it but I couldn't find anything to help me, I did find a [guide]("http://www.thinkwiki.org/wiki/Installing_Ubuntu/Breezy_on_a_ThinkPad_T42") to install breazy on a T42 but there is nothing about the DVI connection except that it worked for him.
One more thing, in the bios there is a display setting which is set to LCD+VGA+DVI, meaning all possible outputs.

How can I make the DVI port work?

Thanks.

---

### Post by twocargar on 2007-08-26
I'm running Feisty on my T42 and also have had no luck with the DVI on my port replicator.  Have you had any luck with this?

Thanks,

TCG

---

