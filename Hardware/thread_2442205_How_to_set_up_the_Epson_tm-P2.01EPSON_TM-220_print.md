---
title: "How to set up the Epson tm-P2.01/EPSON TM-220 printer connection?"
date: 2020-04-30
forum: Hardware
---

### Post by stiuna on 2020-04-30
I don't know the theory behind the ports and connections or ip addresses of the devices on linux so I don't know how I should proceed with this. I'll explain the situation to give you context.

In a work area there is an **EPSON TM-220** printer that is connected to the PC through a **LPT1 port**, at first everything worked fine until someone updated the operating system, then they "fixed" it but when the computer reboots the printer stopped working again.

When I entered the printer manager I clicked on the option "print test page" and it worked but if I print from Calc or from the browser it doesn't work.

In the window that comes out of this command:
sudo system-config-printer

In printer properties there was this connection:
Device URI **usb://EPSON/TM-P2.01**

As I said it worked until the computer restarted and I don't understand why it says usb, I guess someone redirected it there (no idea how that is done or why they would do that). When the PC was restarted, when trying to print it was on hold forever.

Then I tried this other connection:
Device URI **cups-brf:/**

And CUPS (in the browser) informed me that the printing was completed but nothing comes out in the printer.

In both cases the printer status said **"Inactive"** but the test page still managed to print.

Finally I decided to reinstall the drivers and installed the ones offered by Epson in this link:
[https://download.epson-biz.com/modules/pos/index.php?page=single_soft&cid=5012&pcat=3&scat=32](https://download.epson-biz.com/modules/pos/index.php?page=single_soft&cid=5012&pcat=3&scat=32)

I have printed a test page and it prints without any problem, however when I try to print from a program like Calc or from the Browser the story repeats as before.

The PC is 64bits, Ubuntu 18.04

---

