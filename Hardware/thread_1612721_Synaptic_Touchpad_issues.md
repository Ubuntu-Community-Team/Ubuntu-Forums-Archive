---
title: "Synaptic Touchpad issues"
date: 2010-11-03
forum: Hardware
---

### Post by Farving on 2010-11-03
Hi,

I have installed Jolicloud on my Notebook (as far as I know, it's build upon Ubuntu, explaining why I'm asking here).

My problem is that I can't get the touchpad to work, or well I have it up working twice out of tens and tens of reboots, making it wortless.. 

When it's working I can open gsynaptics and manage settings for my touchpad, when it's not working I get this error:

[I]GSynaptics couldn't initialize
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics[/I]

My xorg.conf file contains this section:
[I]Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"
EndSection[/I]
Which should enable SHMconfig..

Anyone able to help me?
I've checked that xorg synaptics drivers is installed and so is gsynaptics.. 

And what bothers me the most is that if I do a boot and it works, and then I just does a reboot, then it's certain that it won't work, even though I haven't changed anything..

Greets

---

