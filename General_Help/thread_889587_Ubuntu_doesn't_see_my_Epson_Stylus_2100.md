---
title: "Ubuntu doesn't see my Epson Stylus 2100"
date: 2008-08-14
forum: General Help
---

### Post by PeterLB on 2008-08-14
Hi folks, and apologies if this is in the wrong forum, but I'm rather new to Ubuntu as I only installed it on one of my PC's yesterday.

I'm running v8.04.1 and it installed with no problems whatsoever, (way quicker than Widoze too :))

Everything works fine except one thing..... it simply doesn't 'see' my Epson Stylus Photo 2100 which is connected via USB.

It happily sees and prints to my hp Laserjet 1010 which is also connected via USB, but when I try to add a printer the auto search simply doesn't see the Epson.

Spent a long time trawling the net but the only things I could find were a) to disconnect the hp and leave only the Epson connected, and b) to download Gimp-Print (now apparently superseded by gimp-gutenprint).

Both of these I've tried, but with no success whatsoever.

Can anyone else suggest what may be the route of the problem or what to try next?

Thanks in advance, and best regards

Peter

Edit......

Plugged the Epson into a Windoze machine and it was recognised immediately, but not by Ubuntu when I plugged it back in there.

followed the Debuging Printer Problems section at [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) and got the following report............

lpinfo -v
network socket
network beh
direct hal
direct hpfax
direct hp
network http
network ipp
network lpd
direct parallel:/dev/lp0
file cups-pdf:/
direct scsi
network smb

---

### Post by PeterLB on 2008-08-15
Bump.

Anyone?

I'm desparate to solve this as the only other solution I have is to go back to Windows, and I really don't want to have to do that!!!!

---

