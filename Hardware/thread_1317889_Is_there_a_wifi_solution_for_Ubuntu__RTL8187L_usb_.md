---
title: "Is there a wifi solution for Ubuntu?  RTL8187L usb device not working"
date: 2009-11-07
forum: Hardware
---

### Post by slowtrain on 2009-11-07
Has *anyone* been able to get a recently purchased USB wifi device working / working well on a Ubuntu 9.04 system?  How 'bout a 64 bit system?  If so what was it?  Are there any plug and play devices?  If not a usb wifi device, is there a card I could put in an old PCI slot (computer was built in 2005--I guess its one of the original PCI architectures)?

I've spent the better part of a week trying dozens of ways of getting a Belkin F5D7050 (v4000) usb dongle to work and now trying to get a RTL8187L device to work.  I was unable to get them to work with: a) the company CD's drivers, b) ndiswrapper, c) downloads of drivers from the companies, or d) Ubuntu's already present drivers.  The buzz online indicated that both the F5D7050 and RTL8187 were easy installs, but apparently that doesn't apply to the F5D7050 v4000 I bought or the RTL8187 version L I got.

Would be happy to give details on what I tried with the RTL8187L.  Even got an assigned ipaddress, but cannot connect to the internet.

---

### Post by Regulas on 2009-11-07
I am having the same problem with Ubuntu 9.10 64 bit and a USB realtek rtl8187 wifi adapter. It sees my network but will not connect even if I turn off all wep and or  wpa security. It came with linux drivers but I am a newbe and it looks real complicated. Linux should really concentrate on wifi driver support during installation.
If any seasoned Linux people are out there we could use the help.

---

### Post by slowtrain on 2009-11-08
Hi Regulas:  I did try to compile the company linux drivers, but the compile process hit errors and did not finish.  From what I've seen online, these drivers can only be compiled with much older kernel headers than we have.  So there is no solution with these.

I've also now tried yet a third piece of wifi hardware:  a CNET CWP-854 PCI wifi card with what appears to be a RT2561 chipset, which I believe is made by Ralink--yet another company that Ubuntu community documentation says makes products that work with Ubuntu.  After rebooting my computer 5 times, I was able to get an assigned ipaddress using the application Wifi-radar (network interfaces never got an address).  After getting that ipaddress, the system now consistently gets an ipaddress when running from network interfaces.

And, eureka!, I now have access to the internet.  Well, not so fast.  The connection works fine until I either hibernate or put my desktop to sleep, at which point the system fairly consistently hangs on sleep or hibernate so bad I can't switch to another terminal to shutdown properly.  When it doesn't hang, other PCI weirdness starts.  So, my computer is unusable.

This is a bad situation for Ubuntu:  How can someone get not one but three wifi devices that, on the surface at least, should work with Ubuntu, but can't be made to work after a week of trying?  Increasingly, people are switching to services such as WIMAX, which often work well only from a couple spots in a house.  We need to have workable wifi access for our computers.  Ubuntu really should have much clearer, up to date information for computer owners on what wifi devices they can purchase, where, and how they can be installed.

---

