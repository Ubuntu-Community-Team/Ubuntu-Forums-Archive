---
title: "wireless problem"
date: 2009-04-13
forum: Hardware
---

### Post by DjordjeRnR on 2009-04-13
Hello to all.
I have a acer aspire 5715Z laptop, and I swiched to linux ubuntu few days ago. Well, everything works fine, and I hawe one problem. Hardver says it ok, and in use, buth its not, nothing hanens when I pres the wireless button, eaven the light does not goes on. Its atheros 802.11 card, and I was looking in google, and didnt find any solutions.
What to do to make my wireless card working?

[IMG]http://img91.imageshack.us/my.php?image=wirelles.png[/IMG]

---

### Post by DjordjeRnR on 2009-04-14
anny ?

:popcorn:

---

### Post by DjordjeRnR on 2009-04-16
it looks like that at the end there is no hope at all to make my wireless card running:(:(:(:(:(

---

### Post by Daisuke_Aramaki on 2009-04-16
> **DjordjeRnR said:**
> Hello to all.
I have a acer aspire 5715Z laptop, and I swiched to linux ubuntu few days ago. Well, everything works fine, and I hawe one problem. Hardver says it ok, and in use, buth its not, nothing hanens when I pres the wireless button, eaven the light does not goes on. Its atheros 802.11 card, and I was looking in google, and didnt find any solutions.
What to do to make my wireless card working?

[IMG]http://img91.imageshack.us/my.php?image=wirelles.png[/IMG]

You obviously are missing a driver for your wireless card. I don't know if the current kernel has support for the driver or if a linux driver exists for the same. But you should find the name of the card precisely. Issue this command. 802.11 is the name of a wireless protocol.

```
lspci -v
```

you will find the manufacturer name and the details for every hardware component. 

If it helps, i found a rather old thread, more than a year old, discussing the compatibility of your laptop with linux. See if this one helps.

[http://ubuntuforums.org/showthread.php?t=640709]("http://ubuntuforums.org/showthread.php?t=640709")

---

### Post by duckfeet on 2009-04-16
I had been following your thread, and I'm glad somebody stepped in.  Somebody always does, but I went thru the exact same thing about a year ago w/my Dell wireless,and I was very frustrated, as I had wanted so to get linux, and then could not get it to work.  But I just started doing searches, and did just what the fellow who is helping you suggested, *then* did a search w/the card specs, and then downloaded nvidia and finally it worked, so you,ll get it, and don't get discouraged: getting your wireless card working taught me a whole lot about how to use the files in linux, and also, how to narrow down my searches on here...best wishes to you...

---

### Post by DjordjeRnR on 2009-04-19
it says this


05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 0136
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at 35200000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 19
	Memory at 34100000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>




what should I do ?

---

### Post by DjordjeRnR on 2009-04-20
any idea ?

---

### Post by mcwall1064 on 2009-04-21
You didn't mention what version of Ubuntu you're using. I'm using Ubuntu 9.04 x64 without issues. I'm surprised that a newer version of Ubuntu wouldn't detect the card and automatically install the correct wireless drivers. Try manually installing the the mad wifi drivers. 
When I run the lcpci |grep Wireless command my laptop displays "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)". Same card as you have in the Acer except I have a Compaq CQ60. 
If you do a google search for "madwifi driver ubuntu" you'll get a lot of tutorials on how to install the mad wifi driver. 
Good luck.

---

### Post by mitchellweston23 on 2009-04-21
i am sort of having the same issue it doesn''t matter because im not sure what a wireless button does exactley. but when i boot in windows xp professional the wireless button works and flashes blue. sorry i can't help keep looking >:)

---

