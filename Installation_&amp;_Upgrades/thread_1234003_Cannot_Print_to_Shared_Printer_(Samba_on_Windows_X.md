---
title: "Cannot Print to Shared Printer (Samba on Windows XP)"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by hwfa on 2009-08-07
I'm new to Linux ...
Just installed Ubuntu 9.04/Gnome on an Acer laptop. Wifi works to my router and thus to my Windows XP Pro tower machine. The tower has an HP Officejet 4315 attached on one of its USB ports. That works fine. The printer is shared. On the Ubuntu laptop I added a printer. The procedure found my HP 4300 on SMB://myTower and apparently appropriate (HP 4300) drivers. I clicked "Print test page". Ubuntu showed the job as "Complete" The printer clicked and whirred; the LCD screen said "Printing". The "Working" light flashed but the paper did *not* move and nothing got printed. On the Windows machine the printer's queue showed the job as "Printing". 

I also have a Sony laptop running Windows XP Pro. This machine prints happily, over my wLAN, to that same HP printer.

I found [https://answers.launchpad.net/ubuntu/+question/33007](https://answers.launchpad.net/ubuntu/+question/33007) and made the suggested changes to /etc/sysctl.conf but it didn't help (yes, I did reboot).

Help!

Please.

---

### Post by tomasrey88 on 2009-08-07
Had the same problem on my printer until I hardwired it. See, the difficulty is with solving 2 problems at the same time; wireless communication and printer communication. Solve only one problem at a time. 

Get the printer set-up using a serial cable, THEN get it set-up using wireless. This worked for me on my printer set-up. 

> **hwfa said:**
> I'm new to Linux ...
Just installed Ubuntu 9.04/Gnome on an Acer laptop. Wifi works to my router and thus to my Windows XP Pro tower machine. The tower has an HP Officejet 4315 attached on one of its USB ports. That works fine. The printer is shared. On the Ubuntu laptop I added a printer. The procedure found my HP 4300 on SMB://myTower and apparently appropriate (HP 4300) drivers. I clicked "Print test page". Ubuntu showed the job as "Complete" The printer clicked and whirred; the LCD screen said "Printing". The "Working" light flashed but the paper did *not* move and nothing got printed. On the Windows machine the printer's queue showed the job as "Printing". 

I also have a Sony laptop running Windows XP Pro. This machine prints happily, over my wLAN, to that same HP printer.

I found [https://answers.launchpad.net/ubuntu/+question/33007](https://answers.launchpad.net/ubuntu/+question/33007) and made the suggested changes to /etc/sysctl.conf but it didn't help (yes, I did reboot).

Help!

Please.

---

