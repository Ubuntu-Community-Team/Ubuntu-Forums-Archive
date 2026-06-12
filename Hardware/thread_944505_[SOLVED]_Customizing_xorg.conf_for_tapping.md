---
title: "[SOLVED] Customizing xorg.conf for tapping"
date: 2008-10-11
forum: Hardware
---

### Post by UberWookieks on 2008-10-11
Hi all. I'm having a spot of trouble configuring the Synamptics touchpad in my Macbook and I was wondering if anyone could help. Basically, I'd like to disable touch-to-left-click while keeping the double-tap-to-middle-click and triple-tap-to-right-click.

I've Googled it a bit, but I can only seem to find solutions that entirely disable tap-to-click, while I'd like to preserve it for the alternative mouse buttons. Here's my touchpad section for xorg.conf:

[PHP]
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option "TapButton" "0"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "VertTwoFingerScroll"   "1"
        Option          "TwoFingerButton1"      "3"
EndSection

[/PHP]

---

### Post by UberWookieks on 2008-10-12
It appears my Google-fu was weak and I found [The Fine Manual]("http://web.telia.com/~u89404340/touchpad/"). I've seen similar questions with the touchpad, so I'll post what I found here. My Synaptics section in xorg.conf is now:
        Option          "MaxTapMove"            "0"
[PHP]Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option "TapButton" "0"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "VertTwoFingerScroll"   "1"
        Option          "TwoFingerButton1"      "3"
**        Option          "MaxTapMove"            "0"**
EndSection
[/PHP]

I added the line in bold [EDIT: The last line before EndSection. I'm not good at this markup.]. It disables "single finger tap for left click" while leaving two- and three-finger clicking functional for suckers like me with Macs that want to use middle- and right-click multitouch functions.

Also, this is my first post in Ubuntu forums. I'm giving this distro a shot after using Gentoo for years. I'd like to say it's very well done and say thanks to Mr. Shuttleworth, Canonical, the coders, and all the people that make this happen. 

Also, mods, can you move this to a more appropriate section than mythbuntu? I had some epic fail when I first made this post.

---

