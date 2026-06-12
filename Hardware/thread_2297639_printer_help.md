---
title: "printer help"
date: 2015-10-05
forum: Hardware
---

### Post by sbarretdolph2 on 2015-10-05
I can't get our printer to print anything. The printer is USB mounted. I am using Ubuntu 15.04 and the printer is recognized by the printer utility but cannot print a test page or anything. I tried pdf viewers and Libre Writer and neither would print. I tried setting it up with CUPS on the webbrowser administrator but this failed as well. I selected a generic printer but was not sure which type of printer to select. I tried most options for laser printers but nothing happened.  The printer is an Aurora which quite common in China and Taiwan. It is a laser office printer. Pretty basic model which can handle a good amount of printing. We never had any problems when we were using Windows.

---

### Post by Bucky Ball on 2015-10-05
Please open a terminal and, with the printer's USB plugged in, post the output of this command:

```
lsusb
```

... between [code] tags (see last link in my signature). 

I can find no sign of Aurora printers and Ubuntu online.

---

### Post by sbarretdolph2 on 2015-10-05
> **Bucky Ball said:**
> Please open a terminal and, with the printer's USB plugged in, post the output of this command:

```
lsusb
```

... between ```
 tags (see last link in my signature). 

I can find no sign of Aurora printers and Ubuntu online.

[code]   Bus 003 Device 003: ID 0bda:b728 Realtek Semiconductor Corp.  
 Bus 003 Device 002: ID 8087:8000 Intel Corp.  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 005: ID 5986:065c Acer, Inc  
 Bus 001 Device 006: ID 132b:20e9 Konica Minolta  
 Bus 001 Device 004: ID 17ef:602d Lenovo 
 Bus 001 Device 003: ID 17ef:602e Lenovo 
 Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

It may well be that their printers are exported and sold under another name. I will try to find that out as soon as I can. (We are in the middle of a holiday so that might not happen quickly.)

Thanks for your help.

---

### Post by SeijiSensei on 2015-10-05
Maybe it's a rebranded Konica Minolta?

---

### Post by Bucky Ball on 2015-10-05
> **SeijiSensei said:**
> Maybe it's a rebranded Konica Minolta?

... is what I'm thinking, too. What is that entry?

---

### Post by aikishugyo on 2015-10-06
If its the Konica Minolta one, then this particular PID is not yet listed in the USB ID database for Konica Minolta VID=132b
[https://usb-ids.gowdy.us/read/UD/132b](https://usb-ids.gowdy.us/read/UD/132b)
Without further information about capabilities (maybe a link to the specs somewhere?) it will be hard to figure out what could work.

---

### Post by sbarretdolph2 on 2015-10-06
Yes, it appears that it is a rebranded KonicaMinolta Bizhub 185 or 165. (The 185 model is slightly faster. When the print company is open I will find out which one is ours.) But neither are listed in the CUPS adminstration set up. I played with a few of the listed options but nothing seemed to work. 

In the open printing forum the printer is listed as hopeless for setting up. (Paperweight Division.) [http://www.openprinting.org/printers/manufacturer/KONICA%20MINOLTA/](http://www.openprinting.org/printers/manufacturer/KONICA%20MINOLTA/)

Is there any hope to get this printer to work under linux?

---

### Post by Bucky Ball on 2015-10-06
> **sbarretdolph2 said:**
> 
In the open printing forum the printer is listed as hopeless for setting up. (Paperweight Division.) [http://www.openprinting.org/printers/manufacturer/KONICA%20MINOLTA/](http://www.openprinting.org/printers/manufacturer/KONICA%20MINOLTA/)

Is there any hope to get this printer to work under linux?

I think you answered your own question. You might get lucky, but I suspect not if it is classed in the Paperweight division.

---

### Post by aikishugyo on 2015-10-06
Looking at the specs for the 165 and 185, I see that apart from GDI, they also have an XPS engine. It seem Konica Minolta, Canon, Minolta, Toshiba and Xerox produced native XPS printers.
Ref: [https://en.wikipedia.org/wiki/Open_XML_Paper_Specification](https://en.wikipedia.org/wiki/Open_XML_Paper_Specification)
So, if you can find a way to create XPS under linux, you should be able to send the XPS files directly to the printer.
Possibly you could use GhostXPS (gxps), the Ghostscript software for XPS interpretation/rendering (maybe part of GhostPDL?). Something like:
gxps-<version> -sDEVICE=xpswrite -sOutputFile=printfile.xps (or "-o filename.xps"?) -dNOPAUSE inputfile.pdf
Just some things to think about...

---

### Post by SeijiSensei on 2015-10-06
Do you have a Windows machine that the printer works with?  If so, you can share the printer in Windows and print to it over the network.

---

### Post by sbarretdolph2 on 2015-10-06
That is what I am researching now. I just set our new computer for the school and if it wasn't for printing Linux works for us much better than Windows. Now I will use an old computer for printing jobs and try to share the printer with our Linux boxes. 

The first time my team overwhelmingly preferred Linux to Windows and we have a problem that Linux can't solve. :(

---

### Post by Bucky Ball on 2015-10-06
Easily solved with a compatible printer. :) Tell 'em the fact that your printer doesn't work with Linux has little to nothing to do with Linux. If the makers of the printer don't do anything to support the printer in Linux it is up to an unpaid volunteer to spend their time and resources on getting their hands on one of these printers and trying to nut out a driver to get it running. 

Support manufacturers that support Linux, in other words, and write to ones that don't, like the manufacturers of your printer. Who knows, they might have a trick or two up their sleeve they have chosen not to mention. :)

---

### Post by sbarretdolph2 on 2015-10-06
Will do and thanks for your help. Unfortunately, the company we lease printers from will probably still stick with this line of products and their service is simply amazing. Other companies here don't provide any kind of service so we will probably just take the easy way out and keep using the laptop I set up with Windows to run our printing. Everything else will be with Linux as it has made our life so much easier. (We are a school and students need many materials which they obtain via USB sticks or portable hard drives which often are loaded with viruses. We also had a problem with some managers installing software which kept our Windows machines in a state of perpetual chaos. Since we went with Linux our problems have been dramatically reduced.) 

Anyhow, a bit long winded but thanks again for your help and support. I truly appreciate your help and the help from others here.

---

