---
title: "[SOLVED] Ethernet failure after TV card installation"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by twin_57103 on 2008-01-08
Hi folks,

  I just installed a TV tuner card tonight (KWorld TVPlus 115), but afterwards my ethernet port appears to have failed.  The card was a bit of a bear to get in the case - I had to "dog-ear" my case a little to get it to slide in (because the coax inputs are on the case side of the card, it was difficult to slide past the edge of the case).  It's in the middle of three PCI slots, with the video card above and a modem below.  I also removed the modem (not in use) while installing the TV card (more space for my fingers), but replaced it before rebooting.

  I accidentally uplugged the router while messing around in the case, so at first I thought the network problem was just router confusion, however, it didn't come back after the usual tricks.  I plugged the same cable into my laptop and it connected perfectly, indicating that the problem was on my desktop computer.  I have booted into Ubuntu and Windows and get the same problem, indicating that it is not a driver or OS problem.

  The ethernet port is on-board and on the same motherboard connector as two USB ports.  The USB ports are fine - my mouse and printer are connected there (and they work).  I removed the TV card and booted to Linux to see if there was a device conflict, but this does not appear to be the case.  I didn't disconnect the ethernet while working in the case - just the video card (because the cord is short).   I never removed the video card, which was between the work I was doing and the ethernet connector, so I don't think I jostled it.  I've also gone back in the case and checked most of the connections.  Thank goodness for a laptop to post this!

  Am I out of luck on this port?  I don't see how I could have damaged it, but the computer seems to indicate otherwise.  Any thoughts on this problem?  Thanks!

---

### Post by twin_57103 on 2008-01-12
Well, my desktop is back online, but not the way I'd hoped.  Here's the saga, in case it will be of help to anyone who stumbles across this thread.

After some considerable tinkering, I had a friend who is a professional computer technician look at the thing.  He had no more idea than I did.  With the lack of replies to this thread, I suspect no one really had any idea.

Since we couldn't get anywhere repairing the onboard network connection, we went to plan B - replacing it.  I had to remove my (telephone) modem in order to make place for a new network card, which I got from my friend (he had an extra in his basement).  It is a U.S. Robotics 10/100 Mbps network card, model 7900.  It advertises Windows and Linux compatibility on the box.

Before installing the new card, I had to go in to my BIOS and disable the on-board jack.  That way, no OS will try to access that port.

Installation was simple - remove modem, insert network card.  I booted first to Windows and it auto detected.  The installation directions asked to update the driver from the disk, but Windows didn't detect a "better driver," so I left it as-is, and it works fine.

Linux was even easier - I didn't have to do anything except plug in the network cord.

---

### Post by nbv4 on 2008-01-17
I had the same sort of thing happen to me when I installed a wireless card. For some reason, having that card inserted into a PCI slot made my ethernet port not work. The only solution was to just take out the wireless card. Very weird.

---

