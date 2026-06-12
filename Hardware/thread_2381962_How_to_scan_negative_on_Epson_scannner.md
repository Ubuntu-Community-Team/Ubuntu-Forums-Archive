---
title: "How to scan negative on Epson scannner"
date: 2018-01-07
forum: Hardware
---

### Post by satimis on 2018-01-07
Hi all,

I have an old Epson scanner - Epson Perfection 3490 photo.

It is still working fine scanning photos by running Simple Scan.  But now I need to scan negatives because the colour of the photos fading out.

Please advise how to do it?  Thanks

Years ago I have tried it without success and finally I have to run Window7 to do the job.  Please refers to following old thread

Steps to scan negative/film on xsane 
[https://www.linuxquestions.org/questions/linux-general-1/steps-to-scan-negative-film-on-xsane-4175516199/](https://www.linuxquestions.org/questions/linux-general-1/steps-to-scan-negative-film-on-xsane-4175516199/)

Regards
satimis

---

### Post by TheFu on 2018-01-07
I bought a scanner ($99) designed for negatives and slides. Nothing else.  Then I spent the next few years digitizing all the family albums from the 1930s forward. Dad was a huge slide person, not so much for printing to photo paper.

---

### Post by satimis on 2018-01-07
> **TheFu said:**
> I bought a scanner ($99) designed for negatives and slides. Nothing else.  Then I spent the next few years digitizing all the family albums from the 1930s forward. Dad was a huge slide person, not so much for printing to photo paper.
Hi,

Thanks for your advice.

My old Epson scanner worked for me previously scanning negatives but on Window 7 only.  It is still working great without problem scanning photos by running "Simple Scan" on Ubuntu 16.04.

If I couldn't make it scanning negatives on Ubuntu I'll buy a new scanner.  Nowadays The price of a scanner is not expensive.

The 5 Best Film Scanners Under $200
[https://petapixel.com/2017/04/20/5-best-film-scanners-200/](https://petapixel.com/2017/04/20/5-best-film-scanners-200/)

Regards
satimis

---

### Post by pdc on 2018-01-07
there was a very developer of wireless devices who posted on the OpenSuse forums; and he would advise folks ........ "here is some homework" ........... and so instead here is some help [http://www.xsane.org/doc/sane-xsane-doc.html](http://www.xsane.org/doc/sane-xsane-doc.html)

Sadly I don't think there are hordes of experts on each topic around; so one relies on Mr Google to help; sorry about that

As you are lucky enough to have really good hardware; and some great slides; you are in the cherished position of potentially becoming the Ubuntu expert on how to digitise slides; we would really look forward to your contribution and I believe it would be very valuable; all best wishes

.......... I suspect you may find VueScan very helpful [https://askubuntu.com/questions/23991/software-and-scanner-for-scanning-photographic-slides](https://askubuntu.com/questions/23991/software-and-scanner-for-scanning-photographic-slides) .......... the guy Hamrick who developed and maintained the programme will provide very good forum and other support too;

---

### Post by satimis on 2018-01-11
Hi all,

Thanks for your advice and links.  I made following tests:-

1)
OS Ubuntu 16.04 desktop (spare PC AMD 8 cores with 8G RAM)
After having tried ONE day, unfortunately I'm unable to make Xsane scanning color negative films.  The result of scanning is upload on file - screenshot.jpg.

Standard 0.999 EPSON Scanner  1:00```

1  Viewer
+1 Type: JPEG
Transparency Adapter
Color
Kodak negative
800

```

Standard options EPSON Scanner 1:005```

Scan Mode : Quality scan
Enchancement
Bit depth [bit] 16
(check) Qality calibration
Adalog gamma Red [1.800]
Analog gamma greed [1.800]
Analog gamma blue [1.800}]
Brightness [%] [-167]
Contrast [%] [46]

```

2)
But I'm able scanning color negative films on following PC (for daily working) running Windows 8.1:
AMD 8 cores with 32G RAM
Host - Ubuntu 16.04 desktop
VM - Windows 8.1 64bit
Oracle VirtualBox

Software download on;
Epson Perfection 3490 Photo
[https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Windows+8.1+64-bit](https://epson.com/Support/Scanners/Perfection-Series/Epson-Perfection-3490-Photo/s/SPT_B11B177011?review-filter=Windows+8.1+64-bit)

It seems to me that Epson fully support Windows NOT Linux.  They have up-to-date solfware even for Window 10 Home/Pro.

I followed below document to proceed;
How to Scan Negatives and Slides Using EPSON Scan
[http://specular.dmc.dc.umich.edu/GroundWorks/knowledgebase/scanning-2/how-to-scan-negatives-and-slides-using-epson-scan/](http://specular.dmc.dc.umich.edu/GroundWorks/knowledgebase/scanning-2/how-to-scan-negatives-and-slides-using-epson-scan/)

On "Choosing scan settings" under "Setting up the scanning software"

I have to make following adjustment on all color negative films
Image Adjustment
Yellow -> Blue [100]

Otherwise the scanned photos will not be clear with yellowish color.  Please compare img052.jpg (yellow color) and img050.jpg upload.  I don't know why???

It took me lengthy time to scan color negatives film.

I'll find a spare 120G SSD and install Windows 10 home or pro (on the daily working PC) to make another test to see whether the scanning result will be better and with faster scanning speed.

Today the cost of a scanner is NOT expensive.  But I have to consider after having all my color negative films scanned, what shall I do with the scanner?  I won't have further new color negative films to scan.

Regards
satimis

---

### Post by TheFu on 2018-01-11
> **satimis said:**
>  Today the cost of a scanner is NOT expensive.  But I have to consider after having all my color negative films scanned, what shall I do with the scanner?  I won't have further new color negative films to scan.

I'd sell it on Craig's list or ebay when done.

---

### Post by satimis on 2018-01-12
> **TheFu said:**
> I'd sell it on Craig's list or ebay when done.
Hi,

Thanks for your advice.

My old Epson Perfection 3490 Photo scanner is still working great.  It works on Windows 10 Home as well.  The quality of color films scanned is good but the scanning speed is rather slow.

I was testing it with following setup:
(This is an AMD 8-cores PC with 32G RAM onboard)

On Windows 10 home running on VM of VirtualBox:-
Motherboard Base Memory; 20480 MB (Max 32768 MB)
Processor: 6
USB: USD 3.0 (xHCL) Controller

Epson Scan
Mode: Full Auto Mode
Film
Color Negatives
Resolution : 800 dpi
(check) Dust Remove
(check) Color Restoration

Scanning time: about 18~20 Min for 4 color negatives


I don't know whether;
1)
bare-metal scanning will be faster in speed (i.e installing Windows 10 Home on a 120G SSD, not running on VM) ?

Or

2)
A newer Scanner will improve the scanning speed?
I have checked the price of "Epson Perfection V370 Photo Scanner".  Its price is NOT expensive.  After having all color negatives scanned I can use it for scanning documents in future.  Maybe 1 or 2 times in 2~3 months.

If YES for 1) above I'll dig out an old 120G SSD on shelves to test it.

If YES for 2) above I'll let the computer shop testing it for me first before purchasing the scanner, in my next visit to computer shops.

Please shed me some light.  Thanks in advice


Edit
====
For some color negatives I need to use "Professional Mode", unable using "Full Auto Mode".  Also on "Image Adjustment" I need to set "Yellow to Blue [100]".  I suppose it is due the quality of the negatives.  Pls refer to files upload.

img018.jpg - Full Auto Mode
img019.jpg - Professional Mode ("Image Adjustment" -> "Yellow to Blue [100]")


Regards
satimis

---

