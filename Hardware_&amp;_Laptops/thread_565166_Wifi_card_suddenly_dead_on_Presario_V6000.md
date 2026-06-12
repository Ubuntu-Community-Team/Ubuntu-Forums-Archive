---
title: "Wifi card suddenly dead on Presario V6000"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by Pazin~ on 2007-10-01
First of all, sorry for my english.

My wifi card stopped suddenly.
I've using it for 5 months with ndiswrapper and now... the LED is only orange.

My card is (used to be) a  Broadcom 43xx Wireless ( it was recognized by ubuntu as "Broadcom Corporation Dell Wireless 1390" ), but now it is not apearing in lspci anymore.

At this moment I'm using Ethernet.

I'm attaching the LSPCI and LSHW commands :(


Note: Windows Vista stopped recognizing the card too.

My card is dead?

---

### Post by tgalati4 on 2007-10-01
Is it a built-in wireless chip or is it a pcmcia card?  If it's built-in, then it's probably bad.  Look for a pcmcia wireless card as a backup solution.  Post the relevant output of:
>dmesg

---

