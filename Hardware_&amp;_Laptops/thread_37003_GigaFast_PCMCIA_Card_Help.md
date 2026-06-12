---
title: "GigaFast PCMCIA Card Help"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by jalingo on 2005-05-25
I looked into this a little bit already but am a little confused. 

I have a **Gigfast pcmcia wireless network card ** in an **IBM 600E laptop**. It sees the adapter as a Realtek pcmcia card. So how do I load drivers for it so it is correctly **configured**? There are drivers here - or are these not right? I do in fact have the card with the "R" serial number on the link below.

[http://www.gigafast.com/products/product_drivers/WF721-AEX_drivers.htm](http://www.gigafast.com/products/product_drivers/WF721-AEX_drivers.htm)

I've used Redhat 6.2 in the past but stopped using it because I though Linux wasn't ready for the masses - or me. I'm fairly technically saavy, but when it comes to using "makefile" and custom compiling drivers I'm not to sure about what to do. 

I'm also getting no sound for the Crystal sound system on the laptop. Not a priority for me but would like it enabled.

Lastly, can I make a dual boot machine with Ubuntu? I didn't see the option with the full install ISO image when I installed it.

I would appreciate any help on the pcmcia card issue. The rest I can deal with in time if no one knows the answers. Thanks for any input you can give me.

 :)

---

### Post by jalingo on 2005-05-27
I got ndiswrapper working and was able to load the WindowsXP driver for the card. It says driver is loaded, hardware found - just like the tute that's on the Wiki documentation shows.

I rebooted but it still doesn'e detect my PCMCIA card or detect a wireless network option - where to I set this up? The WiFi how-to isn't up to date as it references a menu path that doesn't exist (Computer -> network...) There's no "computer" menu. 

**ifconfig**

outputs the info for the "lo" (Loopback?) network.

**sudo ifup wlan0**

...nothing happens, just error saying it can't do it.

So what do i do next? Thanks.

---

