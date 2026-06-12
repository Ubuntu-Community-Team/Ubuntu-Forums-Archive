---
title: "wireless issues with Dapper beta"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by jgreath on 2006-04-27
Okay, I have a Belkin wireless PCMCIA card, model fsd7010 (atheros based).  The Dapper beta livecd recognized the card just fine, and even listed it in Network Manager, though I couldn't get it to work properly.  I went ahead and installed Dapper, but after installing, my wireless card is no longer "found" by the OS.

It's difficult to past the output of various programs, as the laptop doesn't have any net access other than wireless, but:

lspci correctly identifies it as an ethernet controller from Atheros Communications, Inc., though it labels it as "Unknown device 001a (rev 01)"

ifconfig does not list ath0
iwconfig does not list ath0

lshw -C network lists it as UNCLAIMED

dmesg has a whole lot of lines mentioning that ath_pci contains an Unknown symbol

I'll see if I can find a USB thumb drive to save the outputs of those programs to and then copy them over to my working pc.

---

### Post by jgreath on 2006-04-27
Would this card work "out of the box" on a fresh install of Breezy?  I just got this laptop, so this is the first OS install I've done on it (thought I'd try something really new).

---

### Post by ssam on 2006-04-27
beta 2 just got announced [https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html)

it mentions a fix for atheros

>   * Atheros wireless network cards are now usable after installation
    (#40547).

---

### Post by jgreath on 2006-04-27
Awesome, I'll give that a shot tomorrow.

Maybe after it's all set up I'll sell this laptop on Ebay (got it for free) and use the money to fund the purchase of a nicer/newer laptop...

---

