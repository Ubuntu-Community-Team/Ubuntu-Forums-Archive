---
title: "Acer Aspire One and its Card Readers under Intrepid"
date: 2008-11-07
forum: Hardware
---

### Post by ullix on 2008-11-07
I have Ubuntu Intrepid running on an Acer Aspire One A110L (512MB,8GB SSD). The two card readers still present problems. Unfortunately, this [Ubuntu help site]("https://help.ubuntu.com/community/AspireOne#Install Ubuntu Intrepid Ibex 8.10 on the Acer"), as well as [this one]("https://help.ubuntu.com/community/AspireOne110L"), and this [Debian Wiki site]("http://wiki.debian.org/DebianAcerOne") add to the confusion. Some statements are incorrect and some advice makes things worse. I describe what I got and hope for help:

btw: All three USB ports work out of the box.

**Out of the box: **
With SD cards inserted in both the left and right slot _before_ booting, both cards are being recognized and are shown. I can unmount and remount and remove and reinsert, or use other cards, and any card will always show up.

The card readers are from JMicron (Vendor ID=197b), there are two of them, and _each one_ has the devices with IDs 2381, 2382, 2383, and 2384 (see: [http://pci-ids.ucw.cz/read/PC/197b]("http://pci-ids.ucw.cz/read/PC/197b")). The left one is on bus 04, and the right one on bus 01. The command "lspci -nn -d 197b:*" provides this info:

#only left card inserted
04:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]

#only right card inserted
01:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
01:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
01:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
01:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]

#both cards inserted
01:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
01:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
01:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
01:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
04:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]


If only one of the two readers contains a card at boot, then only this reader is recognized and will show a card upon removal/inserting; the other one is NOT activated and does NOT respond to any card inserts!


With _no_ cards inserted neither left nor right, and then booted, no card is ever recognized upon insertion, neither left nor right. The command "lspci -nn -d 197b:*" has empty output.

**With modifications**
Doing as suggested in the Debian Wiki:

> The simplest way to activate both card slots is to create a file /etc/modprobe.d/aspire-fix-sd-slots with the following contents:

options pciehp pciehp_force=1 pciehp_slot_with_bus=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci

Lastly, add the following line to /etc/modules:

pciehp

results in the following even worse behaviour :

no cards inserted before boot: no readers ever shown nor activated by card inserts.
both cards inserted before boot: both readers are recognized as determined by the lspci command, hower, no card is shown, and no card is ever recognized upon removal/insertion.

The need, as stated on the help site, "to leave out the "pciehp_slot_with_bus=1" instruction" is not changing anything in this incorrect behaviour.

So, the only option left is to use the out-of-the-box setting, and have both card slots filled at boot. While this is what I intend to do with the left reader, where the card slides completely into the reader, it is not advised to do it for the right one, where the card does stick out enough to call for troubles in transporting.

Who can help?

---

### Post by thor2002ro on 2008-11-08
sudo nano /etc/modules and add options pciehp pciehp_force=1

and restart and they work

---

### Post by ullix on 2008-11-08
Today's updates did not look like touching hardware issues, but card reader behaviour has changed significantly, whatever the cause.

Now booting with no cards inserted recognizes the left card reader (bus#04), and inserting/removing cards works as it should. The right card reader is still recognized only when it holds a card at boot. 

#no cards inserted
lspci -nn -d 197b:*
04:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]

#only left card inserted
same as above with no cards inserted

#only right card inserted
lspci -nn -d 197b:*
01:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
01:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
01:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
01:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
04:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]

---

### Post by ullix on 2008-11-08
thor2002ro: Check my initial post - I did this and it got worse, as the readers were recognized but not any cards! Wonder if it has to do with ther readers, which seem to have been changed by Acer: from [http://wiki.archlinux.org/index.php/Acer_Aspire_One]("http://wiki.archlinux.org/index.php/Acer_Aspire_One")
# sd(hc) Card Reader left side: RICOH R5C8xx
# Multi Card Reader right side Seite: JMicron JMB385 Flash Media Controller

This is not true for my AA1, which apparently has two identical reader from JMicron.

---

### Post by ullix on 2008-11-09
thor2002ro: On second look I noticed you wanted to add the "options" line into /etc/modules. While I seriously doubt that this is ever the correct place, I tried it. The result was negative; left reader recognized, right reader not. This is same as default.
I believe you meant to say to put the "options pciehp pciehp_force=1" line into a file under /etc/modprobe.d/. While I did this before, I tried it again. Next thing that happened was that my system is crashed! All repair attempts were fruitless; Ubuntu goes into a low graphics mode and then freezes.

Bad idea.

P.S. In case it is helpful I attached a digital camera screenshot of the crashed computer (The ok button cannot be clicked and it does not respond to any keys. CTL-Alt-F1 however does work. Video memory is ok; the computer can still be started from a Live system on a USB stick)

---

### Post by thor2002ro on 2008-11-09
maybe you got a new revision of the AA1 :confused: my both card readers work perfect with the line from above....

---

### Post by stchman on 2008-12-20
I exhibit the same problems as the OP.

---

### Post by damoisture on 2009-01-09
> **stchman said:**
> I exhibit the same problems as the OP.

Try removing the first three statements in the suggested file, like suggested [here]("http://ubuntuforums.org/showpost.php?p=6497013&postcount=178"). Worked like a charm for me!

---

### Post by sandip26879 on 2009-01-26
> **thor2002ro said:**
> sudo nano /etc/modules and add options pciehp pciehp_force=1

and restart and they work

:p
Thanks,
It works smoothlyon my AA1 on Interpid. I have tested with

```
sudo modprobe pciehp pciehp_force=1
```

It is successful. Now I will write it to /etc/modules.

---

### Post by RubenGarcia on 2009-03-15
Confirmed working after just loading 

sudo modprobe pciehp pciehp_force=1

on an Acer Aspire 6935. (No other tweaking was needed). Thanks.

I am using Xubuntu 8.10.

---

### Post by SteveNorman on 2009-03-20
thors worked for me

---

### Post by RockDoctor on 2009-03-21
It's just an impression, from doing a lot of messing around trying to get the card readers to both work properly when no cards are inserted at boot time, both with Intrepid and with Jaunty; sometimes an update works, but sometimes an update breaks things. Furthermore, the confusion of adding things like "/sbin/modprobe/pciehp pciehp_force=1" to /etc/rc.local or /etc/modprobe.conf or a separate file in /etc/modprobe.d doesn't help. Is there some reason that Ubuntu and its derivatives can't come with a default configuration that just works on the Aspire One and the other Atom-based netbooks?

---

### Post by tron101 on 2009-04-01
I had most of the above issues and used all the tips from the resources mentioned above. 

Having worked this problem over a couple of days my solution was as follows...it works for me using BIOS 3309, ubuntu 8.10 on an Acer Aspire 1gb RAM, 120gb hdd. Model no zg5. 

(To make a file use $ sudo gedit)

1) Make a file 

/etc/modprobe.d/sdhc 

and add 

"options sdhci debug_quirks=1" 

(without double quotes) 

2) Make a file 

/etc/modprobe.d/pciehp 

and add  

"options pciehp pciehp_force=1" 

(without the double quotes)

3) Add the line

"pciehp" 

(without the double quotes) to the end of your existing /etc/modules file

If someone is able to explain why this works it would be useful! I just stick a card in every now and again to check it is still working:lol:

---

### Post by danteuk on 2010-07-21
Still have this problem.
Tried all the solutions here but still cards only work if inserted before booting, otherwise card readers are not detected at all

Aspire One - Atom CPU N270 BIOS 3301 ProdName: AOA150
Kubuntu 10.4 all updates installed as of 21st July 2010

---

### Post by ivan.p on 2010-10-25
Same problem here. Using BIOS v3310 and adding the options to /etc/modprobe/{sdhi,pciehp}.conf doesn't help. In my AA1, the (left) SD card slot works only when there's an SD card in it before boot. I'm going to upgrade and try again.

Surprisingly enough, "modprobe pciehp" (with or without options) does not load any module (and doesn't complain either). If nothing else works, maybe this will help:

[http://getsatisfaction.com/jolicloud/topics/how_do_you_get_the_acer_aspire_ones_sd_card_slots_to_work_hotplug_on_jolicloud#reply_2164147](http://getsatisfaction.com/jolicloud/topics/how_do_you_get_the_acer_aspire_ones_sd_card_slots_to_work_hotplug_on_jolicloud#reply_2164147)

---

