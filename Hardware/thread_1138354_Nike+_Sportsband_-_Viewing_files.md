---
title: "Nike+ Sportsband - Viewing files"
date: 2009-04-26
forum: Hardware
---

### Post by David_H on 2009-04-26
Hi all,

I recently bought a Nike+ sportsband after reading that it stored it's files internally in simple XML, thinking I could use this to write my own software for keeping track of my running.

I was expecting it to appear as a USB drive when I plugged it in to my laptop however this isn't the case.

I do get this appearing in /var/log/messages:

Apr 26 15:15:22 dave-laptop kernel: [10582.836159] usb 6-1: new low speed USB device using uhci_hcd and address 3
Apr 26 15:15:22 dave-laptop kernel: [10583.007471] usb 6-1: configuration #1 chosen from 1 choice
Apr 26 15:15:22 dave-laptop kernel: [10583.058409] generic-usb 0003:11AC:4269.0003: hiddev96,hidraw0: USB HID v1.11 Device [Nike SportBand+] on usb-0000:00:1d.0-1/input0

Could anybody give me any advice as to how to actually mount the device somewhere to see the files?

I am running Xubuntu 9.04, kernel 2.6.28-11-generic.

Thanks,
Dave

---

### Post by brandoncolorado on 2009-05-25
I would like to know this as well.  I am trying to find a way to use my sportband with Ubuntu.

---

### Post by pam196 on 2009-10-31
Bump!

I'm getting exactly the same problem as David_H, and running Ubuntu 9.04.  The system is detecting the presence of the device, just not mounting it anywhere, and I am uncertain how to.

Please could someone offer some advice?

Many Thanks,
Phil

---

### Post by haydnc on 2009-12-26
Has anyone had any luck with this yet? I'm guessing that the kernel just doesn't recognise the device ID 11AC:4269 as a kind of USB storage device, but I don't know how to change that so it does.

Perhaps there is some way to get Ubuntu using the windows driver files or something.

Any solution would be a great help.

---

### Post by rokikish on 2011-06-13
I'm having the same problem with Ubuntu 10.10 and 11.04.  it does not see the device at all.

---

