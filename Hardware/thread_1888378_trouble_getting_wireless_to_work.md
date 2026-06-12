---
title: "trouble getting wireless to work"
date: 2011-11-29
forum: Hardware
---

### Post by rob hayward on 2011-11-29
And I've been a good boy and checked already!!! I downloaded these fixes (as found on t'internet) hybrid-portsrc_x86_32-v5_100_82_112 as well as sp32156 and transferred them to the dell inspiron 6400 and no joy. I'm setting this laptop up for my (16yr old) neice but now I'm wondering if she'll enjoy it because, despite the publicity otherwise, you do seem to need to be pretty technically minded to use linux. Any help at all would by most appreciated,


Rob :)

---

### Post by westie457 on 2011-11-29
> **rob hayward said:**
> And I've been a good boy and checked already!!! I downloaded these fixes (as found on t'internet) hybrid-portsrc_x86_32-v5_100_82_112 as well as sp32156 and transferred them to the dell inspiron 6400 and no joy. I'm setting this laptop up for my (16yr old) neice but now I'm wondering if she'll enjoy it because, despite the publicity otherwise, you do seem to need to be pretty technically minded to use linux. Any help at all would by most appreciated,


Rob :)

Welcome to the Forum.

A bit more info about the box would be helpful.

Open a terminal (Ctrl+Alt+T) and run these commands one at a time. Copy and paste the output between ```
 tags by clicking on the # at the top of the message window please.
[CODE]lspci

lshw -C network

lsmod
```
There will probably be some others as well however this should be enough to make a start.

Thank you

---

### Post by nothingspecial on 2011-11-29
You need to post your wireless card

Open up a terminal and paste the results of

```
sudo lshw -C network
```

into a new post back here.

---

### Post by Bucky Ball on 2011-11-29
Welcome. Once it's up and running should be fine. My mother-in-law has been using hers (8.04 LTS now 10.04 LTS) - 750Kms away from where I live so I can't go fixing every prob she has - unaided for four years now and she's no geek!

Have you plugged in a cable and gotten your updates? Check System>Additional Drivers.

The latest release is unadvisable for something like this. You should go with the most stable release, 10.04 LTS which is supported until 2013. Might fix your wireless issues instantaneously while 11.10 could be a world of pain and you will spend the next week trying to set it up only for the next update to break something ...

And, yes, please post output as requested by nothingspecial and westie457... ;)

---

### Post by rob hayward on 2011-11-29
right chaps, first off, thank you so very much for such a speedy response, did the 'c network' thing, whacked it on stick, opened in notepad,  here it is:
```
symone@symone-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a8:71:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:53:96:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
symone@symone-laptop:~$ ^C
symone@symone-laptop:~$ 
```


again, thank you 

Rob

---

### Post by nothingspecial on 2011-11-29
Well the first thing to do is to plug it into your router then
```

sudo apt-get update && sudo apt-get upgrade
```

Then look and see if anything pops up in the additional driver app. An indicator should pop up on the panel if there is anthing.

---

### Post by rob hayward on 2011-11-29
I don't have a cable!!!! Everything's wifi here!!

---

### Post by westie457 on 2011-11-29
Not knowing which version you are running there is a choice of solutions.

1, If using 11.04 in Synaptic package Manager mark for complete removal of any drivers that you have installed so far. Then mark for installation b43-fwcutter and firmware-b43-installer. If you cannot find the second one enable all of the software sources  with  Settins>Repositories. Reload to refresh the sources.

Click Apply to accept the package changes you have made. Reboot and your wireless should be working.

I believe the same thing works for 11.10 as well however cannot confirm this as not actually using either of them.

2, If using 10.10 or 10.04 LTS then you should be using the Systen > Administration > Additional Drivers to activate the correct one.

Again reboot and your wireless should be working.

Click the Network Manager icon to see available networks, click on the one you want. Enter details as prompted. All done.

Any problems post back here for more help.

Thank you.

---

### Post by rob hayward on 2011-11-29
I'm using ubuntu 9.10, sorry for not having said that before, now to crack on with those suggestions.....

---

### Post by rob hayward on 2011-11-29
I don't think I actually managed to install any software!!! I just tried to run sp32156.exe and got this.......
```
Archive:  /media/Cruzer/sp32156.exe
[/media/Cruzer/sp32156.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/Cruzer/sp32156.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/Cruzer/sp32156.exe or
          /media/Cruzer/sp32156.exe.zip, and cannot find /media/Cruzer/sp32156.exe.ZIP, period.
```

---

### Post by nothingspecial on 2011-11-29
Hi Rob,

Do me a favour :)

When you post code or terminal output, please highlight it and then click the # in the formatting options at the top of the posting box.

That will put it all in nice easily readable code boxes.......

..... and stop me having to do it :p

Cheers

---

### Post by nothingspecial on 2011-11-29
You will not be able to run .exe files in Ubuntu.

It may be possible to download the b43 drivers manually from ubuntu.com, transfer them across and install them but I'm going to wait for someone else because I've never had that card or tried it.

---

### Post by rob hayward on 2011-11-29
thank you mate, will try and look them up!!

---

### Post by PPY on 2011-11-29
I think this problem is somewhat similar to what I had with my latitude d610. It was a wireless card from Broadcom as well, and to get drivers for it I had to connect with wires first. I tried to download driver using my windows computer, but failed. so finally I gave up and used wire connection (not easily accessible in my place as my router is hidden in electrical service panel). So just get connected and tehn dowload you proprietary drivers. Cannot give you step-by step instruction as I don't use Ubuntu on that laptop any more.

---

### Post by westie457 on 2011-11-29
You might be able to install the drivers from the install media.

Boot into your normal Desktop then put the CD in the tray or plug the USB in, Autorun may prompt you for the next action, if it does not then open File Browser and click the entry that corresponds to your install media.

From there navigate your way to pool > main > b > b43-fwcutter and double click the DEB package to install. Now the bit I cannot remember is if you need the other one in pool > restricted > b > bcmwl > bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb. Double click again to install. Try with one and reboot. If no wireless un-install via Synaptic. Install the other driver the same way as the first and reboot. If still no wireless reinstall the first one you tried without un-installing the second and once again reboot. Wireless should now be working.


Once it is working a good suggestion to you is upgrade at the first opportunity to 10.04 because 9.10 is no longer supported.

---

### Post by Bucky Ball on 2011-11-29
9.10 no longer supported. No-one's mentioned that and might be part of your problem, specially if attempting to get a newer wireless card up ... Drivers and firmware probably not in kernel already. ;)

Take note people: The OP has *NO* cable. Wifi only ... makes things trickier, specially for the Broadcom drivers in 9.10

---

