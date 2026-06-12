---
title: "Problems with printing machine"
date: 2016-02-15
forum: Hardware
---

### Post by miguel53 on 2016-02-15
Hi, in my work we running with Windows Xp but google chrome will no longer be giving support so I suggested Ubuntu OS because for the work we do it thru Chrome and before with Chromium I used it in my laptop and gain access to the system of my work. Anyways, I run the OS in the dvd in order to test it but the problem is that we use a receipt printer Citizen ct-s310a and when I tried to print a receipt it start to print a bunch of letters randomly and made a mess with a lot of paper wasted. Try to install differents drivers in the suggested box of the configuring area and nothing works. What can I do to get this printer done? 

P.D. Printer is connected via USB and has a connection (like the phone cable) to the cash register.

---

### Post by dave157 on 2016-02-15
Yes you did not have a driver installed that is why they printer did that. 

What brand is this laptop? to help you more what is the model of the laptop? Most of the time it is on the bottom of the laptop. what version of Ubuntu are you using?

I did a search for your printer for a driver I am sorry to tell you that that model is not supported. I am posting the link. Search for a brand you can use for your receipt printer than search for it here

[https://www.openprinting.org/printers](https://www.openprinting.org/printers)

I think it will be best to select another brand and see if it is supported in Ubuntu. Once you find a printer and you still want to use test it again but be ware once you shutdown the computer what you did will be gone and once you start Ubuntu again you will have to do what you did again. Depending on how fast your computer is you may be able to buy windows 7 and install it. Please take right click on my computer and select properties and look for CPU type and speed and Memory amount we can go from there.

dave

---

### Post by oldfred on 2016-02-16
This says there is a CUPS driver which would be Linux. Also Zebra emulation.

[http://www.citizen-systems.co.jp/english/support/download/printer/driver/](http://www.citizen-systems.co.jp/english/support/download/printer/driver/)

Many years ago we ran Zebra label printers. Using ZPL, which was in effect all the printer driver code. The XP system just sent code to printer, Linux also has a generic pass thru or RAW print drive that sends no codes, if that is how your system is configured.

[https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux](https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux)

---

