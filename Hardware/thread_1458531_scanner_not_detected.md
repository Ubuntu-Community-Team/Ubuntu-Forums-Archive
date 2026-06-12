---
title: "scanner not detected?"
date: 2010-04-20
forum: Hardware
---

### Post by teeliina on 2010-04-20
hi all. I have an interesting problem: I can't scan. I've got ubuntu 9.10 fresh install and a Canon Pixma mp270, and I have installed the drivers for printing &scanning available on the canon au-site. Printing works fine.
 If I try to scan via gimp, it tells me that available scanner not found. check cable and power. but everything is fine there. nothing happens if I hit the scan button. I have connected via usb.

If I try to scan via xsane, it will try to scan through some other device, I think its the videocard since there's an old tv-card inside the computer (this is and old media center machine).:confused:

so, how do I change the default scanner for xsane? how do I make it find the correct device? I'm quite sure that this is the origin of the problem...
I'm quite a newbie with technical stuff, so simple intructions please :D

---

### Post by khelben1979 on 2010-04-20
I checked [this thread]("http://ubuntuforums.org/archive/index.php/t-166944.html") and now I'm wondering if you get more devices to choose from with your [XSane]("http://en.wikipedia.org/wiki/Xsane") application if you run it as root. Have you tried this?
```
sudo xsane
```

---

### Post by teeliina on 2010-04-21
that seems not to be the problem, since then xsane opens like normally. with the code or not. The title of xsane when opened is the device mentioned below.  but I did sane-find-scanner
it said ' no scsi scanner found. usb scanner was (probably) detected. it may or may not be supported by xsane.' then did the terminal proposed scanimage -L and the result was 'v4l:/dev/video0 is a Noname Hauppage WinTv 34xxx models virtual device.' I wonder what that is??? not my scanner, that I can understand... Terminal also suggested to read the backends manpage, but I don't know what that means.
 Again, I think xsane is using the wrong device for scanning. how to change that? I haven't found an add a scanner box anywhere....?

---

### Post by khelben1979 on 2010-04-21
First off, let's examine what device your Linux system reports about your usb scanner by looking at some output from your usb ports:
```
lsusb
```
Post your output in this thread.

---

### Post by teeliina on 2010-04-21
here's what I got when I did that:
:~$ lsusb
Bus 001 Device 004: ID 04a9:173b Canon, Inc. 
Bus 001 Device 002: ID 059b:0470 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 55aa:b012 OnSpec Electronic, Inc. Mitsumi FA402M 8-in-2 Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the canon inc is my printer, iomega an external hd, rest is a mystery to me. but what was then the device given by the scanimage -L command?

---

### Post by khelben1979 on 2010-04-21
It definitely looks like your scanner is not detected.

---

### Post by dabl on 2010-04-21
> **teeliina said:**
> 

there's an old tv-card inside the computer 



Yes, I had the same problem with a Hauppauge PVR card.  It is detected as an "optical" device, and the detection seems to stop at that point.  After I was finished with my VCR tape conversion project, I pulled the PVR card and the scanner was detected correctly again.  One would not think that a PCI card would interfere with something plugged on the USB bus, but ......

I would try pulling that TV card.

Also, you might need to install a package that is named "libsane-extras".  It extends the list of scanner backends.

---

### Post by teeliina on 2010-04-22
Ok. I will try that tomorrow, then I can get some experienced assistance with the finding& removing of the Hauppage card and putting everything back together again in correct order. I have the tendency of losing small items like screws :D
I will post the outcome here anyway.
one more question, what would the lsusb output be after removing the hauppage card, since that canon inc device is both printer and scanner?and will xsane then open labelled 'canon pixma mp270 scanner' or something?

---

### Post by teeliina on 2010-04-25
Sorry it took this long to get back to business. (enter here 3 of your favourite excuses)

Gentlemen, we have victory. I can now scan through Gimp. Removing the tv-card really did it. To Gimp there appeared an option in File/Create/ Scangear Mp...  which previously wasn't there and my scanner works. 

However, the victory is still partial, since xsane won't find my scanner, root or not it will not open, just says now 'no devices found'. I downloaded the libsane-extras, but that didn' do the trick. my xsane is version 0.996 -maybe updating it could help? 

All in all, I'm ready to call this problem solved, since the real issue of not being able to scan at all is solved! the quality of canon's scangear-image is sufficient. Thank you both for the help!! :D

---

### Post by desertdog on 2010-07-02
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)


Edit:
Actually, this is a better link to get your scanner working:

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

This blog tells how to download and compile the latest sane source code.

---

### Post by gmarcotte on 2012-04-11
I found a deb package from what looks like canon here:

[http://cweb.canon.jp/cgi-bin/download/select-product-by-catg.cgi?i_cd_pr_catg=011](http://cweb.canon.jp/cgi-bin/download/select-product-by-catg.cgi?i_cd_pr_catg=011)	

then selected the model and then here:
[http://cweb.canon.jp/cgi-bin/download/select-os.cgi](http://cweb.canon.jp/cgi-bin/download/select-os.cgi)	

and then here
[http://cweb.canon.jp/cgi-bin/download/select-software.cgi](http://cweb.canon.jp/cgi-bin/download/select-software.cgi)	
down loaded these but ended up installing the deb files directly. 

it creates a program that you can run from the command line:
scangearmp

the program will scan one page at a time (no multi pdf files). after installing this the normal programs descuss above still cant find the scanner. the program that they provide is a bit brain dead non standard unko, but it atleast I can scann a document in so my printer scanner is not a waste of money. 

I wish some one would hit these companies that not every one uses winblows, and there is a standand USB scanner API that they could use.

I am using ubuntu 12.04 hopefully updates will fix this problem.

---

