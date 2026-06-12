---
title: "usb mouse disconnects and then connects again"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by BungaMan on 2006-10-12
Since about a week my mouse does not respond for about a second and then works again.  I first thought this had something to do with the system hanging but the music kept on playing fine.  Checking /var/log/messages showed me the following, worrying, fact that my usb mouse seems to be disconnected at random times and detected again.

Anyone has an idea how to solve or what to check?  The address seems to change every time.  I don't know if that is a good thing or a bad thing.

[edit] I've just read on an other forum it could have something to do with power management.  I do seem to remember vaguely that this was updated with a new version not so long ago.  Any clues?

```
Oct 12 19:36:12 lapper kernel: [17271984.768000] usb 1-1: USB disconnect, address 9
Oct 12 19:36:12 lapper kernel: [17271984.880000] usb 1-1: new low speed USB device using uhci_hcd and address 10
Oct 12 19:36:13 lapper kernel: [17271985.072000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input6
Oct 12 19:36:13 lapper kernel: [17271985.072000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 19:36:51 lapper kernel: [17272024.388000] usb 1-1: USB disconnect, address 10
Oct 12 19:36:52 lapper kernel: [17272025.076000] usb 1-1: new low speed USB device using uhci_hcd and address 11
Oct 12 19:36:52 lapper kernel: [17272025.268000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input7
Oct 12 19:36:52 lapper kernel: [17272025.268000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 19:36:59 lapper kernel: [17272032.144000] usb 1-1: USB disconnect, address 11
Oct 12 19:37:01 lapper kernel: [17272033.952000] usb 1-1: new low speed USB device using uhci_hcd and address 12
Oct 12 19:37:01 lapper kernel: [17272034.144000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input8
Oct 12 19:37:01 lapper kernel: [17272034.144000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 19:37:01 lapper kernel: [17272034.412000] usb 1-1: USB disconnect, address 12
Oct 12 19:37:02 lapper kernel: [17272035.156000] usb 1-1: new low speed USB device using uhci_hcd and address 13
Oct 12 19:37:02 lapper kernel: [17272035.348000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input9
Oct 12 19:37:02 lapper kernel: [17272035.348000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 20:00:01 lapper -- MARK --
Oct 12 20:03:12 lapper kernel: [17273605.380000] usb 1-1: USB disconnect, address 13
Oct 12 20:03:13 lapper kernel: [17273606.124000] usb 1-1: new low speed USB device using uhci_hcd and address 14
Oct 12 20:03:14 lapper kernel: [17273606.316000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input10
Oct 12 20:03:14 lapper kernel: [17273606.316000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 20:03:38 lapper kernel: [17273631.332000] usb 1-1: USB disconnect, address 14
Oct 12 20:03:39 lapper kernel: [17273631.572000] usb 1-1: new low speed USB device using uhci_hcd and address 15
Oct 12 20:03:39 lapper kernel: [17273631.764000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input11
Oct 12 20:03:39 lapper kernel: [17273631.764000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1
Oct 12 20:09:20 lapper kernel: [17273973.356000] usb 1-1: USB disconnect, address 15
Oct 12 20:09:21 lapper kernel: [17273973.596000] usb 1-1: new low speed USB device using uhci_hcd and address 16
Oct 12 20:09:21 lapper kernel: [17273973.788000] input: Trust GM-4200 Gamer Optical Mouse as /class/input/input12
Oct 12 20:09:21 lapper kernel: [17273973.788000] input: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1

```

---

### Post by BungaMan on 2006-10-13
On te 4th page already... *bump*

---

### Post by Enginerd on 2006-10-13
I get a very similar problem but my mouse is not redetected unless i pull the cable and replug.

---

### Post by BungaMan on 2006-10-18
nobody?

---

### Post by Enginerd on 2006-10-18
Have you checked on launchpad to see if there is a similar bug?

What are your system specs? 

If no one has filed a bug i can start one... the more info the better.

I am running an 
AMD64 x2 (Dell E521)
Nvidia-glx beta drivers... but it happens with the nv and nvidia-glx drivers as well.

Enginerd

---

### Post by Rhubarb on 2006-10-18
It wouldn't be something hardware related would it?
Have you tried the mouse on a different Ubuntu box or tried a different mouse on your machine?

(I noticed you've got a gaming mouse there!  Lovely things gaming mice are - just got a 2000dpi one myself yesterday - no problems in Dapper so far (Logitech G5 Laser mouse)).

---

### Post by BungaMan on 2006-10-18
Not as in mouse hardware related.  As I posted before, it only started a couple of weeks ago after an update.  I can vaguely remember the gnome power manager got updated but not 100% sure and that may not even have anything to do with it.  I'll try and see what the result is after killall gnome-power-manager...  It could as well be something to do with the hal daemon or a combination etc... or the uhci_hcd driver but then I would see all the usb devices being disconnected which is not the case.

The problem seems to be more frequent when the speed of the CPU drops.  In my case to 600MHz.

It usually happens about 3 times right after each other but it could also be once or even 4 times :(

Specs:
Fujitsu-Siemens Amilo 1424
Predator GM-4200 gamer mouse optical

I will try a different mouse soon though.

---

### Post by MetalMusicAddict on 2006-10-18
Im having a simular issue. I get it on boot. Im using Edgy. Sometimes I get a mouse sometimes I dont. Its been better with new updates. I noticed that if I play with the mouse on boot it works.

Hardware:
    * Mobo: Gigabyte GA-M55SLI-S4
    * CPU: Athlon 64 X2 4600
    * Mouse: Trackman Wheel (USB)

---

### Post by BungaMan on 2006-10-19
I don't know what exactly the conflict is but it seems to be caused by my external HD which is connected via USB.  When the HD is turned on or even off, the problem occurs.  When I plug out the USB then the problem doesn't happen.

Do note that the USB HD has always been connected and never caused problems.  I do think there is a software bug that causes this.  Unfortunately I have no knowledge where to look for or analyze it.

---

### Post by pregoeater on 2006-11-02
mine was doing same thing. so i used a usb hub for my mouse and all is well.

---

### Post by BungaMan on 2006-12-10
seems to be hardware related after all.  got an intellimouse explorer now, working like a charm.

---

