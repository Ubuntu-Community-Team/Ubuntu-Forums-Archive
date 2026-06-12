---
title: "Getting HP PSC 1350 to work on Ubuntu"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by DaturaX on 2005-05-10
I am trying to find linux drivers for this printer. It is a HP PSC1350 printer and scanner.

Anyone knows where to get drivers for the printer and scanner to work on linux?

Thanks

---

### Post by Calgarian on 2005-05-11
I'm working with an HP PSC 1610 right now and having some problems. The printer works, but not the scanner at the moment. There is an HP product called hplip for these devices. Here is the install guide location: [http://hpinkjet.sourceforge.net/install.php#HPLIP](http://hpinkjet.sourceforge.net/install.php#HPLIP)

Be sure to get the 0.9.2 version of hplip and follow the instructions to the letter. Don't use the Ubuntu apt version of hplip. By the way the http:/localhost:631 approach won't work so use the KDE Print Manager. Let me know how you do?

---

### Post by kamstrup on 2005-05-12
For all these HP PSC XYZ (printer and scanner in one devices), you need the hpoj driver.

To make things work, you have to do something like the following:

- Remove the printer via System-Admin->Printers

- Install hpoj like this "sudo apt-get install hpoj"

- Now it might run some configuration scripts. If it does answer "no" to scan parallel ports and "yes" to scan usb ports.

- Check if scanning now works. Don't fear if it doesn't.

- Reboot your system

- If scanning didn't work rerun the setup 
```
sudo /etc/init/hpoj setup
```

- Add a printer as follows via System->Admin->Printers: 
*** DON'T use the detected printer! Click the "Select by specifying port"-thing and select the PTAL entry.

- Try printing a test page. If it doesn't work, try rebooting and/or make sure the setup script finished succesfully.

Hope it helps! Fiddling around with this should make things tick atleast :)

---

### Post by DaturaX on 2005-05-12
```

configure: error: "cannot find libjpeg support"
configure: error: /bin/sh './configure' failed for prnt/hpijs

```

I get this error when i tried to run *./configure --prefix=/usr* on the hplip file

I've checked. both libjpeg and hpijs is installed.

libjpeg62 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.


anyone?

---

### Post by DutchLau on 2005-05-12
I think you need an appropriate C++ compiler. Do: >  sudo apt-get install build-essentials 

Now try doing the ./configure command again!

Good Luck!

DutchLau

---

### Post by DaturaX on 2005-05-12
[QUOTE=DutchLau]I think you need an appropriate C++ compiler. Do: 

Now try doing the ./configure command again!

Good Luck!

DutchLau[/QUOTE]
 I've the latest build-essential installed.

Anyway i just did a apt-get upgrade build-essential

And tried running the ./configure command but i still get the same error message.

---

### Post by kamstrup on 2005-05-12
Do you have the libjpeg62-dev package installed? I don't know if it is that it is missing..?

Good luck

---

### Post by DaturaX on 2005-05-12
[QUOTE=kamstrup]Do you have the libjpeg62-dev package installed? I don't know if it is that it is missing..?

Good luck[/QUOTE]
 thanks guys. got it to work

---

### Post by Jvaldezjr on 2005-06-27
I sent you a PM about this, but I'm curious how you got it to work exactly.  I've fooled around with the HPOJ drivers, and the HPLIP drivers, and have nto been successful.  I either get scanning funtionality, or printing, but never both.  I'm curious about what  you did to get it to work, since Sourceforge says that the PSC 1350 is fully supported.

Thanks

---

### Post by C J Pro on 2005-06-27
I am also experiencing problems with HP PSC 1350.  If anyone knows how to get an HP PSC 1350 to work over networking, please reply to [http://www.ubuntuforums.org/showthread.php?t=44365](http://www.ubuntuforums.org/showthread.php?t=44365).

---

### Post by Jvaldezjr on 2005-06-29
ok I got it to work...both scanner and printer.  Make sure you remove the printer from the system.

First...follow the instructions here:

sudo apt-get install python-dev
#Note: Install python-dev 2.3 or later.
# After the python-dev package is installed, enter this command:
sudo apt-get install libsnmp5-dev
#After the libsnmp5-dev package is installed, enter this command:
sudo apt-get install libcupsys2-dev
# After the libcupsys2-dev package is installed, enter this command:
sudo apt-get install python-qt3
# After the python-qt3 package is installed, enter this command:
sudo apt-get install lsb

Now install the HPLIP package (you can compile from source, but I ended up with some build errors I didn't know how to fix)

sudo apt-get install hplip
# Note - If you had hpoj installed before, hplip removes it.

Now restart HPLIP and CUPS
sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart

Now add your printer via KDE printer manager or GNOME print manager- which ever you prefer.
#NOTE- when you pick the driver for your printer, there is NOT a 1350 driver listed.  You'll probably see something like HP PSC 1300, 1300 hpijs, 1310, and 1310 hpijs.  I am using PSC 1300 hpijs driver.

You can try to print a test page now, you should be successful.
Try to run Kooka, or XSane, and see if a dialog box opens up to select your printer.  If not, then do the following:

sudo sane-find-scanner
This should probe your USB port and find the PSC.
scanimage -L
this will list out your scanner devices.
Rerun Kooka/XSane, and you should be able to select the PSC.

Now you can't print and scan at the same time, so if you queue up a print job, then decide to run the scanner you will have to wait until the print job is done, and vise versa.

Good luck

---

### Post by flippantfig on 2005-08-14
[QUOTE=Jvaldezjr]ok I got it to work...both scanner and printer.  Make sure you remove the printer from the system.

First...follow the instructions here:
sudo apt-get install python-dev
#Note: Install python-dev 2.3 or later.
# After the python-dev package is installed, enter this command:
sudo apt-get install libsnmp5-dev
#After the libsnmp5-dev package is installed, enter this command:
sudo apt-get install libcupsys2-dev
# After the libcupsys2-dev package is installed, enter this command:
sudo apt-get install python-qt3
# After the python-qt3 package is installed, enter this command:
sudo apt-get install lsb

SNIP!

Good luck[/QUOTE]

Hello, I need a bit of help with the PSC 1350 and printing...

I had Ubuntu Hoary printing ok prior to my fiddling, but I needed to get the scanner working. I fiddled, I followed the instructions above (oops!) and broke the printing! Stuff uninstalled, was replaced etc. Now I am looking to 'rollback' to the original set up but I am having problems. APt doesn't log by default from what I can tell so I am having difficulty getting back to the previous state as far as install goes.

The gnome-print dialogue has also got 2 entries for the HP PSC 1300 listed, how best to wipe the slate clean and start over?

Help gratefully appreciated!

---

### Post by Jvaldezjr on 2005-08-17
I would remove the printer from the system, then use synaptic to reinstall the printer drivers.  Thats all I can think of right now.  I do remember having to power cycle my printer the first time I installed it, but then it worked after that.

---

### Post by matthew on 2005-08-17
I have the HP psc 1210. While it is not the same, maybe the method I used will work for you as well, or at least add an idea that will help you. Here's a link documenting my struggle and eventual success.

[http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

EDIT: here are a couple other threads you may find helpful as well.
[http://www.ubuntuforums.org/showthread.php?t=8549](http://www.ubuntuforums.org/showthread.php?t=8549)
[http://ubuntuforums.org/showthread.php?t=4360](http://ubuntuforums.org/showthread.php?t=4360)

---

### Post by flippantfig on 2005-08-17
Thanks for the replies. I'll sort this out in due course (its my fathers PC and he dualboots so it can wait!). I'll post how I get it going for future reference too.  :)

---

### Post by flippantfig on 2005-08-18
Hello again, an update:

Printing systems were stripped out ready for a new set up.
1 uninstall cupsys and all related cups packages
2 uninstall all HP related packages
3 uninstall all foomatic related packages
4 reinstall cups
5 reinstall hpoj, get xsane running with /etc/init/hpoj setup 
6 reboot
(LPR is also not install BTW)

xsane scans using the 1350! This is progress....

But I am now stuck going round in circles. I install cupsys so that I can access the printer functions and I now need some drivers. So I go for hplip and (as apt suggests it!) hplip-data. The only thing is I have to strip out hpoj to get this in place. I therefore  lose the scanner and I still have no printer....

Any ideas? which is the best package to get 1350 printing? I have looked at the links and info supplied but I keep coming back to this same issue.

---

### Post by Jvaldezjr on 2005-08-19
Based on how I got my 1350 printing and scanning, I think your problem is using the HPOJ drivers.  You want the HPLIP ones.  Thats what I used, and had full functionality.

---

### Post by flippantfig on 2005-08-27
I must admit that the system beat me!  ](*,) 

I resorted to doing a full clean reinstall (using a Breezy snapshot which brings with it many other fun things to do!).

Once I had the system up and running, the printer worked straight off with the gnome printer setup (using hpijs drivers). I checked the scanner as root but I had no luck, BUT as a normal user everything slotted into place, and the PSC1350 does everything  it should!

Pity I had to go the distance and wipe the system, but still it works.

---

