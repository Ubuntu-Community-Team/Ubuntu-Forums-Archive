---
title: "Dell Inspiron 1501 fn keys issue with Wireless"
date: 2012-03-18
forum: Hardware
---

### Post by Minifig666 on 2012-03-18
I'm having some issues with my laptop. It has one of the dreaded BCM4311 wireless cards.
I've successfully installed the drivers. (They appear in the Additional Drivers dialogue)
Unfortunatley I can't enable the card. I've tried the Fn+F2 combination countless times after following numerous suggestions, but I can't seem to activate the card or get the light to come on.
The card is definitely connected because I can see it in the list after a ~lspci.
Any ideas on what could be causing the issue, or a way to enable the card using terminal.
Sorry if I'm being a total noob here, new to this Linux stuffs! :D
Thanks, Mini

---

### Post by Mark Phelps on 2012-03-19
Sorry, but function keys often just don't work in Linux because they require special drivers which often are not available.

You should see if there is a switch on the Dell to turn the wireless on/off -- and turn it ON with that switch.  If not, you may just be out of luck.

---

### Post by ahallubuntu on 2012-03-19
> **Minifig666 said:**
> I'm having some issues with my laptop. It has one of the dreaded BCM4311 wireless cards.
I've successfully installed the drivers. (They appear in the Additional Drivers dialogue)
Unfortunatley I can't enable the card. I've tried the Fn+F2 combination countless times after following numerous suggestions, but I can't seem to activate the card or get the light to come on.
The card is definitely connected because I can see it in the list after a ~lspci.
Any ideas on what could be causing the issue, or a way to enable the card using terminal.
Sorry if I'm being a total noob here, new to this Linux stuffs! :D
Thanks, Mini

Silly question: have you tried simply hitting the F2 key without the Fn key?  My Dell laptop originally was set (in BIOS Setup) to use the Function keys without Fn - not what I wanted so I changed it in BIOS as soon as I figured this out!  The function keys do work on my Dell (Inspiron 1545), though.  I use Fn+F2 to turn on/off wireless all the time.

There may also be an option in BIOS Setup regarding the wireless control.  Have you looked in there?

It may be you can use a different make/model of wireless card in your Dell.  I have an Intel 5100 wireless card in my 1545 - I replaced the original Broadcom card that came with it.  I'm not sure if the Intel cards like the 5100 are compatible with your Dell, but you can get a used one for about $10 off eBay.  I'd do a bit of research first if you want to go this route (because mini-PCI wireless cards are not completely the same size even) but I have had good luck with Intel wireless cards in Linux.

---

### Post by gato2707 on 2012-03-19
I have one Inspirion 1501. If I remember well, when it was new I had same problem, I solved it activating the WiFi card from Vista (It's original OS).

At present time I have installed only Bodhi Linux and all the Fn Keys works fine, and it works totally using LiveCD.

My suggestion is: Download the Bodhi LiveCD, Activate the WiFi Card using it and then you may return to your installed Ubuntu.

Bodhi is a small LiveCD based in Ubuntu 10.04, may be you could use Ubuntu Lucid, but I really don't remember if it will work without the proprietary drivers.

As I seen, there are a lot incidents with the Ubuntu versions and Broadcom Wifi cards in versions newer than 10.04.

---

