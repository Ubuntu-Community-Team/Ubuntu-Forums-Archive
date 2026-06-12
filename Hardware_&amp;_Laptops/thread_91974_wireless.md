---
title: "wireless"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by dmonney on 2005-11-18
I have a wireless card Hawking Tech HWC54G (rev r.). I cannot seem to find any drivers for it. please help (I'm very new and frankly I'm ready to give up cause I've had so much trouble with this)

---

### Post by Lambert on 2005-11-18
This list doesn't show rev r but there may be a linux specific driver you can use

[http://linux-wless.passys.nl/query_part.php?brandname=Hawking+Tech&zoek=brandname]("http://linux-wless.passys.nl/query_part.php?brandname=Hawking+Tech&zoek=brandname")

Load your card and type

sudo lshw -C network

You should see your card. Look at the line **configuration: **does it show a driver there?


What does iwconfig output show? If it shows something then a driver is working and identifying the card to the os as a wireless device. 

If there is a card showing in iwconfig then post the output of iwconfig here
 along with the output of ifconfig.

If the output is just a couple letters followed by a number with no more detail then post output of **sudo lshw -C network** and [B]lsmod
[/B]

---

### Post by jml on 2005-11-18
The Hawking Website lists drivers available for download.  Here is the link.

[http://www.hawkingtech.com/press.php?typeID=3](http://www.hawkingtech.com/press.php?typeID=3)

If you cannot find Linux specific drivers for your card, try using NDISWRAPPER with a windows driver for the card.  That driver should be available on the set up disc that came with your card.  Also, refer to the ....Hardware Help >> Networking Forum.  There may be a lot of helpful information for you there.  It helped me a lot with my specific hardware.  I can appreciate your frustration, it took me months to get wireless working on my laptop.  Hang in there.

Joe

---

