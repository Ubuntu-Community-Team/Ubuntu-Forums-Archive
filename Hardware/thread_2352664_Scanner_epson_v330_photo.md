---
title: "Scanner epson v330 photo"
date: 2017-02-14
forum: Hardware
---

### Post by Mantu2 on 2017-02-14
Hi,

I installed 16.04 with dual boot (win 10). I have problems with my scanner now - in Ubuntu. This Epson is not easiest to install. Actually it is so hard so I can't do a thing with the install part. I have tried many hints I found, but still nothing.

-> sudo sane-find-scanner -> found USB scanner (vendor=0x04b8 [EPSON], product=0x0142 [EPSON Perfection V33/V330]) at libusb:001:006

I've tried to follow this one: [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn't%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn't%20auto-detected)

as well this one [http://download.ebz.epson.net/man/linux/iscan_e.html](http://download.ebz.epson.net/man/linux/iscan_e.html)

Case is that this scanner needs Image Scan! for Linux (as I have used on 14.04.). What so ever I do, there is nothing installed. Could you help me and make it simply as possible for install. The notes from Epson site is not working for me - at least I think so.

---

### Post by Mantu2 on 2017-02-15
Still not working and help needed. I'll put here some info what I've figured out.

- downloading the driver and manual I found here: [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=47261&DSCCHK=106e9b9f905d401214f718b6d1981a195d91a743](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=47261&DSCCHK=106e9b9f905d401214f718b6d1981a195d91a743) Download ok and I do know how to read English
- It doesn't matter which command I'm writing in terminal. There is no lines to tell that installing have happened.
- I found out that Epson v33 and v330 is using the same driver. Case is that online manuals are not valid anymore, since the driver has been changed to multiply downloads to one-in-all package.
- I unpacked the tar.gz-file and went to my downloads folder and hit ```
sudo dpkg -i iscan-perfection-v330-bundle-1.0.1.x64.deb
```
- Well. It didn't work. Apparently the problem is that it is a folder, not a file.

So. Give me good hints how to continue.

---

### Post by Mantu2 on 2017-02-15
Ok. Got it. Good enough help from here [http://askubuntu.com/questions/724323/how-to-install-epson-l210-scanner](http://askubuntu.com/questions/724323/how-to-install-epson-l210-scanner)

---

