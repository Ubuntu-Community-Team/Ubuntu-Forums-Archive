---
title: "Looking for MFP (scanner, printer, fax) that works in Ubuntu"
date: 2010-04-28
forum: Hardware
---

### Post by andygraybeal on 2010-04-28
Hi everyone,
I'm looking for a MFP (scanner, printer, fax) machine that works with Ubuntu.  I work at a company with about 70 employees, 20 or so are in the office.  Currently we have a Dell 2335dn that works great as a printer, but only scans from MS Windows.

We like it's features: ethernet, 50 page ADF, duplexer, copy, fax, print, scan, USB jump drive and email options.  It can duplex copy, which is great with many different options.

We have it hooked directly to the network.

When scanning from the printer it supports scanning to either an application or to a directory (only for MS Windows as far as I can tell)

I followed various Ubuntu scanning websites to get this thing to scan, and I haven't made any headway.  I emailed the [EMAIL="ubuntu-users@lists.ubuntu.com"]ubuntu-users@lists.ubuntu.com[/EMAIL] as well, no solution was found.

I was very happy to come across this forum posting: [http://ubuntuforums.org/showthread.php?t=1335993](http://ubuntuforums.org/showthread.php?t=1335993)
He mentioned this MFP: 
[http://www.samsung.com/us/consumer/office/printers-multifunction/black-and-white-multifunction-printers/SCX-4826FN/XAA/index.idx?pagetype=prd_detail](http://www.samsung.com/us/consumer/office/printers-multifunction/black-and-white-multifunction-printers/SCX-4826FN/XAA/index.idx?pagetype=prd_detail)

The only thing I'm afraid of is that this device won't hold up well to the dangers that may come upon it in a 20 person office (with 70 people maybe needing to use it for whatever reason).  Amazon sells it for $226 ... which is an awesome price, and maybe worth getting to have for a year and if it breaks keep getting a new one, or something like that, as wasteful and as bad as that sounds.
Tobiasly also mentioned that it had a graphic interface for linux!  I want to jump up and down with this knowledge, but I'm fine with a HTTP interface; my office-mates might enjoy the graphical interface.

Lots of people have mentioned Brother, I'm also afraid to buy a Brother MFP for the same reasons as the Samsung.. I'm afraid that it won't last the perils of my office-mates.

I am particularly hoping that Xerox or HP have a good MFP that has network image scanning ability.

Thanks in advance,
-Andy

---

### Post by SnickerSnack on 2010-04-28
Did you already google for "linux print scan fax"?

First two hits:

1. [http://www.converttolinux.com/printer.shtml](http://www.converttolinux.com/printer.shtml)
2. [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by andygraybeal on 2010-04-28
Amazing, thank you.  I have been typing "ubuntu mfp" into google.  I wish I had known about HPLIP sooner!

Thanks again,
-Andy

---

### Post by garvint on 2010-08-31
I must warn you though, I have an Officejet 5610, multifunction, this uses hplip and supposed to "fully support" according to the website,

the full support is in fact none at all.

The Officejet 5610 doesn't fax from software, they also claim it will in future receive from hardware to software, but that isn't happening.

scan works and print works, but you get tiny cartridges, over priced that regularly need changing, so not suitable for your office. Very poor printer. I am looking for something new now

---

### Post by jeffss on 2010-09-07
In our office (~12 users) we have a HP Color LaserJet CM2320fxi MFP and a Xerox Phaser 8860MFP. Xerox does have drivers for Linux which give pretty good printing functionality. The Xerox is also fairly reliable although we have required repairs.

I finally became tired of the round-about way of scanning from the Xerox (either scan to the mfp's url or scan to a Windows remote desktop then copy to a network folder) so I looked to the HP. After some effort I succeeded and am very happy.

I know that the toner cartridges are fairly expensive (compared to the Xerox) but I can print, scan and fax using the hplip software. I can also see toner levels. It is nice to have full functionality for once.

I hope this helps.
Jeff

---

