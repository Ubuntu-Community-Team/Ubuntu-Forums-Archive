---
title: "Canon BJC 250 printing problems"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by gazsp on 2005-06-27
I've set up CUPs via the System->Admin->Printing tool to use the BJC-250 gimp-print driver and although I can print text to the printer with cat file > /dev/lp0, anything else will either not print or stall after about printing one line.

The printer is then completely locked up and the only way to try anything else is to reboot the machine.

Has anybody else encountered this problem or found a solution?

---

### Post by Xian on 2005-06-27
I don't have a direct answer, but LinuxPrinting has a nice resource page on that printer, with good information and links, including one to a Canon support forum.

[LinuxPrinting-BJC/250](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-250)

---

### Post by Typhoon on 2005-06-27
[QUOTE=gazsp]I've set up CUPs via the System->Admin->Printing tool to use the BJC-250 gimp-print driver and although I can print text to the printer with cat file > /dev/lp0, anything else will either not print or stall after about printing one line.

The printer is then completely locked up and the only way to try anything else is to reboot the machine.

Has anybody else encountered this problem or found a solution?[/QUOTE]

I had a similar problem with a Canon BJC-265SP. I fixed it by adding myself to the "lp" group:

xxx@yyy:~$ sudo addusr <login name> lp

Cheers,
Typhoon

---

### Post by TheGrinch on 2006-11-21
> **Typhoon said:**
> I had a similar problem with a Canon BJC-265SP. I fixed it by adding myself to the "lp" group:

xxx@yyy:~$ sudo addusr <login name> lp

Cheers,
Typhoon

Hi Typhoon,

I have the same problem & tried your suggestion, but I get addusr command not found. Are you sure that is correct?

Regards

---

