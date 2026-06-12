---
title: "ADS TECH DLX-181 USB2.0/Firewire pcmcia"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by mezzmerized17 on 2007-10-26
I'm running UbuntuStudio Gutsy and Linux Mint XFCE on a Gateway mx8530 notebook.
It has a built-in 4-pin firewire port, but the connection sucks and the cable will never stay in right.
I have tried multiple cables and fiddled with both male and female physical connectors to improve the connection. No deal.

So...I picked up an ads tech adx-181 usb 2.0/ firewire pcmcia card since the 6-pin connectors on my desktop work fine (others apparently have problems with 4-pin connections on gateway lappies too).

This is a multi-tiered project since I need to use the Presonus firepod with freebob/jack. If I can get the cardbus to work, then I have to configure the freebob deal and all.

I have pcmcia-utils and udev installed, but the card is not recognized either when connected at boot or any other time.

I have scoured google and these forums and haven't found much info.

Am I supposed to configure something? If so what? Is ndiswrapper a possibility? 

I am at a loss. Anyone have advice as to where to begin?

Any help would be greatly appreciated.

########################################################################
Update: My ignorance unabated!

I had been so focused on the fw inputs that I had neglected to try the usb2.0.

Upon plugging a 1gb pny flashdrive and compaq optical usb mouse into the 2 available ports on the card, THEY WORK!!

So, the card works out of the box in UbuntuStudio feisty/gutsy and Linux Mint 3.1 XFCE (cassandra) [ubuntu-based].

It appears that everything is on udev/freebob now.

I'm at work now and have no Firepod to test. Will report back soon.

---

