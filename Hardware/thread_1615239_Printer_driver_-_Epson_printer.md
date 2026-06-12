---
title: "Printer driver - Epson printer"
date: 2010-11-06
forum: Hardware
---

### Post by ianc1 on 2010-11-06
Hi

I must confess I've never attached a printer to my Linux PC since installing over a year ago.  However I'd now like to print.  Before I dig my old printer out of the loft (an Epson Stylus Photo RX520) can someone please provide some advice.

Firstly will it just work when I plug it in via the USB or do I need to install drivers?  I've looked on [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting) and cannot find a driver for this printer.  Does this mean I'm stuffed?

This is a printer/scanner but for now I'd be happy with printing.  I dread the thought of having to boot into Windows to print.  If anyone knows anything about the scanning capabilities any advice would also be appreciated.

Thanks in advance

Ian

---

### Post by P4man on 2010-11-06
Epson provides closed source drivers through avasys:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

(scroll down to the second part). Not sure about the scanner, but I suspect it will work as well.

---

### Post by ianc1 on 2010-11-07
Thanks P4man.  Downloaded the rpm and shall attempt to install in the next evening or so.  I assume I can simply convert this to a deb archive for easier installation using alien something I found out about on this forum last night.

Would the code:```
alien -d -c filename.rpm
```be correct.

Cheers

---

### Post by P4man on 2010-11-07
Eeew, indeed, there seems to be no .deb for that printer apparently :S (although they offer one for the scanner).

You could try alien, but I dont know the syntax nor if it will work.

---

### Post by ianc1 on 2010-11-07
I assume its possible to leave the driver as it is and directly install the rpm.  Or am I being naive?

---

### Post by P4man on 2010-11-07
Not sure what you mean. RPMs are packages for red hat/fedora/suse. You can try converting them with alien to a .deb, and maybe they work, but I have no idea.

---

### Post by ianc1 on 2010-11-08
Ah, my status as a relative newbie has been exposed.

I gave alien a bash and converted the rpm to deb and what do you know I have a working printer driver.  Only one query remains and that's how reputable is avasys whoever they are that provide the driver?

Next for the scanner function

---

### Post by P4man on 2010-11-08
avasys is completely trustworthy (or at least as trustworthy as closed source software goes). They do the linux porting of drivers and software for epson, contracted (and paid for) by epson. 

Glad it worked btw.

---

### Post by krupintupple on 2010-11-08
honestly, on the wife's fresh install of 10.04, our Epson 4800MFP "just worked" when we plugged it in.

...you know, not to take any of Apple's thunder ;)

---

### Post by ianc1 on 2010-11-08
Hi krupintupple.  I to had hoped for plug and play and it appears if I had any other Epson printer that would have been the case.

---

