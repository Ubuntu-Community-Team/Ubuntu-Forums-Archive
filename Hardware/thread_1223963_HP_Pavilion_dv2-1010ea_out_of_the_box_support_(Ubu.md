---
title: "HP Pavilion dv2-1010ea out of the box support (Ubuntu 9.10 Alpha)"
date: 2009-07-26
forum: Hardware
---

### Post by arranmc182 on 2009-07-26
Here is a list of what hardware works out of the box

Graphics card: Works
Sound Card: Works
Network Card: Works
Bluetooth: Works
Wifi: Dose Not Work (but can be set up to work but seems to have problems with WPA2 with some routers an all versions)
Track Pad: Works
Multi Card Reader: Works
USB Ports: Works
Internal Mic: Dose Not Work (now works in the final version non-beta)

To get the WiFi card to work go to software sources & go to the third party software tab and make sure all is ticked and then go to Updates tab and make sure Proposed Updates are ticked, Then open Synaptics Package management and search for Braodcom what you need is there.

It seems like this laptop dose not fully work with APIC & ACPI so it will not read the battery properly it will give a percentage but not time remaining :(.

Also there is a small problem with sound some times the ALSA driver dose not load on boot if this happens just go to terminal and type

> $ sudo alsa force-reload

now the sound driver should be loaded and working.

---

### Post by pantropik on 2009-08-02
The lack of "time remaining" isn't just a Linux thing. It only gives the percentage in Vista, too.

---

### Post by arranmc182 on 2009-08-26
Ah well i didnt know that as i only use the Vista that came with it to crate the restore disks then installed Ubuntu

---

### Post by ozorba on 2009-11-03
Karmic WiFi has problem with dv2. At least with my dv2. Most of the time I do not get a connection and when I get the connection no internet traffic. Ethernet connection is very good.

---

### Post by arranmc182 on 2010-02-10
> **ozorba said:**
> Karmic WiFi has problem with dv2. At least with my dv2. Most of the time I do not get a connection and when I get the connection no internet traffic. Ethernet connection is very good.

I had this same problem with the beta and non-beta of Karmic what I found is that its a problem with WPA2. I run with two routers one is a Modem/Router (BT Homehub 2) That is WPA2 and just a Router no modem (Linksys WRT54GL) that is WPA, The problem I have is connecting to the BT Homehub 2 but it connects to the Linksys WRT54GL so I would say try WPA and not WPA2 and try not to use WEP.

But I find a lot of devices dont talk well with WPA2 like my Wii when on WPA2 will only connect half the time and when connected its slow and laggy but on WPA it works much smoother. 

I think WPA2 only seem to work well on newer chip sets or if two of the devices have the same chip set.

---

### Post by arranmc182 on 2010-02-10
As Ubuntu 9.10 is no longer in Beta I have started a new thread.

[http://ubuntuforums.org/showthread.php?p=8807123#post8807123](http://ubuntuforums.org/showthread.php?p=8807123#post8807123)

So submit all new posts at the new thread.

---

