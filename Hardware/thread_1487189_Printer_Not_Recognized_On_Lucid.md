---
title: "Printer Not Recognized On Lucid"
date: 2010-05-18
forum: Hardware
---

### Post by GonzalitoUY on 2010-05-18
The printer is a Canon IP1000, that was working flawleesly on Karmic, after a little tweaking.
But under Lucid, is not even detected as a printer, but is recognized as USB device, on "lsusb"
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 011: ID 04a9:1098 Canon, Inc. PIXMA iP1000
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Although previously not supported on Karmic, it was at least showing the "add printer" when connected. Now I don't even have that.
I can always use that printer on another OS, but don't know why it used to work,and now it doesn't.Can't even add it to VirtualBox, as it gets an error only on this USB device

---

### Post by 99_rover on 2010-05-18
I fixed following a suggestion in another thread

sudo service cups start

starts the cups so at least you can get going

---

### Post by GonzalitoUY on 2010-05-18
Nope,that didn't worked, but thanks for the advice, I'll keep trying, but it doesn't look good for this printer

---

### Post by ianmillington on 2010-05-19
The printer isn't listed at openprinting.orgYou may find this useful

[http://software.canon-europe.com/software/0032993.asp?model=](http://software.canon-europe.com/software/0032993.asp?model=)

---

### Post by GonzalitoUY on 2010-05-19
But why it was working on Karmic, on now is gone? What DID change, CUPS, something on the USB system? I know many people that use this printer, as it is quite cheap on ink, just want to know where did something go wrong.
EDIT:Installing manually, adding the URI, and using the driver that I could find and was working til Karmic, but get an error on the naming step, «client-error-not-possible»

---

### Post by ianmillington on 2010-05-19
Truth is, I haven't a clue. This may shed some light though if you look down the list. 

[https://wiki.kubuntu.org/HardwareSupportComponentsPrintersCanon](https://wiki.kubuntu.org/HardwareSupportComponentsPrintersCanon)

By all accounts, the fact you had it running in Karmic seems a minor miracle. Your best chance is, I would suggest, with the Canon driver.

---

### Post by ianmillington on 2010-05-19
Truth is, I haven't a clue. This may shed some light though if you look down the list. 

[https://wiki.kubuntu.org/HardwareSupportComponentsPrintersCanon](https://wiki.kubuntu.org/HardwareSupportComponentsPrintersCanon)

By all accounts, the fact you had it running in Karmic seems a minor miracle. Your best chance is, I would suggest, with the Canon driver.

---

### Post by chitowner2 on 2010-06-17
Same scenario, different printer.

I have an HP4315 Officejet. This is an "all-in-one" type using a USB cable. It was working fine on karmic, but after a clean install (not upgrade) to lucid, I can't connect to it despite doing a setup in system-manager (KDE). This is on my desktop PC.

I tried moving the printer to my laptop, upgraded recently to lucid/kde. I have never had any printer connection to this laptop, and I could not even get system manger to do a setup.

Next I moved the printer to another PC still runing karmic/kde. Presto! As soon as the printer is plugged in, it is automatically connected and prints fine, requiring no manual attention. Not sure if it matters, but this PC also has never been connected to a printer. 

SO what the heck is going on with lucid and printers? Anybody got a clue?

CT

---

### Post by ianmillington on 2010-06-17
I tried to add a printer in kubuntu lucid via the printer settings manager. It wasn't even recognised due I believe to a bug in the kde print manager which doesn't allow the addition of a local printer for some reason.

Try opening your browser and typing [http://localhost:631](http://localhost:631) 

This is the cups config page and might allow you to sort this.

---

### Post by chitowner2 on 2010-06-17
> **ianmillington said:**
> I tried to add a printer in kubuntu lucid via the printer settings manager. It wasn't even recognised due I believe to a bug in the kde print manager which doesn't allow the addition of a local printer for some reason.

Try opening your browser and typing [http://localhost:631](http://localhost:631) 

This is the cups config page and might allow you to sort this.


I did try that in Konqueror, but for some crazy reason it went to a wonderful Comcast 404 page. Geez do I hate that!

On the bright side tho, further perseverance has paid off. I found this:

> 
[http://kubuntuguide.org/Lucid#Printers_and_Scanners](http://kubuntuguide.org/Lucid#Printers_and_Scanners)
HP Printers

For Hewlett Packard printers / scanners, install hplip and hplip-gui.

sudo aptitude install hplip hplip-gui

Then, click on menu > applications > system > HP Toolbox to add the printer. This should set up printer / scanners for scanning as well.


That fixed my problem, thanks to HP. No idea if there is anything comparable for Canon or others tho.

CT

---

### Post by 741Baus on 2010-06-29
I had a similar problem to this after an upgrade to Lucid but , with a Canon Pixma MP160,installing printconf from Synaptic resolved this , it install a few other packages and dependencies and I am now able to print from browser and e-mail client .

---

### Post by this_costs_more_cell_bill on 2011-02-16
I don't know about other trademarks, but I know for sure about Canon drivers using old, obsolete, packages.
Maybe assuring the right packages may help. I learned from different forums posts and I wrote here step by step what to do: [http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon](http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon)

---

