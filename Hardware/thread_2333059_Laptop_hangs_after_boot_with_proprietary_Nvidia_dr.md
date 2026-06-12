---
title: "Laptop hangs after boot with proprietary Nvidia driver"
date: 2016-08-06
forum: Hardware
---

### Post by Ascaris_ on 2016-08-06
Hi everyone, 

I posted about this issue on the Mint forums, but I haven't had any luck, so I tried a test install of Ubuntu MATE (x64) to see if the problem exists there too, and it does.

The laptop is an Asus F8SN laptop (well, F8SP with SN motherboard, so I guess now its an SN) with Core 2 Duo CPU and Intel PM965 chipset.  It has a Nvidia GT220M video card (part of the 9600M series, as I read), originally from another model of Asus laptop.  

It works great in Windows 7 x64, although I did have to edit the driver's .INF file to recognize the card, even though the driver was the one Nvidia suggested for the 220M (the legacy driver in the 340 series).  The card's ID matched the vendor ID and device ID sections, but the subsystem ID didn't match.  Editing one of the entries in the .INF that matched all but the subsystem to match it allowed the driver to install and run (with a "cannot verify the source of the driver" error, of course), and it is flawless in Windows now.  Stable, fast (for what it is), no glitching or artifacting.

Mint 18 x64 (tried Cinnamon and MATE) listed the 340 proprietary driver as being the recommended one from the moment it was first run.  I installed it, then rebooted as it said to.  It booted and appeared to be okay, but after logging in, it only works for 30 seconds to a minute, then the mouse clicks and keypresses stop being recognized.  The mouse arrow, if it is in the spinning wheel "busy" mode, stops animating, and the clock freezes (I have it set to display seconds, so it is immediately noticeable).  I can still move the mouse arrow around the screen, though, and the wireless button still causes the wifi light to toggle on and off (though with nothing else working on-screen, I cannot confirm that the wifi is actually being changed).

Eventually it locks up completely.  

I tried Mint 17.3 Cinnamon x64 as well as Ubuntu MATE 16.04 x64, and it's the same.  Cinnamon in software rendering mode makes no difference; it still happens.  

With the Nouveau driver, it works, but for all of the usual reasons, I would like to use the Nvidia driver.

Any hints or ideas are welcome!  Thanks.

---

### Post by Ascaris_ on 2016-08-07
Okay... I did some poking around, and I found out that I am seeing an old bug that has been mentioned many times in the past, going back as far as eight years, and which has been supposedly fixed a few times, but is also still open as an [Xorg bug]("https://bugs.freedesktop.org/show_bug.cgi?id=62912").

If I use Ctrl-Alt-F2 before the hang takes place, it soon tells me (right in the middle of me trying to log in, sometimes) that pciehp 0000:00:01.0:pcie04: Device 0000:01:00.0 already exists at 0000:01:00, cannot hot-add

I have no idea what that means, but it seems to be related, since the device at that address seems to be my video card.  Does it think I am trying to add a new device at that same address?

---

### Post by Ascaris_ on 2016-08-09
Ok, the EQ overflow and x11 hang happens also with the Nouveau driver... it just did it when I attempted to run the Peacekeeper benchmark on Firefox (48).  Right when the WebGL spheres test began (it rendered the first frame; it looks like that was as far as it got), the issue manifested again.

I also confirmed that the issue happens in Kubuntu 16.10 as well as Ubuntu Mate and Mint 18 and 17.3.  I have not yet tried any non-Debian based distros; I will have to try it and see how it goes.

---

