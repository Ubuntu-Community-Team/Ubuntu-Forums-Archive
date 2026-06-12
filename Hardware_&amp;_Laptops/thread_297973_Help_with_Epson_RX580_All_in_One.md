---
title: "Help with Epson RX580 All in One"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by zal91 on 2006-11-12
Hey, I have just purchased a Epson RX580 AIO Printer/Scanner, I cannot seem to get scanning to work under ubuntu 6.10 Edgy. It would be useful since this is the only reason I have a Windows partition. Future thanks goes to anyone who helps/gives their time.

*Edit:.* I have tried iScan and Xsane.

---

### Post by zal91 on 2006-11-12
No help?

---

### Post by zal91 on 2006-11-14
Ok, I just reinstalled ubuntu and now it won't even print, if anyone can help it would be appreciated.

---

### Post by bl8n8r on 2006-12-30
you might want to try the latest [*] epson cups and iscan software for this printer.  I installed these today on Edgy but pictures are printing out really really small.  Like 1" x 2". 

I used the rpm files and then used alien to convert them to deb packages and installed them that way.

apt-get install alien
alien --scripts --to-deb *.rpm
dpkg -i filename.deb

There are two commands you run then to get things setup.  One makes the ppd file and the other sets up /etc/services.  When you use dpkg to install the converted deb files, it will list the commands to run.  I dont remember what they were off-hand.  One of them, a GUI comes up to tell you the status of the installation.  I think they had a device wrong.  The installer listed /dev/usb/lp0 but the device is actually /dev/usblp0 (missing slash).  After getting that straightened out, the installer completed ok.

After that, go to system -> administration -> printing and select add a printer.  I think I restarted cups and rebooted before things worked right here.  If you dont see the rx580 listed under "Model" in step 2 of 3, select "Install Driver" and point it to /usr/share/cups/model/eksrx580.ppd (or something like that.  sorry it was on another machine). 

hope it helps.  Epson is doing a nice job supporting the linux community.  They will get better.

[*] [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

---

