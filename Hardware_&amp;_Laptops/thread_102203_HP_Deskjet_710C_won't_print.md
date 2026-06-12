---
title: "HP Deskjet 710C won't print"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by thecwin on 2005-12-11
The HP 710C is connected to the system (Ubuntu 5.10) via the parallel port.

**from dmesg..**
```

Dec 10 08:58:00 ubuntuj kernel: [   38.959222] parport: PnPBIOS parport detected.
Dec 10 08:58:00 ubuntuj kernel: [   38.959320] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec 10 08:58:00 ubuntuj kernel: [   39.000909] parport0: faking semi-colon
Dec 10 08:58:00 ubuntuj kernel: [   39.001688] parport0: Printer, HEWLETT-PACKARD DESKJET 710C
Dec 10 08:58:00 ubuntuj kernel: [   39.006069] lp0: using parport0 (interrupt-driven).
Dec 10 08:58:04 ubuntuj kernel: [   58.573316] lp0: ECP mode
Dec 10 08:58:04 ubuntuj kernel: [   58.628261] lp0: ECP mode
Dec 10 08:58:05 ubuntuj kernel: [   58.862022] lp0: ECP mode

```

echo "whatever" > /dev/lp0 

Doesn't show any reponse from the printer, but as I understand, it's not supposed to on this printer.

I added the printer to the cups thing with the Printers dialog, and it said it had detected this HP Deskjet 710C (so I clicked that and chose the selected driver, which was pnm2ppa). However, printing things with cups doesn't show any response from the printer either. I've made sure the pnm2ppa.conf has the "version 710" line in it (saw that on another thread on this site). The CUPS page says that the printer is ready... I'll try to get more information upon request. 

Any ideas on why I can't get any response from the printer?

Thanks :)

---

### Post by datube on 2006-01-08
I did got the same problem...

So after a lot of googling a came across this page:
[http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/II.Foomatic-User/II.tutorial-handout-foomatic-user.html]("http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/II.Foomatic-User/II.tutorial-handout-foomatic-user.html")

So at:
[http://www.linuxprinting.org/]("http://www.linuxprinting.org/")

I used this path on the site to find the driver for the HP Deskjet 710c:
- Driver listenings (menu left)
- Choose pnm2ppa
- Select printer: [ HP Deskjet 710c ]
- Generate PPD file

Once downloaded goto: System > Administration > Printing
- New Printer
- Select HEWLETT-PACKARD DESKJET 710C
- Forward
- Install driver (navigate to the previous downloaded PPD file)
  (it should now show pnm2ppa (recommended)(Suggested) )
- Select Model:  Deskjet 710C
- Apply

Print a testpage...

Succes

---

### Post by dragonfoundry on 2006-02-21
Followed that through still nothing :cry:

---

### Post by PaDV on 2006-02-28
The solution for your HP Deskjet 710C printer problem is already on the forum: [http://www.ubuntuforums.org/showthre...ght=hp+printer](http://www.ubuntuforums.org/showthre...ght=hp+printer)

---

