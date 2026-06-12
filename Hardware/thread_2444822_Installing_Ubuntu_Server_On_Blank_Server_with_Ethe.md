---
title: "Installing Ubuntu Server On Blank Server with Ethernet from Windows PC"
date: 2020-06-04
forum: Hardware
---

### Post by yellow-jacket on 2020-06-04
Been trying to figure out how to install Ubuntu Server using my Windows PC connected to a blank server with a Ethernet cable. Would this be possible, or would I have to invest into like a USB and additional cable to connect it to a monitor?

---

### Post by guiverc on 2020-06-04
I'll provide a tutorial link on install server.

[https://discourse.ubuntu.com/t/install-ubuntu-server/13949](https://discourse.ubuntu.com/t/install-ubuntu-server/13949)

You can boot the install media using whatever options exist on the intended hardware, which is usually easiest using removable media (eg. cd/dvd/thumb-drive), but it can be hdd/ssd/flash-card or any device your hardware can boot from (even network device).

---

### Post by yellow-jacket on 2020-06-07
So recently I got a usb and put the server on the usb. After turning on the server with the usb in, nothing comes up and my monitor screen remains blank. I have a dell poweredge server. Which is why I wanted to figure out how to do this via ethernet connected to my other computer.

---

### Post by CelticWarrior on 2020-06-07
> **yellow-jacket said:**
> So recently I got a usb and put the server on the usb. After turning on the server with the usb in, nothing comes up and my monitor screen remains blank. I have a dell poweredge server. Which is why I wanted to figure out how to do this via ethernet connected to my other computer.

So, your logic is if the easiest way fails I'll try the hardest one instead?

Like desktop computers those servers have either BIOS or UEFI. There's always a way to access the firmware settings where you should make sure the boot device with the first priority is the live USB (or DVD). And with USBs made nin Windows either use something like Balena Etcher or, if using the very popular Rufus, make sure the settings are in accordance with the firmware type otherwise it won't boot.

---

### Post by yellow-jacket on 2020-06-07
Personally I would rather learn how to do it the harder way, but since I can't find any resources on how to do it the other way I guess I'll do it the normal way. I did however use Etcher already with a usb drive.

---

