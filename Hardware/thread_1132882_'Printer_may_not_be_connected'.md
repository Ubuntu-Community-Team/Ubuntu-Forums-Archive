---
title: "'Printer may not be connected'"
date: 2009-04-22
forum: Hardware
---

### Post by Deatzo Seol on 2009-04-22
So, I have a shared HP LaserJet 2100 connected to an ubuntu computer... now, it used to work for a couple of weeks, however, since a few days, whenever I try to print anything from any computer (inc. the server) it gives me a 'Printer HP-LaserJet-2100-Series may not be connected', while certainly, it is (parallel port)... (And, it's not the printer's problem, since when I connect it to a Windows computer, it works!)
Other printers (HP DeskJet) however, work without any problem, for a very long time ...

The error log gives:
```

E [22/Apr/2009:16:25:37 +0200] DNSServiceRegister failed with error -65537
E [22/Apr/2009:16:25:37 +0200] DNSServiceRegister failed with error -65537
E [22/Apr/2009:16:43:26 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [22/Apr/2009:16:58:11 +0200] cupsdAuthorize: Local authentication certificate not found!
E [22/Apr/2009:16:58:11 +0200] cupsdAuthorize: Local authentication certificate not found!
E [22/Apr/2009:17:11:29 +0200] PID 7769 (/usr/lib/cups/cgi-bin/admin.cgi) crashed on signal 9!

```

Any suggestions?

---

### Post by Deatzo Seol on 2009-04-23
Bump? :biggrin:

---

### Post by Deatzo Seol on 2009-04-25
... bumpity bumpity bump!

---

### Post by Deatzo Seol on 2009-04-27
Okay, so now, seemingly none of the printers work anymore, at least from remote locations. When I use the server itself to print, it prints fine... Seemingly there is a problem with CUPSd?

---

### Post by nematorc on 2009-04-28
I have same problem. I upgraded one computer from Ubuntu 8.10 to 9.04 and I installed Ubuntu 9.04 on another computer. My HP CP3503 printer is not working anymore. Same message: printer may not be connected. I tried to install hplip-3.9.2 and 3.9.4 but both installations were terminated: extraction failed.

---

### Post by nematorc on 2009-04-29
There was an update of cups. The printer is working now, but for a second printing job it is complaining again that 'Printer may not be connected'. I have to unplug the printer and plug in to make it work again.

---

### Post by Deatzo Seol on 2009-05-02
Sorry to bother again, but it still ain't been solved yet...

---

### Post by Deatzo Seol on 2009-05-04
And the LORD spoke: let there be bumps!

---

### Post by BertjeBebo on 2009-05-05
:( same problem here with a hp deskjet 720c

worked perfectly before i upgraded from 8.10 to 9.04

---

### Post by BertjeBebo on 2009-05-05
this seems to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850)

---

