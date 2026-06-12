---
title: "Toolbars are constantly outside of the border of TV when using it as a monitor."
date: 2011-07-17
forum: Hardware
---

### Post by crusel832 on 2011-07-17
I've installed 11.04 on an ASROCK Ion 330 (planning on using it as an HTPC with XBMC). I have it hooked up to an Insignia 37" 1080p TV, but no matter what resolution I choose the screen borders always appear just above the top and bottom of the screen, cutting off the toolbars. Even on the lowest possible resolutions. I've tried right clicking on the toolbars and increasing their pixel size, but this makes them look very glitchy and unappealing and still doesn't really fit it all that well on the screen. I'm worried this is an issue with the TV specifically that can't be fixed, but I had it running Windows 7 without any screen border issues.

Hopefully I put this in the right spot, I also tried searching for this issue but wasn't sure what to search for since it's kind of an unusual issue. Any help would be greatly appreciated!

---

### Post by movieman on 2011-07-17
Sadly TV manufacturers are evil and when you give them a perfect 1920x1080 digital signal they'll then scale it up and crop off the edges before displaying it on the 1920x1080 display.

So either you need to find an option on the TV to not screw up the display, or you need to find a way to get the video driver to render to a smaller area than the TV claims to display. My guess is that the Windows driver is probably doing that automatically.

Oddly I see the opposite result, where my Ion MythTV frontend seems to work fine but my Windows laptop has the screen edges cropped off.

---

### Post by crusel832 on 2011-07-17
Ah, yes, that's what I was afraid of. The TV isn't all that nice and I see no options in the settings menu to adjust the borders. When using Windows 7 I couldn't use the actual 1080p resolution because of the same issue, I had to use some wonky resolution that was "close enough" to the edges to make me happy, and I'm afraid I have no idea how to mess drivers in Ubuntu. It doesn't make me too happy but this might be the end of my hopeful HTPC :(

Edit: I see under the System menu the option for "Additional Drivers" but I haven't messed with NDISwrapper to get the USB wireless adapter working yet, and I'm an Ubuntu n00b and don't want to go through the hassle only for it to all be in vain

---

