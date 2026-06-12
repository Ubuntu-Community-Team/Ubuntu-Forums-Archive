---
title: "Resume require reboot because of USB problem"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by beast.dk on 2008-03-24
Hi

On my Intel P35 chipset PC I have a problem with suspend/resume (as many other I have found out)

It suspend OK, but when I try to resume it tells me on the terminal/screen something like this (for all USB devices):

[I]Mar 24 09:57:46 benny-desktop kernel: [ 4040.448000] usb_endpoint usbdev8.1_ep00: PM: resume from 0, parent usb8 still 2
Mar 24 09:57:46 benny-desktop kernel: [ 4040.448000] usb_endpoint usbdev8.1_ep81: PM: resume from 0, parent 8-0:1.0 still 2
Mar 24 09:57:46 benny-desktop kernel: [ 4040.448000] usb_device usbdev8.1: PM: resume from 0, parent usb8 still 2
Mar 24 09:57:46 benny-desktop kernel: [ 4040.448000] usb_endpoint usbdev3.3_ep00: PM: resume from 0, parent 3-2 still 2[/I]

It ends with a line that states "Power down" I can then press the reboot button and the PC reboots and shows the resume login screen. When I then login the computer seams to be OK but I have no internet connection (network is down somehow). I have to reboot a second time to make it work again.

I have also seen that when I resume it goes into the normal work screen and I am able to work for 5 sec. before it show the terminal with the USB messages. In this case I may see a popup window with the message that it is unable to go into suspend mode (some error).

Any solution to this problem?

Regards

---

