---
title: "Looking for a compatible wireless device"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by aresgoddess on 2006-03-22
Hi! I was wondering if anyone had any advice on what type of wireless device I should get for my laptop so that I can connect to the wireless network at my school. 

I've read the other threads concerning wireless devices, but there were some things that I don't really understand, like WPA. That is for Wi-Fi, right? Is that very important? I am not a Wi-Fi user, I don't even really know what that is, except that the Burger King resturants in my area all offer it for free. 

My laptop is a Dell Inspiron 5150 with the Hoary Hedgehog release of Ubuntu. I debated upgrading to Breezy Badger, but I was recommended to wait for Dapper Drake to come out. Plus I really like hedgehogs. ^_^ Now that I've read (in another thread) that Dapper won't be coming out 'til June, I might just upgrade to Breezy for now since Hoary seems to be on its last leg in the forums. ;_; how sad! Anyways, if anyone can give me some advice, I'd really appreciate it!

I can't believe how much I love Ubuntu now! It rocks!

edit: I didn't realize that I was in Hardware Help for Breezy. I thought it was an all version forum for hardware support. Please forgive me. I tried to delete it so I could put it in the right one, but all I seem to be able to do is edit, not delete. =(

---

### Post by jml on 2006-03-22
Welcome to the "dark side"  (hope you got the Star Wars reference)  :mrgreen: 

Getting wireless to work in Linux is one of the most challenging aspects of this operating system, so don't feel bad about being a bit confused.  Assuming that your laptop has a PCMCIA slot, your best bet is to get a wireless card that uses the Atheros wireless chipset.  The one that I use is the NetGear WG511T.  There are others of course, but I have experience with this one.  Ubuntu 5.10 (Breezy Badger) recognizes this card.  All that is necessary is to go into the networking application, configure and activate it.

Your second question about WiFi, WEP and WPA is a bit more complicated.  WiFi is a generic term for wireless networks that use the 802.11 protocol.  WEP stands for Wired Equivalent Privacy.  It was an early form of encryption that was not too secure and could be relatively easily broken.  WPA stands for (I believe) Wireless Protected Access.  Its a stronger level of encryption, (ie harder to break.)

Ubuntu supports WEP out of the box with its Network Utility.  If you want to run a wireless network with WPA you need to download an application called wpa_supplicant.  This application will configure your computer with WPA encryption.  The only problem is that there is no graphical/user friendly interface for this application.  After it is installed, it must be configured by manually editing a configuration file.

If all you need is either unencrypted wireless access or WEP encrypted access, then you don't need to deal with wpa_supplicant.  Hope this helps.

Joe

---

### Post by aresgoddess on 2006-03-23
Ah! thank you. it helps a lot. as for the welcome, i've been on the dark side for quite some time. hee hee. ^_^ <-- cute smilie face.

---

