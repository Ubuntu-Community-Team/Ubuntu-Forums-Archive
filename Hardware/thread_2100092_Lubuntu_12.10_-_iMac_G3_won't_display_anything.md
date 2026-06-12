---
title: "Lubuntu 12.10 - iMac G3 won't display anything"
date: 2012-12-31
forum: Hardware
---

### Post by dtourond on 2012-12-31
I have an iMac G3 (indigo) that I installed Lubuntu 12.10 on via the alternate iso. The installation went fine but now I can't boot into the OS properly. Every time I try the screen goes blank after the blue splash screen disappears.

Here's a video I recorded of my experience. In this video it shows you the boot process and what happens after the splash screen disappears.

[http://www.youtube.com/watch?v=puMbXeLNuTU](http://www.youtube.com/watch?v=puMbXeLNuTU)

Now.. Here's the twist: The iMac comes with a VGA port in the back and I thought to myself "Why not try running an external monitor and see if that works". After plugging it in and turning it on again, I was able to login and run Lubuntu off of my external monitor, but not from the Imac's built-in display..

I tried to change the resolution settings so that it would match the requirements. The iMac's video requirements are:

- 640x480 at 117 Hz
- 800x600 at 95 Hz
- 1024x768 at 75 Hz

However, when I'd go into the display settings and see what my options were, it only said:

- 640x480 at 60 or 56.6 Hz
- 800x600 at 60 Hz or auto
- 1024x768 at 60 Hz or auto
- Auto

I can't say for sure but I think that maybe it's not working because of that. Maybe the refresh rate is too low and the Mac simply can't handle that less of a frame rate. 

I tried forcing Lubuntu to use a different option the default 3 that I was given. I tried changing it by using these methods:

[http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/](http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/)
[http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

On a side-note: I tried installing Lubuntu 12.10 and 12.04 (alternate) on my old Toshiba Satellite 1000 laptop and it wouldn't display there either. I also tried it on my older PC and the screen would just flick on & off every second.

Since they both didn't work I tried another test. Instead of Lubuntu, I tried Xubuntu to see what would happen. To much of my surprise, Xubuntu works on my laptop and on my older PC.. I don't if there's an issue with the DE and the hardware or what..?

Other sources:

iMac specs: [http://www.everymac.com/systems/apple/imac/specs/imac_400_indigo.html]("http://www.everymac.com/systems/apple/imac/specs/imac_400_indigo.html")

---

