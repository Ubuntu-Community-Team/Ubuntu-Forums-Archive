---
title: "Scanner Installation"
date: 2008-05-10
forum: Hardware
---

### Post by M4rotku on 2008-05-10
Hello,

I have 1 scanner installed which was installed using the process to install a first scanner with XSane.  I need to install a 2nd scanner but I can't find the way to go about doing so.  Whenever I open XSane, it doesn't give me the option to install a scanner since I already have one.  It is an Epson Stylus XC7400 and I have the installation disk for Windows OS's.  It connects via USB and I am able to print with it.  Can anyone walk me through how to do this?

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-05-13
bump, still confused with the scanner.

---

### Post by teaker1s on 2008-05-13
supported by epson directly


[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do")

Long time since I installed my epson with this but I remember using "alien" to use the rpm file to create a deb and install

```
Sudo apt-get install alien
```

cd into the directory that contains the "rpm" file
 look here
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")

If you want to use the created "eklite.ppd" file to drive printer I will need to look where to find it, think it's in 
/usr/share/cups/model/

---

### Post by M4rotku on 2008-05-14
That confused me a lot.  Lol, I'm a noob.  I managed to download all the files i think I'll need and I managed to use alien to create the .deb file and I think I ran the .deb successfully.  However, the scanner is still not detected by XSane.  Is there a step I missed or something I may not have done correctly?

Thanks for your help

---

### Post by teaker1s on 2008-05-15
when I installed mine the epson driver configured xsane.

If the driver has installed correctly you should have "iscan" epson's own gui scanner interface.

Previously to this I had another epson printer and this needed you to modify ekowa.conf in xsane to get it to recognise it. I did this ages ago and unless things have changed with sane

run ```
sane-find-scanner
``` it should find the scanner and give use the vendor id 0x04b8(for Epson) and 0x0813 (product ID for cx6600).
      

modify the following files:
```
sudo gedit /etc/sane.d/epson.conf
``` 
(add usb statement usb 0x04b8 0x0813) the comments explain this.
```
 sudo gedit /etc/sane.d/epkowa.conf
``` (same as above)
      ```
sudo gedit /etc/sane.d/dll.conf.conf
``` make sure epkowa has been added at the end of the file. In my case I just have to uncomment it.

may be worth a look here too 
[http://ubuntuforums.org/showthread.php?t=38445]("http://ubuntuforums.org/showthread.php?t=38445")

---

### Post by M4rotku on 2008-05-15
both "epkowa" and "conf.conf" returned blank documents.

I don't know if I got the part with the installation of the deb file right.  When I tried to install the .deb file, I got: 
```
Warning: Skipping conversion of scripts in package pipslite-cups: postinst postrm
Warning: Use the --scripts parameter to include the scripts.

```

and then I tried:
```
sudo alien -k --scripts pipslite-cups_1.0.3-2_i386.deb

```

and nothing happened.  However, when I tried the:
```
sane-find-scanner

```

it returned:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:006:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

so that means that the scanner was detected, it just can't be used.

This is kinda still confusing me.  Is there any way I can use the install disk and there's someway to translate the window-ness of the install disk into something that Linux is compatable with? :confused:

This probably sounds kinda stupid, but I am just thinking that there has to be an easier way.

Thanks again for your helping me work this.

---

### Post by teaker1s on 2008-05-16
found USB scanner (vendor=0x04b8, product=0x0838) at libusb:006:002 you may want to look at "Sane" project as I believe most of your issue is that the above details need entering in sane config file. 

Also it appears things have changed in hardy heron so you should look here too
[https://help.ubuntu.com/8.04/printing/C/scanning.html]("https://help.ubuntu.com/8.04/printing/C/scanning.html")

---

### Post by M4rotku on 2008-05-17
Ok, it works now.  I guess I just needed to reboot the system after doing the other stuff you told me.  Thanks for your help, I would never have gotten this to work w/o it.

---

### Post by teaker1s on 2008-05-17
:popcorn: glad to be of help:guitar:

---

