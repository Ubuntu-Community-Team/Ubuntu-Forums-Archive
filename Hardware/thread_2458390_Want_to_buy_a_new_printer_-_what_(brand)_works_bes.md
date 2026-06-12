---
title: "Want to buy a new printer - what (brand?) works best with Ubuntu?"
date: 2021-02-23
forum: Hardware
---

### Post by equi000 on 2021-02-23
Hi,

after some struggling I managed to get my old Canon Inkjet printer work quite well with Ubuntu. But now it more or less quit working (not even a new printer head solved the „stripes“ problem). When I installed it several months ago I often read that Canon is a brand that does not very well support Ubuntu (no drivers available). In fact Gutenprint helped in this case.

Are there brands that can be especially recommended for the use with Ubuntu? 

I‘m not sure if I will by a color inkjet again or a color laser this time. Probably it should also have a scanner build in. It should be mid priced, not really cheap.

Maybe there is a list of printers available that are supported well?

Thanks for any hints!

---

### Post by brian_p on 2021-02-23
> **equi000 said:**
> 
Maybe there is a list of printers available that are supported well?

Thanks for any hints!

All modern printers are supported by Ubuntu.

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by mastablasta on 2021-02-24
HP are usually well supported.

list of supported printers is here:
[https://www.openprinting.org/printers](https://www.openprinting.org/printers)

---

### Post by Autodave on 2021-02-24
HP.  I have yet to have any problem with any HP printer.

---

### Post by mIk3_08 on 2021-02-24
Brother printer/scanner for me with wifi network connection. 
This is not to advertise but just want to share that I have this device which I use for many years now with my Ubuntu System. So far I haven't experience any problem with it with my Ubuntu System.
I use to run this device via wifi network with some network IP tweak and it was very friendly so far.
The scanner works with the Simple Scan application of Ubuntu and Xsane.

---

### Post by equi000 on 2021-02-24
Thank you all for your suggestions. I&#8216;ll see what&#8216;s available at the moment. Seems many types are sold out due to COVID and working at home at the moment.
 
In fact I can remember my time at the university in the 90th: HP with postscript always worked best on our UNIX systems...

---

### Post by equi000 on 2021-02-27
Ok, I did some checks. In case the needed support would not be pre-installed in Ubuntu: Indeed Brother delivers CUPS debian support (which should work for Ubuntu) and HP delivers its own printing system on their support download pages. Both seem the best options and both companies seem to &#8222;care&#8220; about Linux customers.

Well, Brother has cheaper toner costs and higher print/scan resolution at the same price. Maybe I go with that...

---

### Post by mastablasta on 2021-03-01
Brother are also a very good choice. we use it at work.

---

### Post by pushbike06 on 2021-03-01
The first consideration: How many print jobs/pages are you likely to do in say a year? 
   Second consideration: How much are you prepared to pay per print page?     
Third consideration: This is related to the first consideration, how much "effort" are you prepared to expend in doing the print job?   
Fourth consideration: How urgent are the print jobs likely to be. 
   Fifth consideration: Do you really need to print the job to hard copy?      

For the second consideration, the costs include the printer capital cost, consumables cost (paper, ink), convenience cost (travel to printer location) more about this  later.      

Printer manufacturers market their printers at the lowest price possible, they are actually marketing consumables the ink being the most likely. Then for commercial use, the paper and a mandatory service contract.
 For example it is common to find a perfectly capable printer at a price of say $100. That printer will have a unique printer ink cartridge that costs say $50 to replace. This cost has been a long term grievance of printer users and with the fall off in demand for the ink cartridge system, some manufacturers are offering bulk ink / reservoir style ink systems.      

An alternative to home printing is to utilise your local public library. No printer maintenance upkeep, high quality and at a page cost of < $0.50. That is where the third and fourth considerations come into play. 

    The fifth consideration is relating to the wide acceptance of digital documents and storage.

---

### Post by SeijiSensei on 2021-03-02
I have a Brother HL-3710CDW which has wifi. I never use it. I just connected the printer to my local network with an Ethernet cable and gave it a static IP address. Every device can print to it whether wired or wireless. On my Android phone I use the Brother app.

---

### Post by him610 on 2021-03-04
I have an older Brother MFC-7360N that works without any issues. I got it on sale for $99 (refurbished, originally over $300) at Staples online store several years ago. As a multi-function device it scans and faxes also; I use the scanner quite often during the tax season. Like SeijiSensei in #10, I assigned a static IP address to mine: it works great from any computer on my network. As an older device, the MFC-7360N does not have wireless connectivity so the Brother Android app does not work with legacy devices - I just tried it.

---

### Post by equi000 on 2021-03-05
Just installed my new Brother MFC_L3750CDW.

It worked almost like a charm. 

Just pressed the „WPS“ button on my router and after automated WIFI connection of the printer Ubuntu instantly installed the pre-installed driver :-) Printing worked fine, but scanning was somewhat unreliable.

So I installed the debian driver that was available on the Brother support home page. And now I have some additional settings for the print quality and scanning also works perfect. So far I‘m very pleased.

Thanks for your hints. I don‘t think I would have chosen Brother without the suggestions.

Probably I will not print more than 25-50 pages per month, but I was really sick of blocked inkjet printer heads, so I hope this laser printer will suit my application best.

---

### Post by TheFu on 2021-03-05
If compatibility is the primary goal, get a printer that supports 2 things:
[LIST=1]
[*]postscript
[*]ipp
[/LIST]
Then you are golden regardless of everything else, including the OS.

I'd avoid inkjets. The cost of ink is like gold/platinum. Very expensive.

I have a cheap Samsung PCL laser printer. It has always shown up in the list-o-printers since 14.04 - well, not the exact model, but a model that is close enough to work fully.  Thanks to CUPS, sometimes I just use **lpr** to throw PDF files directly at the printer. That works too, since it knows how to convert .ps and .pdf files for the printer.

---

### Post by brian_p on 2021-03-06
> **TheFu said:**
> If compatibility is the primary goal, get a printer that supports 2 things:
[LIST=1]
[*]postscript
[*]ipp
[/LIST]
Then you are golden regardless of everything else, including the OS.

Compatibility  with what? Why is PostScript capability a must? Why is it important? Many (most?)  modern devices do not support it.

IPP I agree with. But as, I implied in the first post in this thread, all modern printers with network capability support the protocol well.

---

### Post by SeijiSensei on 2021-03-06
I think everything supports Postscript these days except perhaps for HPs.  (I haven't owned one in quite a while.)  I actually had to switch my Brother into PS mode to print envelopes properly. Works fine in that mode for everything else, too.

---

### Post by brian_p on 2021-03-07
Not quite the situation, but many modern printers, including HPs, do indeed have a PostScript interpreter. However, the default printing system prefers other languages to send jobs to a printer, so it doesn't get used. PostScript as some part of a Gold Standard isn't the case.

---

### Post by iamjiwjr on 2021-03-08
> **brian_p said:**
> All modern printers are supported by Ubuntu.

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

.... except most Brother printers (clunky slow inconsistent functioning at best) and pretty much all Brother scanners.

---

### Post by brian_p on 2021-03-08
> **iamjiwjr said:**
> .... except most Brother printers (clunky slow inconsistent functioning at best) and pretty much all Brother scanners.

The important word is **modern**; that is, those devices put on the market in the past five years or so. However, I would alter my statement to include **network-capable**; USB-only devices may or may not support driverless printing.
So we have: all modern, network-capable printers, including those manufactured by Brother, are supported by Ubuntu.

A Brother scanner in an MFD is also very likely to be supported on Ubuntu via SANE and/or **sane-airscan**.

---

