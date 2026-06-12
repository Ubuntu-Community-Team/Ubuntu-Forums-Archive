---
title: "Canon MF3010 prints black page instead of clear PDF"
date: 2017-03-15
forum: Hardware
---

### Post by k3r10n on 2017-03-15
Hello.

I have **Canon MF3010** directly connected (**USB**) to my **32-bit Kubuntu** and I am trying to print **PDF** file - nothing but **black page**. Not every PDF file is printed like that. I guess only those editable but I am not sure if this is somehow related. Some PDFs are printed well, others are not. I tried installing cups-pdf, then I was creating PDF file anew but it didn't work either. Cups service restarted several times. I can't see proper options to modify in **cupsd.conf** file which could help here.

But - when I checked** RASTERIZATION** in PDF print options I could see text but the page was still black around. Has this something to do with the fact that this is Canon and PDF is editable? I'm trying to print the same document via Xerox Workcentre 7830 and everything is fine.

[**Update**] - As soon as I have physical access to the device, I will try to install driver from official Canon website for Linux x32/x64, step by step.  

Regards.

---

### Post by pdc on 2017-03-15
I remember something similar happening to us a while back: I need to google: something to do with clicking a tickbox somewhere; 

I think it was ```
enable the option labelled "Print as image" in the "Advanced Print Setup" dialog.
```  ....... this link isn't exactly you [https://helpdesk.win2pdf.com/index.php?/Knowledgebase/Article/View/168/0/pdf-displays-correctly-in-adobe-reader-but-doesnt-print-correctly](https://helpdesk.win2pdf.com/index.php?/Knowledgebase/Article/View/168/0/pdf-displays-correctly-in-adobe-reader-but-doesnt-print-correctly) but the sense of it might apply?

_________

to install the 32bit debian Canon package for this driver, if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and click to download and save, you will have [COLOR="#008000"]Linux_UFRII_PrinterDriver_V330_uk_EN.tar.gz[/COLOR]

install commands are  ...... line by line pasted into the terminal ...........

[COLOR="#FF0000"]cd Downloads
tar -zxvf Linux_UFRII_PrinterDriver_V330_uk_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V330_uk_EN
sudo ./install.sh[/COLOR]

and the script should start running; it may ask a couple of questions

---

### Post by k3r10n on 2017-03-18
Hi pdc, thanks for reply.

I think the option You are talking about is associated with rasterization I mentioned before. I don't have Print as image option when print dialog appears. It causes text to be somehow finally visible but the background of the page remains black.

I tried original Canon driver and I was following the manual but it didn't fix the issue. I installed common and UFR deb packages. I restarted cups service. I tried to register printer with Canon_MF3010.ppd file without success - however - my current Canon MF3010 instance uses this ppd file (and proper filter) because when I change its name, the printer does not print. When I get back to the original ppd file name - it's ok.

Although I got this 'Unable to copy ppd file' error - during printer registration procedure (according to the manual) I think it does not matter, because my current printer instance uses this ppd file.

I will try to use ./install script tomorrow - I see many options within the script. Thanks pdc.

**[UPDATE 20/03/2017] **- although [COLOR=#FF0000]Linux_UFRII_PrinterDriver_V330_uk_EN.tar.gz[/COLOR] driver did not help, the only way to bypass the issue seems to be **printing as image** indeed. To do that I had to download and install Adobe package, still available [here]("ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/") - I think printing program / filter cannot handle all PDF file structures when it prepeares a document to be sent to a device, maybe a bug? No helpful information in cups log. 

Regards.

---

### Post by ippsatsi on 2017-11-02
Hi i have Canon IR1730, I also printed pages in black, when they were scanned pages in pdf,
with  the Canon driver "linux-UFRII-drv-v340.tar.gz", a utility called **cngplp**  is installed, run it in a terminal and check the option within special  options, "Correct print data (including By N" ), and save as config defaults. With that, solve it.

[ATTACH=CONFIG]277385[/ATTACH]

---

