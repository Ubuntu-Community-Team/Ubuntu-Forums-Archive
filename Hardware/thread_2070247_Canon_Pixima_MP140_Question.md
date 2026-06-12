---
title: "Canon Pixima MP140 Question"
date: 2012-10-12
forum: Hardware
---

### Post by Roly34 on 2012-10-12
I've got a Laptop that's currently running Windows 7 Ultimate x64 and a Netbook that is currently running OpenSuse 12.2 x86 and a Canon Pixima MP140 AIO Printer/Scanner/Copier and I'm considering moving over to Ubuntu and wondered how easy it is to setup the Printer with the drivers that Canon provide for linux on there website especially 12.04 and 12.10 when it's released?

Roland

---

### Post by oldfred on 2012-10-12
I have a Canon Pixima MP160. It came "free" with my new laptop 6 years ago. It took a while (months) to find drivers on a Canon Asia site. Fortunately I still had my old printer at that time. 

All recent versions of Ubuntu have just worked. I turn printer on and add printer and it adds it. 

The newest version with 12.04 has had a regression or two. It at first would only print one page and lock up. I had to pull power plug to reset. Now it prints one page and scans just fine, but on multiple pages often locks up after printing last page.

---

### Post by Lyfang on 2012-10-12
I have a Canon PIXMA MP190 using Lubuntu 12.04. Simply plug it in and install the driver. The printer works with printer driver: Canon PIXMA MP190 - CUPS+Gutenprint v5.2.8-pre1 [en]. Working Canon PIXMA MP190 printer driver worked in Ubuntu 12.04 LTS (Precise Pangolin) Beta 2 and latter. Before I was using the drivers for PIXMA MP180. Add printer by: System &#8594; Administration &#8594; Printing or CUPS (Common UNIX Printing System) type [http://localhost:631/](http://localhost:631/) in your web browser. Canon PIXMA MP190 scanning works with Simple Scan in Lubuntu 12.04 as well. The Canon PIXMA MP140 - CUPS+Gutenprint v5.2.8-pre1 driver is listed in Lubuntu 12.04. I hope this will help.

---

### Post by Roly34 on 2012-10-12
> **Lyfang said:**
> I have a Canon PIXMA MP190 using Lubuntu 12.04. Simply plug it in and install the driver. The printer works with printer driver: Canon PIXMA MP190 - CUPS+Gutenprint v5.2.8-pre1 [en]. Working Canon PIXMA MP190 printer driver worked in Ubuntu 12.04 LTS (Precise Pangolin) Beta 2 and latter. Before I was using the drivers for PIXMA MP180. Add printer by: System &#8594; Administration &#8594; Printing or CUPS (Common UNIX Printing System) type [http://localhost:631/](http://localhost:631/) in your web browser. Canon PIXMA MP190 scanning works with Simple Scan in Lubuntu 12.04 as well. The Canon PIXMA MP140 - CUPS+Gutenprint v5.2.8-pre1 driver is listed in Lubuntu 12.04. I hope this will help.
I followed the Instructions on 12.10 Beta 2 and it was listed as soon as I plugged in the Printer and turned it on and went to CUPS web Interface, was so easy to Install compared to when I tried Installing it in OpenSuse 12.2 on Wednesday.

Think it's time to backup the Notebook HDD and burn 12.10 Beta 2 x64 and ditch Windows.

I only use the Printer & Copier side of the Printer and very rarely use it for Scanning.

Roland

---

### Post by pdc on 2012-10-12
and the scanner side of the MP140 is listed as completely supported by SANE: the linux open scanning programme

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

---

### Post by turboscrew on 2013-05-01
> **oldfred said:**
> I have a Canon Pixima MP160. It came "free" with my new laptop 6 years ago. It took a while (months) to find drivers on a Canon Asia site. Fortunately I still had my old printer at that time. 

All recent versions of Ubuntu have just worked. I turn printer on and add printer and it adds it. 

The newest version with 12.04 has had a regression or two. It at first would only print one page and lock up. I had to pull power plug to reset. Now it prints one page and scans just fine, but on multiple pages often locks up after printing last page.

Is there a new working version to replace (I guess) CUPS+Gutenprint v5.2.9? (This version acts up as you described.)
Or which would be the earlier still working version?
Or maybe it would be better idea to use PIXMA MP 150 drivers instead of 140?

It's annoying when "reset" by pushing the power button is not enough but a "power chord reset" is needed.
It's especially annoying when paying the bills and printing the receipts.

---

### Post by Resistent on 2013-05-01
I have a Canon Pixma MG2250, the driver are on the net:  ([http://support-asia.canon-asia.com/P/search?model=PIXMA+MG2270&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG2270&menu=download&filter=0&tagname=g_os&g_os=Linux))

But, for installation I did (after problems with installing the files above):

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get install cnijfilter-mg2250series scangearmp 

To start the scanning Application you have to enter in the terminal:  scangearmp

Maybe from interest, I found the page where the Pixma Error Codes are... 
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2250.aspx?faqtcmuri=tcm:14-958376&page=1&type=faq](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2250.aspx?faqtcmuri=tcm:14-958376&page=1&type=faq)

---

### Post by turboscrew on 2013-05-02
Thanks. I'll try that.
This: [https://launchpad.net/~till-kamppeter/+archive/ppa](https://launchpad.net/~till-kamppeter/+archive/ppa)
didn't seem to install.

---

### Post by aikishugyo on 2013-05-02
The issue with non-printing in gutenprint 5.2.9 is either a bug in gutenprint or in CUPS, not sure which, that would depend on the situation perhaps.
As far as I am aware, 5.2.9 did not introduce bugs of this sort, but I am investigating issues with "borderless".
The Canon driver no doubt will give better printing for photos.

---

### Post by turboscrew on 2013-05-02
The printer is shared via Samba, so I guess Cups...

---

