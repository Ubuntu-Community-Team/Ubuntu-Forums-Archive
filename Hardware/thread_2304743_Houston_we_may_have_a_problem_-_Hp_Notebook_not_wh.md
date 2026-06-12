---
title: "Houston we may have a problem - Hp Notebook not what I ordered?"
date: 2015-11-29
forum: Hardware
---

### Post by michael-piziak on 2015-11-29
I went back and reviewed the Notebook I ordered, and I do not think I got what I bought.

Amazon still gives me the option to return it to the vendor, but I want to make sure I have my ducks and facts straight before I click return and type in a reason.

This is what I ordered:
[http://www.amazon.com/gp/product/B00BJ8C02I?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s00](http://www.amazon.com/gp/product/B00BJ8C02I?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s00)

The 2 screenshots below is what I think I got - which appears to be 1.6 gib ram instead of 4 and a different graphics card?
I added 1 screenshot of the computer I bought on the Amazon website if the link above doesn't work.

Also, I just added another screenshot.  The computer is advertised as a 320 gig HD - looks to me like it only has 291 gig HD total - ?

---

### Post by Yellow Pasque on 2015-11-30
Easy way to tell what memory is physically installed:
```
sudo apt-get install dmidecode
sudo dmidecode -t memory
```

Most likely, it's an issue with your BIOS and Ubuntu/Linux, possibly caused by running an older version on newer hardware. It would be interesting to boot a LiveUSB of Ubuntu 15.10 and see if that recognizes all of the RAM. If it does, you can try running a newer  kernel on your install, since I know you want to stick with 12.04

```
The computer is advertised as a 320 gig HD - looks to me like it only has 291 gig HD total - ? 
```
[https://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](https://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by Bucky Ball on 2015-11-30
You can also use 'top' in a terminal and see what amount of RAM that reports. The hard drive size of 291 for a 320Gb hard drive is normal. Check Temüjin's link and forget about it. :)

That's not an issue but the RAM's odd. :-k

---

### Post by michael-piziak on 2015-11-30
```
Configured Clock Speed: Unknown

Handle 0x0026, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0023
    Error Information Handle: 0x0028
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom-Slot 2(under)
    Bank Locator: CHANNEL A
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 1066 MHz
    Manufacturer: A-DATA Technology
    Serial Number: 00005E3B
    Asset Tag: Asset Tag: 
    Part Number: AM1U16BC2P1-B1AH  
    Rank: 1
    Configured Clock Speed: 533 MHz

michael@michael-HP-2000-Notebook-PC:~$
```

---

### Post by Bucky Ball on 2015-11-30
You have a 2Gb stick in channel A according to that output. Is that all of your output? In this case, 1.6Gb might be about right. Your Amazon link says:

> 4GB DDR3 SDRAM (1 DIMM)

Your output says:

```
Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom-Slot 2(under)
    Bank Locator: CHANNEL A
```

Guess you could physically check what's in there.

---

