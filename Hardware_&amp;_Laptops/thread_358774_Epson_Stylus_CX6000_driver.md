---
title: "Epson Stylus CX6000 driver"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by bozemblem on 2007-02-11
Hey everybody.  I recently purchased an Epson Stylus CX6000 Printer/Copier with support for photos and I have been unable to find any drivers for it.  Does anyone else have this printer, and if so, how did you get it to to work?  Thanks!

---

### Post by cjlemmon on 2007-04-04
i bought an epson cx6000 printer today and it works very nicely using Feisty beta.  I just plugged in the usb cable and added a connected printer from the printing configuration utility.  The printer was found and recognized. 

For scanner support be sure that libsane-extras is installed.  

```
apt-get install libsane-extras
```

Also,  i added the following two lines to   **/etc/udev/rules.d/45-libsane.rules**

```
# Epson CX-6000
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="664", GROUP="scanner"

```

This allows users other than root to access the scanner.

---

### Post by doctor bangali on 2007-05-07
> **cjlemmon said:**
> i bought an epson cx6000 printer today and it works very nicely using Feisty beta.  I just plugged in the usb cable and added a connected printer from the printing configuration utility.  The printer was found and recognized. 

For scanner support be sure that libsane-extras is installed.  

```
apt-get install libsane-extras
```

Also,  i added the following two lines to   **/etc/udev/rules.d/45-libsane.rules**

```
# Epson CX-6000
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="664", GROUP="scanner"

```

This allows users other than root to access the scanner.

I brought the printer yesterday. No such luck here unfortunately. The printer is NOT recognized by Kubuntu Feisty,  I am quite frustrated at this point of time.

---

### Post by Lopar-XL on 2007-06-01
> **bozemblem said:**
> Hey everybody.  I recently purchased an Epson Stylus CX6000 Printer/Copier with support for photos and I have been unable to find any drivers for it.  Does anyone else have this printer, and if so, how did you get it to to work?  Thanks!

[[COLOR="Green"]This thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=436777&highlight=epson+cx6000") should have the answer.  Basically, you just click on System, then Administration and then Printing...  Adding a new printer is similar to what you would do in Windows.  Double-click the New Printer icon and follow the on-screen instructions from there.  I don't know how to get the scanner to work, though.

---

### Post by Ocxic on 2007-06-03
I have the printer working in ubuntu fiesty just not the scanner yet

i got the scanner working by following the previous instructions,, i also had to install sane and libsane-extras
i also had to restart the computer after all o f this

---

### Post by uputer on 2007-07-01
Are you guys happy or satisfied with your printer now? 

Edit:  I edited my message since I found info that this printer has major problems with cartridges.  

[http://www.pacificink.com/blog/2006/10/10/epson-cx6000-ink-problem/](http://www.pacificink.com/blog/2006/10/10/epson-cx6000-ink-problem/)

I'll pass...

---

