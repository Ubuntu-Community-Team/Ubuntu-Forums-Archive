---
title: "Brother &quot;QL-570&quot; Label Printer"
date: 2009-06-23
forum: Hardware
---

### Post by Atsuko on 2009-06-23
I have one of these and would like to use it on my Linux box so would anyone know if there is a driver for it or have one working on Ubuntu?
[QL-570](http://www.brother-usa.com/labelprinter/modeldetail.aspx?PRODUCTID=QL570)

---

### Post by celem on 2009-07-31
Brother says that they supply a driver/procedure. I'd be curious as to how well it works. Please advise if you try. See:
[http://tinyurl.com/mk9tx5]("http://tinyurl.com/mk9tx5")

---

### Post by earlra on 2009-11-02
I have one and just installed it in 9.10 and it is working just fine.  I followed the procedures on:
[http://solutions.brother.com/linux/en_us/instruction_esp1.html](http://solutions.brother.com/linux/en_us/instruction_esp1.html)

---

### Post by kirkhoward on 2009-12-04
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html#QL-570](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html#QL-570)

I am running ubuntu 9.04.  Most instructions I found are for 8.04/8.10.

Ubuntu 8.04/8.10 [Before Instructions: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#201]](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#201])
1. "sudo aa-complain cupsd" command is required before the installation.
2. "sudo mkdir /usr/share/cups/model" command is required before the installation.

sudo dpkg -i --force-all ql570lpr-1.0.0-1.i386.deb
sudo dpkg -i --force-all ql570cupswrapperinch-1.0.0-1.debian.i386.deb

* Completes with errors, but if you go to PRINTER CONFIGURATION in GNOME, you can find your QL-570, go to properties, and select the DEVICE-URI (usb://Brother/QL-570 )as it is already recognized.

Uninstall, Reinstall, Select Driver from list.  Seems to work after messing with it.  Seem to be able to ignore most of the errors if (in gnome PRINTER CONFIGURATION) you delete the printer, unplug, plug, install, go to driver area, find the QL-570, and it should work.  I had to delete the printer in GNOME a few times before I got the procedure just right.

As a note, I did receive the following errors during the install process, and it still worked fine after the delete-printer/reinstall/select driver process.

sudo dpkg -i --force-all ql570lpr-1.0.0-1.i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `ql570cupswrapperinch' missing, assuming package has no files currently installed.
313436 files and directories currently installed.)
Preparing to replace ql570lpr 1.0.0-1 (using ql570lpr-1.0.0-1.i386.deb) ...
Unpacking replacement ql570lpr ...
Setting up ql570lpr (1.0.0-1) ...
mkdir: cannot create directory `/var/spool/lpd/ql570': No such file or directory
chown: cannot access `/var/spool/lpd/ql570': No such file or directory
chgrp: cannot access `/var/spool/lpd/ql570': No such file or directory
chmod: cannot access `/var/spool/lpd/ql570': No such file or directory

sudo dpkg -i --force-all ql570cupswrapperinch-1.0.0-1.debian.i386.deb
Selecting previously deselected package ql570cupswrapperinch.
(Reading database ... 313436 files and directories currently installed.)
Unpacking ql570cupswrapperinch (from ql570cupswrapperinch-1.0.0-1.debian.i386.deb) ...
Setting up ql570cupswrapperinch (1.0.0-1) ...
 * Restarting Common Unix Printing System: cupsd                                                                             [ OK ] 
lpadmin: Bad device-uri "brusb_ql570:/dev/usb"!
/var/lib/dpkg/info/ql570cupswrapperinch.postinst: 4: /etc/init.d/cupsys: not found
dpkg: error processing ql570cupswrapperinch (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ql570cupswrapperinch

---

### Post by robfantini on 2010-04-16
thank you.

---

### Post by Ongytenes on 2011-01-03
I followed the instructions provided by Brother's website. But I had to go in and create some of the directories individually since they were nested one inside another. After that my QL-570 printer started to blink red every time I tried to print to it. I tried several label settings to no avail.  I was using a continuous roll, but when I switched it for a roll of fix labels it went to working. I never was able to get that roll to work. I thought I would pass that bit of info along. 

The directories I made manually were..
/var/spool/**lpd**    &   /var/spool/lpd/**ql570**

The install was having trouble making the directory **ql570** because it's parent directory** lpd** didn't exist either.

---

### Post by dkesh on 2011-07-11
[FONT=Arial][SIZE=2]Once the driver is installed, what kind of application software do you use to print labels to the QL-570?  I am using Ubuntu 10.10 64bit.[/SIZE][/FONT]

---

### Post by celem on 2011-07-11
> **dkesh said:**
> [FONT=Arial][SIZE=2]...what kind of application software do you use to print labels to the QL-570?...[/SIZE][/FONT]

Amazon.com has a post for this printer that says that PayPal can print USPS postage labels via PayPal and java. 
Seems like that should work for Linux although I haven't tried it.

```

4.0 out of 5 stars Great printer, confusing setup, August 27, 2008
By V. Kailas "antonio" (dc) - See all my reviews
(REAL NAME)   
This review is from: Brother QL-570 Professional Label Printer (Office Product)
Great label printer. Fast, reliable, and quiet. A bit bulky but the size makes it easy to change the label. 

Note about setting up printer for postage: 
I bought this printer to print folder labels and postage. Folder labels was easy enough but postage proved difficult. 
I read on a forum that you could print USPS click and ship postage. Signed up on USPS and spent a few hours trying to 
fit the postage image onto the label. Finally, a search revealed that paypal has this functionality. I signed into paypal 
and under Profile -> shipping settings set the printer settings to ql-550 (ql-570 not listed but it's okay). It gives 
you a heads up that you need Java(TM) 2 Runtime Environment to print labels to your label printer and points to you a 
link for the no longer unsupported J2SE JRE from 2005 that no longer works. You do need Java Run Time Environment but 
can use the newer one. You can get it by searching for JRE or get the older one by searching J2SE JRE. 

Then I went into Label Printing Application found under Aution Tools tab -> PayPal MultiOrder Shipping and printed 
two labels. Wasted about 1 foot of labels trying to get them to print. Then finally realized there is another setting 
inside this MultiOrder Shipping App under Edit -> Settings. I set this to the ql-550 and hit the "Reprint" button (next 
to View Details...) under the History tab. I wasted another foot of continuous label trying to print the labels. Then 
realized that reprinting keeps the original printing formatting. Had to void out the labels and /really/ re-print them 
(luckily I didn't have to refill in the shipping details). Very annoying experience. end rant. 

1. Download Java http://www.java.com/en/download/index.jsp 
2. Create or login your Paypal Account 
3. Click auction tools -> free MultiOrder Shipping 
4. If Getting Started pops up click Close 
5. Click Edit -> Settings -> Print Settings -> Label Printer, and choose ql-550. (Also I unchecked packing slips and receipt.
   Packlist comes up after printing labels and you can choose your regular printer) 
6. Click Ok 
7. You are done. Click File -> Create New Order 

Also, turn off pop-up blocker before trying to print and you might want to change your OS's "Printer Preferences" paper 
size to the correct value so you don't have to do this everytime you print. The default is wrong for the ql-570. 

This is a big feature for the ql series so they should have some better documentation but it is equally paypals fault for 
poor documentation.


```

---

### Post by dkesh on 2011-07-13
[FONT=Arial][SIZE=2]I use the printer for normal address and mailing labels.  I may just have to connect it to the other PC, which is still a Windows box.  I got the driver to load for the printer under Ubuntu, but there is no software I can find that is anything like the P-Touch editor or address book, which makes the printer essentially useless to me.

If anyone knows of any alternative label printing software that will work for this printer, I would really appreciate knowing about it.

Thanks!
[/SIZE][/FONT]

---

### Post by maxmojo53 on 2011-07-26
> **dkesh said:**
> [FONT=Arial][SIZE=2]Once the driver is installed, what kind of application software do you use to print labels to the QL-570?  I am using Ubuntu 10.10 64bit.[/SIZE][/FONT]

According to the Brother site 64bit is not supported :(

---

### Post by astrobob.tk on 2012-02-03
I landed here while wondering if it works on Linux so I can get one.
I did not go through the posts, but thought the following links might help:

[http://www.websale.tv/1/post/2011/11/brother-multi-function-and-label-printers-in-linux.html](http://www.websale.tv/1/post/2011/11/brother-multi-function-and-label-printers-in-linux.html)
[http://www.websale.tv/1/post/2011/12/printing-barcode-labels-with-the-brother-ql-570-using-linux-and-amazon.html](http://www.websale.tv/1/post/2011/12/printing-barcode-labels-with-the-brother-ql-570-using-linux-and-amazon.html)

Hope it helps you & please update us in the thread so others can (including me) benefit! :D

cheers

---

