---
title: "can't change paper size in canon lbp2900b printer"
date: 2020-01-29
forum: Hardware
---

### Post by kinjal-hmt on 2020-01-29
I have installed canon lbp2900 printer from its official site. and its working fine. But when i tried to change paper size or page formate it stop printing. To print again i have to retstart printer and again start ccpd service. so kindly guide me to print A4 and legal size paper in canon lbp2900b.

---

### Post by guiverc on 2020-01-29
Providing your release of Ubuntu would be a good start.  

I'll provide some documentation links (given I don't know release)

[https://help.ubuntu.com/stable/ubuntu-help/printing.html.en](https://help.ubuntu.com/stable/ubuntu-help/printing.html.en)
[https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en](https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en)
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

### Post by slickymaster on 2020-01-29
Thread moved to **Hardware** for a better fit

---

### Post by kinjal-hmt on 2020-01-29
Os is Ubuntu 14.04

---

### Post by kinjal-hmt on 2020-01-29
thanks it surely helped me!

Printer successfully installed on ubuntu 14.04 64 bit system. (though canon lbp printer driver i have installed was 32 bit because 64 bit driver didn't work so i tried 32 bit and it run smoothly)
But now what problem i am facing is once i have print A4 size paper it will print successfuly. But now if i am changing page format and page type to legal nothing prints. To solve i have to restart printer then again i have to submit print then it prints.

---

### Post by coffeecat on 2020-01-29
> **kinjal-hmt said:**
> Os is Ubuntu 14.04

Ubuntu 14.04 is obsolete and unsupported. It became end of life in April 2019. There are no updates and it is or will become a security risk. You are strongly advised to upgrade to a supported release or make a fresh install. Best options would be the long term support 18.04, or the latest 19.10. Please be aware that 19.10 is an interim release and only supported for 9 months until July this year. If you need help with upgrading, you are welcome to start a new thread for this.

---

### Post by kinjal-hmt on 2020-01-30
Ok. thaks a lot!.
Previously I have tried to install canon lbp 2900 on 18.04 but it didn't work and on company website it states that it tested on ubunutu 14.04 so I go for 14.04!
Lets again upgrade to 18.04 and try to install. any help to install lbp2900b on ubuntu 18.04 will be helpful. 
thankkng in advance.

---

### Post by him610 on 2020-01-31
I am not familiar with a canon lbp2900 printer, but I am familiar with printers. I use a Dell 1700n and a Brother MFC7360N; neither would be considered new, both are several years old.
The Dell 1700n paper size is set in Printer Settings > Paper Size. 
The MFC7360 paper size is set in General Setup page.
Your canon lbp2900 printer should have similar settings. If you are unsure how do this, check your owners/users manual.
You need to access the printer settings in your printer through its (network or USB) cable connected to your computer.

---

### Post by kinjal-hmt on 2020-02-01
I am able to change paper size in lbp2900 but when i changed paper size printer doesn't take print to resolve issue i have to restart printer and system then it will print. So my point is whenever i changed paper size in printer settings i need to restart system. So any solution for this.?

---

### Post by kurt18947 on 2020-02-01
I have no experience with Canon printers so keep that in mind. What driver are you using and where did you get it? Canon sites other than U.S. are reputed to have more Linux support so if you're looking for current Canon drivers for Linux perhaps Canon Asia might be a good source. I've had better luck with manufacturer provided drivers (if they exist) than open source when it comes to the less common functions.

Edit: Here's a link to Canon Asia's Linux driver. The driver appears to be universal.

[https://asia.canon/en/support/0100924010](https://asia.canon/en/support/0100924010)

---

