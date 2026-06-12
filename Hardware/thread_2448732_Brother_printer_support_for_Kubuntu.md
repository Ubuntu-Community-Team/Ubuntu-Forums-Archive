---
title: "Brother printer support for Kubuntu ?"
date: 2020-08-12
forum: Hardware
---

### Post by oygle on 2020-08-12
Kubuntu 19.10

Our HP Photosmart C310 now won't print, informing me the paper needs to be loaded when it is already loaded. Looking to replace it. We only print a few pages each month. Just looking for good quality, quick and easy to use, and quick. Needs to have a USB connection and also a scanner; nothing complex, and most of all, the printer needs to have good support for Ubuntu.

A relative told me about this printer, a Brother - INKvestment Colour Multi-Function Printer MFC-J1300DW- [https://www.brother.com.au/en/products/all-printers/printers/mfc-j1300dw](https://www.brother.com.au/en/products/all-printers/printers/mfc-j1300dw)

Is there good support on Ubuntu/Kubuntu for Brother printers ?  Possibly a list somewhere of which models are compatible maybe ?

Looking through some other threads on Brother printers, there was a reference to "Installing a Brother Printer on Linux" at [https://kbpdfstudio.qoppa.com/install-printer-driver-on-linux/](https://kbpdfstudio.qoppa.com/install-printer-driver-on-linux/)

---

### Post by oygle on 2020-08-13
I asked Brother about support for Linux/Ubuntu and they have provided a few links

[Downloads]("https://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=mfcj1300dw_eu_as&os=128")

[What driver package format is supported by my Linux distribution?]("https://support.brother.com/g/b/faqend.aspx?c=au&lang=en&prod=mfcj1300dw_eu_as&ftype3=100257&faqid=faq00100713_000")

[FAQs & Troubleshooting]("https://support.brother.com/g/b/faqcategory.aspx?c=au&lang=en&prod=mfcj1300dw_eu_as&ftype2=10066")

---

### Post by VMC on 2020-08-13
I use to have to download and go through all that script nonsense . It was always time consuming, and didn't always work at first. I needed to tweak the PPD files.
Not anymore. For some reason all my linux os's work without intervention. I just plug it in and its recognized immediately. I have a Brother laser printer. **HL-L2330D**

---

### Post by oygle on 2020-08-13
> **VMC said:**
> I use to have to download and go through all that script nonsense . It was always time consuming, and didn't always work at first. I needed to tweak the PPD files.
Not anymore. For some reason all my linux os's work without intervention. I just plug it in and its recognized immediately. I have a Brother laser printer. **HL-L2330D**

Thanks, I noticed in Synaptic that there are already a lot of Brother drivers installed.

---

### Post by brian_p on 2020-08-13
> **oygle said:**
> 
A relative told me about this printer, a Brother - INKvestment Colour Multi-Function Printer MFC-J1300DW- [https://www.brother.com.au/en/products/all-printers/printers/mfc-j1300dw](https://www.brother.com.au/en/products/all-printers/printers/mfc-j1300dw)

Is there good support on Ubuntu/Kubuntu for Brother printers ?  Possibly a list somewhere of which models are compatible maybe ?

Printing support is excellent with an MFC-J1300DW :D.

 [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by SeijiSensei on 2020-08-13
Since upgrading to Kubuntu 20.04 my Brother HL-3170CDW now uses "driverless" printing. Opening [http://localhost:631/](http://localhost:631/) with a browser will take you to the CUPS management interface. I went to Printers and looked at the properties page for my printer.
```
Driver:	Brother HL-3170CDW series, driverless, cups-filters 1.27.4 (color, 2-sided printing)
```

I always prefer to use the native CUPS management console at localhost:631 instead of any "printers" application that comes with the operating system.

---

### Post by kurt18947 on 2020-08-14
Brother's inventory of new printers has been limited on many sites. I keep an eye on Brother printers, my current Brother inkjet multi-function is 11+ years old and ink jets don't normally live that long. I'm monitoring models and prices for the day when old faithful packs it in.  If you only print a few pages a month, do you need color? If not, monochrome laser printers can be pretty inexpensive and virtually maintenance free.

---

