---
title: "getting epson scanner to work"
date: 2008-07-26
forum: Hardware
---

### Post by DenzilS on 2008-07-26
Hi, all,

I have an Epson Perfection 1260 scanner that doesn't work with Ubuntu 8.04. I fire up Xsane, which correctly identifies the scanner, but when starting a scan it makes a small clunk as if the scanner drive motor starts to move, but does nothing else.

I switched to Ubuntu from Suse 10.0, and had a similar problem there, which I resolved by installing Iscan and ignoring Xsane. Iscan is not available from the repositories, so seeing as this scanner is supposed to work out of the box, what can I do?

Denzil

---

### Post by empty_spaces on 2008-07-26
I have an Epson CX7400 all-in-one. To get Hardy to detect the scanner, I had to install the **libsane-extras** package from the repositories.
Don't know if you need the same, but thought I'd mention it.

---

### Post by DenzilS on 2008-07-26
Good idea but it didn't make any difference. Thanks anyway.

---

### Post by phidia on 2008-07-26
Take a close look at [this page]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson+&model=perfection+1260&bus=any&v=&p=") and specifically your model.
One thing I notice is that the sane site seems to say the backend for that scanner is not in the kernel (so you need to load a module i think) and then there's this note:
> requires DFSG non-free iscan-plugin-gt-7300<br>also supported by the plustek backend<br>overseas version of the GT-7300U
There is more info available at the link I inserted.

From the Ubuntu hardware wiki I see that [this page]("https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson") does list OOTB support _but_ that's for 5.10 I don't think you can infer support for more recent versions from that.
Someone correct me if I'm wrong on that.

---

### Post by DenzilS on 2008-07-26
From your link I found [http://www.gjaeger.de/scanner/plustek/#epson](http://www.gjaeger.de/scanner/plustek/#epson) and downloaded the backend. Now I am still inexperienced in Linux, but I am an intelligent, computer literate guy, and I can't make sense of the installation instructions. Can anyone translate into something intelligible, or should I get rid of the scanner and find something easier to use?

---

### Post by Steve413z on 2008-07-26
this may seem stupid but...

I've noticed that alot of flatbed scanners, especially the new small portable LED scanners, have a little lock switch to keep it from moving on the bottom or the side, (i guess it's for when you transport it)

have you ever gotten it to work before in windows or something?

---

### Post by phidia on 2008-07-27
> **DenzilS said:**
> From your link I found [http://www.gjaeger.de/scanner/plustek/#epson](http://www.gjaeger.de/scanner/plustek/#epson) and downloaded the backend. Now I am still inexperienced in Linux, but I am an intelligent, computer literate guy, and I can't make sense of the installation instructions. Can anyone translate into something intelligible, or should I get rid of the scanner and find something easier to use?

It looks to me like you need to download the most recent sane frontend deb packages are [here]("http://packages.debian.org/unstable/graphics/sane"). You should be able to install the deb by right clicking that package and selecting the "Install with.." menu item.
And then from the link you gave: > Downloads

Latest backend-code is version 0.52-3 and can be found [here]("http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz").  Get that tar.gz file put it in you home/yourusername directory-extract it, and from a commandline-terminal window the usual method is (please check the README file though): step1; ./configure
step2; make step3; sudo make install
And that installs the driver.

---

### Post by DenzilS on 2008-07-27
@steve413z
Thanks, but it was working fine with Suse and Iscan, so I am fairly confident the scanner itself is OK, although I will check with Windows if I can.

@phidia

OK, I've installed the latest Sane package, and unpacked the plustek-sane tarball to /home/[username]. It unpacks to two folders, "doc" and "backend". I cd to the backend folder and do ./configure to be given this message

bash: ./configure: No such file or directory

Tell me if I am wrong, but ./configure requires that there is a file called "configure" in the current folder, yes? There is no configure file.:confused:

Here is a list of the files in the backend folder, if it helps.
plustek.c
plustek.conf.in
plustek.h
plustek.usb.c
plustek.usb.h
plustek.usbcal.c
plustek.usbcalfile.c
plustek.usbdevs.c
plustek.usbhw.c
plustek.usbimg.c
plustek.usbio.c
plustek.usbmap.c
plustek.usbscan.c
plustek.usbshading.c

---

### Post by DenzilS on 2008-07-28
I have established that the scanner is working fine under Windows. Anybody any ideas where I go from here, please?

---

### Post by phidia on 2008-07-28
It's been a while since I had to load drivers for a scanner, but I think you need to find the system directory the has the sane files and but those in the correct folder. From the sane page [here]("http://www.sane-project.org/man/sane.7.html"): > CONFIGURATION

       To use your scanner with this backend, you need at least two entries in
       the configuration file /etc/sane.d/plustek.conf
              [usb] vendor-id product-id
              device /dev/usbscanner

       [usb]  tells the backend, that the following devicename (here /dev/usb-
       scanner) has to be interpreted as USB scanner device.  If  vendor-  and
       product-id  has not been specified, the backend tries to detect this by
       its own. If device is set to auto then  the  next  matching  device  is
       used.
       The  following  options can be used for a default setup of your device.
       Most of them are also available through the frontend.


---

### Post by DenzilS on 2008-07-29
I seem to have it working now, by installing the Sane package from [http://packages.debian.org/unstable/graphics/sane](http://packages.debian.org/unstable/graphics/sane), and using xscanimage, either from a command line or via The GIMP and Acquire image.

The configuration file referred to was installed with the Sane package and looked OK.

Xsane just doesn't work, whichever way it is invoked.

Also, trying to install the backend from [http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz](http://www.gjaeger.de/scanner/downloads/plustek-usb-0.52-3.tar.gz) was a waste of time, because there were no installation instructions, just a bunch of C files that I don't know what to do with. I have now deleted them.

So whilst I can now scan stuff, it is a little disappointing that I have had to waste so much time on it, and that the packages installed with Ubuntu didn't work.

@phidia - thanks for helping, anyway

---

