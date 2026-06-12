---
title: "Samsung Xpress C410W Printer and installation"
date: 2016-07-27
forum: Hardware
---

### Post by andrew237 on 2016-07-27
Hi 

I have an Xpress (SL-C410W) Samsung Laser Printer which up to now have had attached to a windows PC.  Recently I have installed Ubuntu 16.04 and I am trying to connect this printer to Ubuntu.  I have read forums which have said to install Unified Linux Driver, which I can't find on Samsung's website, however, there is a Samsung Printer Software Installer there.  Anyway I have tried downloading and extracting this program and tried installing the printer via CUPS but when I test the printer the printer does not work.  I am not sure what I am doing wrong but I am new to Ubuntu so I am wondering if I need to do something else or if I have missed something.  I connected the printer by USB and am hoping to get it wireless.

Please help.

Thank you in advance.

---

### Post by gordintoronto on 2016-07-27
This might work: run Printers (or Printing?) and select Add, or perhaps "+". Then "proceed" or "OK" or whatever moves you forward. (Sorry, I run several variants of Ubuntu, but not Ubuntu itself.)

If you want to access the printer via wireless, do not install it by USB, that will just confuse the issue. Set it up as wireless, then after "Add," select "network printer."

---

### Post by uNoubu8a on 2016-07-27
OK, go to [http://www.samsung.com/us/support/owners/product/SL-C410W/XAA](http://www.samsung.com/us/support/owners/product/SL-C410W/XAA) and click on **See More + **at the bottom of the Downloads section.  Scroll through until you see:

```
Print Driver (Driver) ver. V1.00.36_00.91 - Linux 
(MULTI LANGUAGE,14.66 MB)
```

Click on [B]DOWNLOAD (GZ)

[/B]Now extract the GZ archive where ever you can find it again... say perhaps into the Downloads folder in which you saved it originally.

Open up a terminal and navigate to where you extracted the archive.  Example let us say we extracted it to our Downloads folder. Let us also assume you extracted the archive to a folder called uld (that is typically a default for Samsung, well for my printer in any case... off course you can name it what you want).

Hit Ctrl+Alt+t
in the terminal type:

```
cd
cd Downloads
cd uld
sudo ./install.sh
```

Follow the prompts and answer the questions.  (In the long EULA you can press q to escape and then press y enter to accept...)

Now once you have this installed, run the printer config as per normal and your printer will show up and will be added.

I hope this is enough info to get you going ;)

---

### Post by kurt18947 on 2016-07-28
> **work-work said:**
> OK, go to [http://www.samsung.com/us/support/owners/product/SL-C410W/XAA](http://www.samsung.com/us/support/owners/product/SL-C410W/XAA) and click on **See More + **at the bottom of the Downloads section.  Scroll through until you see:

```
Print Driver (Driver) ver. V1.00.36_00.91 - Linux 
(MULTI LANGUAGE,14.66 MB)
```

Click on [B]DOWNLOAD (GZ)

[/B]Now extract the GZ archive where ever you can find it again... say perhaps into the Downloads folder in which you saved it originally.

Open up a terminal and navigate to where you extracted the archive.  Example let us say we extracted it to our Downloads folder. Let us also assume you extracted the archive to a folder called uld (that is typically a default for Samsung, well for my printer in any case... off course you can name it what you want).

Hit Ctrl+Alt+t
in the terminal type:

```
cd
cd Downloads
cd uld
sudo ./install.sh
```

Follow the prompts and answer the questions.  (In the long EULA you can press q to escape and then press y enter to accept...)

Now once you have this installed, run the printer config as per normal and your printer will show up and will be added.

I hope this is enough info to get you going ;)

This is what has worked for me installing a Samsung Multifunction machine. The only problem I've had on multiple installs is in one case install.sh did not work. I had to run printer.sh then scanner.sh (working from memory re file names). For my machine - Samsung Xpress 2870 - the printer driver can be installed without the Samsung download. The scanner requires the Samsung software. Your machine is just a printer albeit color, did you try printers -> add or printers -> new? Don't make things more complicated than they need to be.

---

