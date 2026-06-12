---
title: "Installation Guide for Brother HL-2130 on Ubuntu 11.10 64 Bit"
date: 2011-12-06
forum: Hardware
---

### Post by Football Mania on 2011-12-06
In this post, I am gonna guide you how to set up brother hl-2130 lazer printer driver properly on 64 bit ubuntu 11.10 system.


**Installation Guide for Brother HL-2130 on Ubuntu 11.10 64 Bit**

1. On Ubuntu 64 system you must be sure that you have the files that involve 32 bilt lib files. 

You can check it via:

```
dpkg -l | grep lib32s && dpkg -l | grep ia32
```

When you typed this code in terminal and didn't get any answer then go to software center and install lib32stdc++ and ia32-libs.

2.*[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2130*go](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2130*go) to this link and click on  LPR Driver and cups wrapper files which are already in  deb format, then install it download it saying that you agree.

3. Open terminal

```
cd Downloads/
sudo dpkg -i --force-all hl2130lpr-2.1.0-1.i386.deb
sudo dpkg -i --force-all cupswrapperHL2130-2.0.4-2.i386.deb
```

4. In order to see whether the drivers you install properly or not: type;

```
dpkg -l | grep Brother
```

You must get the following result:

```
ii* cupswrapperhl2130:i386* * * * * * * * *2.0.4-2* * * * * * * * * * * * * * * * *Brother HL2130 CUPS wrapper driver
ii* hl2130lpr:i386* * * * * * * * * * * * *2.1.0-1* * * * * * * * * * * * * * * * *Brother HL-2130 LPR driver
ii* ptouch-driver* * * * * * * * * * * * * 1.3-0ubuntu11* * * * * * * * * * * * * *CUPS/Foomatic driver for Brother P-touch label printers
```

5. Click on super key and type printing then you must see your printer, click on remove printer.

6. Then select add printer and on the left select HL2130 for CUPS and on the right side select HL2130 for CUPS. Then click next and then you must accomplish the process.

7. When you type in your browser's address bar: [http://localhost:631/printers/Brother-HL-2130-series](http://localhost:631/printers/Brother-HL-2130-series)

you must see the result like this:

```
Description: Brother HL-2130 series
Location: serhan-Lenovo-3000-G530
Driver: Brother HL2130 for CUPS (grayscale, 2-sided printing)
Connection: usb://Brother/HL-2130%20series?serial=G1N422630
Defaults: job-sheets=none, none media=iso_a4_210x297mm sides=one-sided
```

The installation process is complete. You are all welcome.

---

### Post by johannesri on 2012-05-15
Thanks for explaining this, but is it normal that the printer needs 1-2 minutes befor starting printing (4pages)? Testprint is fast.

---

### Post by lookit on 2012-09-01
I'm running 12.04 32-bit, and can't get my HL-2130 to print. As this is the same printer, I'm hoping someone could help.

Any ideas? While I'm in no way new to computers, I'm completely new w/ ubuntu. Any help is greatly appreciated!

---

### Post by zaihasamrizadhasfar on 2013-01-05
5. Click on super key and type printing then you must see your printer, click on remove printer.

6. Then select add printer and on the left select HL2130 for CUPS and on  the right side select HL2130 for CUPS. Then click next and then you  must accomplish the process.

7. When you type in your browser's address bar: [http://localhost:631/printers/Brother-HL-2130-series](http://localhost:631/printers/Brother-HL-2130-series)

--- i do not find the "remove printer" button, having trouble to complete steps 5 through 7. Using Ubuntu 12.04 LTS.

---

### Post by eromana on 2013-02-12
Much thanks, 
Your Brother HL-2130 installation guide also works fine on Ubuntu 11.04  64 Bit

---

### Post by chebby-monsta on 2014-02-03
Thank-you so much! I've had some serious issues with the drivers for this printer in the past but this worked perfectly first try. 

I'm using Xubuntu 13.10. Works perfect.

---

