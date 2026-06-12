---
title: "Epson V330 scanner install on Ubuntu 12.04 64 bit"
date: 2012-10-12
forum: Hardware
---

### Post by bhawkes on 2012-10-12
I've followed other threads and Epson support and installed in order, having first purged/removed iscan:-


iscan-data_1.18.0-1_all.deb
iscan_2.29.1-6_amd64.deb
esci-interpreter-perfection-V330_0.2.0-1_amd64.deb

ImageScan! for Linux is then present as an icon but on clicking does nothing i.e desktop remains blank.


sane-find-scanner   found V330 at libsub:001:009


Any ideas what I can next try?

---

### Post by pdc on 2012-10-12
looking at this thread

[https://answers.launchpad.net/ubuntu/+source/gscan2pdf/+question/195163](https://answers.launchpad.net/ubuntu/+source/gscan2pdf/+question/195163)

I see in post #2, Joe Taylor commented

> To set up your device for scanning via its network interface, follow the steps outlined below:

1. Download and install the latest version of Image Scan! for Linux from here.
2. If your device has a supported network interface, the iscan-network-nt plugin will also be available for download. Download and install the version appropriate for your system.
3. Now configure your device for network access. You need to set or obtain the IP address of the device. Please consult the product manual for details on how to do this.
4. [COLOR="Red"]Configure Image Scan! for Linux to connect to your device by editing /etc/sane.d/epkowa.conf[/COLOR]. You need administrative privileges to do so. [COLOR="Blue"]Read the instructions in the file about network configuration and add an entry for your device as indicated[/COLOR].
[COLOR="Red"]5. Finally, disable the conflicting epson2 SANE backend[/COLOR]. [COLOR="SeaGreen"]You can do so by changing the line consisting of "epson2" to "#epson2" in /etc/sane.d/dll.conf[/COLOR]. This will require administrative privileges.

.....he got his advice from this post

[http://avasys.jp/eng/linux_driver/faq/id000652.php](http://avasys.jp/eng/linux_driver/faq/id000652.php)

to edit such files, I would use the text editor gedit and so issue the command

> sudo gedit /etc/sane.d/epkowa.conf

and then 

> sudo gedit /etc/sane.d/dll.conf

I got my advice by googling on 

> ubuntu solved ImageScan! for Linux

---

