---
title: "Epson RX580 PPD/driver"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by pwc on 2007-02-16
OK I just bought new Epson RX580 All in One printer. It is not listed in Edgy printer setup. So I downloaded PPD/Driver in tar.gz and extracted it to a pipslite-1.0.0 folder in my home directory.
How do I install the driver from here, there are no clear instructions! What are the commands I need to put into system.

thanks to anyone that knows,
pwc

---

### Post by radtek on 2007-02-16
[FONT="Comic Sans MS"]Have you checked if you have cups or gutenprint drivers already for your model? Check through the **settings-administration-printer-install new printer **list of drivers for your printer. Otherwise then check and see if there is a .ppd file already in the pipslite package and use "install driver" in **settings-administration-printer-install new printer** If not, you will probably have to compile the driver from the pipslite package. 


Make sure you have the cups & gutenprint dev packages installed through synaptic first.

Then open pipslite in a terminal and type:

```
sudo ./configure
```

then

```
sudo make
```

and if everything went well you can follow it up with "sudo install"

This might work or you can download the .rpm file and convert it to a .deb file using **alien** There is a specific command for this- I forget it offhand but it is easily found through the community docs on ubuntu.org.

```
sudo apt-get install alien
```

Convert then double click on the .deb package to install it.

Log out and back in.

Hopefully you will be most of the way there. Look around at other epson install posts and at the epson forum regarding your printer. You might need to sudo gedit (text edit) a certain file in etc/share/cups/model to get you usb settings right.

This has got me part of the way with my epson (which I hope to complete later tonight after work) If this sounds like a lot of work, it only really is if you are teaching youself how to do it as you go. Hope it works for you!
[/FONT]

---

### Post by pwc on 2007-02-17
Thanks radtek for your reply. My printer(RX580) is new model and is not listed in the Ubuntu drivers list since the Edgy release was before model hit the retail stores. I looked very carefully thru all the files in pipslite folder(there were hundreds) and did not see any ppd files. I looked at the extentions on all the files, I assume thats how you tell( files that end in .ppd). So it looks like I'll have to compile the driver from pipslite pkg, which I'll do later today and let you know how I did. As far as cups and gutenprint dev packages, it looks like they are installed even though synaptic's list is not worded exactly as yours(they came installed with ubuntu 6.10, I didn't install them).

Thanks again for your help, I'll get back in a few hours, I've got some real work to do for now.

pwc

---

### Post by pwc on 2007-02-17
OK I tried the ./configure command and after many lines of text I got a
 configure: error:  *** 'cups-config' missing, please install cups or fix your $PATH$ ***

Does anyone know what this means or what I did wrong.

Thanks, pwc

---

### Post by Brigitte Seib on 2008-03-24
I ust bought the all in on Epson RX580 and found it does not appear to work in ubuntu.
I am on Feisty 7.04
Did anybody get it to work? If yes please let me know how
Thanks
Brigitte

---

### Post by c0lin on 2008-03-31
I got the RX580 to work under Ubuntu 7.10.

I found an article stating the Gutenprint 5.1.1 supported the RX580. So I downloaded gutenprint from this link: [http://sourceforge.net/project/downloading.php?groupname=gimp-print&filename=gutenprint-5.1.3.tar.bz2&use_mirror=internap]("http://sourceforge.net/project/downloading.php?groupname=gimp-print&filename=gutenprint-5.1.3.tar.bz2&use_mirror=internap") 
After I downloaded it I moved it to /usr/bin/ then extracted it from the archive. I then navigated to the folder /usr/bin/gutenprint-5.1.3/ and ran ./configure

I received a "C compiler" error checked my config.log and found this line
/usr/bin/ld: crt1.o: No such file: No such file or directory
fixed it by running this command:
sudo apt-get install libc6-dev

Ran "sudo ./configure" and it completed successfully. I then just followed what the configure said at the end which was "make clean" then "sudo make" then "sudo make install". Once all was complete I connected my laptop to the RX580 printer, 2 seconds later it was ready to print. I printed a PDF via the default Ubuntu document viewer and it printed just fine.

---

### Post by Brigitte Seib on 2008-03-31
Thank you for you information . I considered using the new Gutenprint as well (will probably try it when installing Feisty 7.10).  
 I got the printer to work with help from the Ubuntu forum using the Epson supplied driver with program alien to convert the rpm to ubuntu.

It works and I printed a test page.

But I do not have the scanner working yet. Did you get the scanner to work? What did you do?
I have sane and xsane installed. But xsane does not find it. So I suspect I have the backend not configured correctly.

please let me know

Brigitte

> **c0lin said:**
> I got the RX580 to work under Ubuntu 7.10.

I found an article stating the Gutenprint 5.1.1 supported the RX580. So I downloaded gutenprint from this link: [http://sourceforge.net/project/downloading.php?groupname=gimp-print&filename=gutenprint-5.1.3.tar.bz2&use_mirror=internap]("http://sourceforge.net/project/downloading.php?groupname=gimp-print&filename=gutenprint-5.1.3.tar.bz2&use_mirror=internap") 
After I downloaded it I moved it to /usr/bin/ then extracted it from the archive. I then navigated to the folder /usr/bin/gutenprint-5.1.3/ and ran ./configure

I received a "C compiler" error checked my config.log and found this line
/usr/bin/ld: crt1.o: No such file: No such file or directory
fixed it by running this command:
sudo apt-get install libc6-dev

Ran "sudo ./configure" and it completed successfully. I then just followed what the configure said at the end which was "make clean" then "sudo make" then "sudo make install". Once all was complete I connected my laptop to the RX580 printer, 2 seconds later it was ready to print. I printed a PDF via the default Ubuntu document viewer and it printed just fine.

---

