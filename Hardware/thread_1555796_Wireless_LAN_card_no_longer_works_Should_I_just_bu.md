---
title: "Wireless LAN card no longer works? Should I just buy a new one?"
date: 2010-08-18
forum: Hardware
---

### Post by i2c on 2010-08-18
So I install Ubuntu on my laptop and it works wonderfully (this is a laptop I bought used) however after a couple of days the WiFi just stopped working on day while in the middle of web browsing. I tried out the LiveCD and it worked on there, I didn't have much stuff installed so I just did a fresh install and it worked again. Today it stopped working and now I boot the LiveCD and it still doesn't work. It won't even show any WiFi networks, it just says Wireless Networks disconnected. So I think it's a problem with the WiFi card inside my laptop, which I am more than capable and willing to replace if needed. It's an Atheros AR5001 by the way. I'm thinking this looks like a fine replacement, and my USB Realtek 8187 (may or may not be B I don't know) works fine without installing drivers on my laptop, so why would this one work any differently? (i.e. it should work correct?)

Any thoughts please tell me. Thank You.

---

### Post by tgalati4 on 2010-08-18
Sometimes the card comes loose inside the laptop.  Try to reseat it.  Sometimes the antenna wire wears out--it normally goes through the laptop hinge and the flexing can wear through the insulation causing an antenna short and no signal.  Sometimes the wireless chip gets toasty and delaminates from the board causing intermittent connections.  How old is the laptop?

If this is an external pcmcia wireless card, then flexing of the card--by stuffing into a tight laptop bag, can cause chip failure.  Try any card that you can return if it doesn't work, or search the forums for the tweaks required to get it to work.

---

### Post by Fafler on 2010-08-18
Go for it. Is it miniPCI or miniPCIe? I brought a Intel 5100 miniPCIe from eBay for $10, i think. It solved all kind of weird problems my previous Broadcom card had.

---

### Post by i2c on 2010-08-18
I tried reseating it more than once, I guess I'll try unplugging the antenna wires and then seeing if I can get a signal (I'll stand right next to my router) De-laminates from the board? You mean the motherboard's solder connections to the Mini-PCI-E card slot or just the Wifi LAN IC from the WiFi PCB?

---

### Post by i2c on 2010-09-06
Great, so after I bought the new WLAN card and then my old one started working again. So I got the new one in the mail and put it aside. My old one stopped working last night again,so I swapped them. The new one is a Realtek 8187B and it doesn't even show up in Ubuntu. iwconfig comes up with nothing. I tried sudo modprobe rtl8187 and nothing happened. So now I am back at square 1, except I'm out 8 dollars on a WiFi card that apparently doesn't work in Linux. What the freaking crap?

Great I tried to use NDISWrapper to install the Windows driver, and it says hardware not present, I'm starting to get pissed at Linux.

---

