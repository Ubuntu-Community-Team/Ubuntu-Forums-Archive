---
title: "Which flatbed scanner should I buy to work with Kubuntu 18.04?"
date: 2021-11-01
forum: Hardware
---

### Post by vn-casting on 2021-11-01
I'm looking for a quick scan time but also value for money.

---

### Post by fckwan on 2021-11-01
[https://www.canon.ca/en/product?name=CanoScan_LiDE_300&category=/en/products/Other-Products/Scanners/Photo-Scanning](https://www.canon.ca/en/product?name=CanoScan_LiDE_300&category=/en/products/Other-Products/Scanners/Photo-Scanning)

[https://www.canon.ca/en/product?name=CanoScan_LiDE_400&category=/en/products/Other-Products/Scanners/Photo-Scanning](https://www.canon.ca/en/product?name=CanoScan_LiDE_400&category=/en/products/Other-Products/Scanners/Photo-Scanning)

Canon Canoscan 300 and 400 support Linux.

---

### Post by Holger_Gehrke on 2021-11-02
The standard software interface to scanners in Ubuntu is SANE (Scanner Access Now Easy; also a pun because they think the mix of driver and UI in TWAIN isn't sane ...). It's [homepage]("http://sane-project.org/") features an extensive list of supported devices and the state of support for each of them.

For scanners which aren't supported by SANE there's VueScan, a commercial package from [Hamrick Software]("https://www.hamrick.com/"). They have a free trial version which puts a very annoying big watermark on scanned images but does show clearly whether or not the scanner works.

Holger

---

### Post by vn-casting on 2021-11-03
Thank you. It lists the Canoscan LiDE 300 as completely supported.

---

### Post by Tadaen_Sylvermane on 2021-11-03
I have had 99.9% success with anything HP as well. The hplip package + simple scan are 2 packages that always get installed for me around here.

---

### Post by yancek on 2021-11-03
I've always used HP also and have rarely had any problems not of my own creating, using laptops only means I rarely have the printer/scanner plugged so that's been my big problem.  I'd agree that HPLIP is really helpful..

The link below has a lot of good information.

[https://developers.hp.com/hp-linux-imaging-and-printing/KnowledgeBase/Troubleshooting/BasicHPLIPTroubleshooting](https://developers.hp.com/hp-linux-imaging-and-printing/KnowledgeBase/Troubleshooting/BasicHPLIPTroubleshooting)

---

