---
title: "Lexmark x1270 driver installation"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by aref on 2009-08-02
I am having trouble installing my Lexmark X1270 driver. I followed the steps listed in the [HOWTO: Lexmark Printers]("http://ubuntuforums.org/showthread.php?t=49714&highlight=S19cupsys"), all went well except for when I got to the step/etc/rc2.d/S19cupsys restart that restarts the driver, there was no S19supsys. Can someone tell me where to go next?
Thank you

---

### Post by dE_logics on 2009-08-02
I don't know a bit about this, but this 'x1270'...is real crap.

I mean, my chipset hosts an ATI x1270 chip..............AND there are really no drivers...man I'm pissed :(

Good thing your printer is a lot more popular than the chip and we do have the complete working drivers.

---

### Post by SunnyRabbiera on 2009-08-02
Lexmarks are crap anyway, they have crappy ink and even more crappy linux support.

---

### Post by exit_jones on 2011-02-24
Hey lovely ubunteros...  i know this is a REALLY old thread but i could not help but recognize a disparity: i found a perfect fix (i repeat, my lexnark 1270 all-in-one works **perfectly** ..scans, prints, copies (of course), and for old times' sake i put a little paper underneath it too, just cauz it still *is* a lexmark, after all.  i was *just*  given the above printer/scanner (it's 2011!) and temerously searched for a method to make it work.  the below worked 100% perfectly for me.  i found it at [http://www.ubuntu-es.org/?q=node/123309](http://www.ubuntu-es.org/?q=node/123309) and have translated it into english for my anglophone brothers and sisters.

i run ubuntu 10.04 (64-bit) and this worked well for me.  you'll need to install the library libstdc++5 --which is not in the ubuntu repositories-- as well before you can install the actual driver.  To download:

1) Open your favorite terminal emulator
(e.g., Applications >> Accessories >> Terminal)```

sudo -s
wget http://es.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb
wget http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600cups_1.0-2_i386.deb
wget http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/z600llpddk_2.0-2_i386.deb
```
2) Now let's install:

For 32-bit systems:
```

sudo dpkg-i libstdc + +5 _3.3.6-17ubuntu1_i386.deb
sudo dpkg-i z600cups_1.0-2_i386.deb
dpkg-i z600llpddk_2.0-2_i386.deb
```
For 64-bit systems there is no support, so we'll force the 32-bit driver:
```

sudo dpkg-i - force-architecture libstdc + +5 _3.3.6-17ubuntu1_i386.deb
sudo dpkg-i - force-architecture-2_i386.deb z600cups_1.0
dpkg-i - force-architecture-2_i386.deb z600llpddk_2.0
```
3) Install xsane (for the scanner):

```

sudo aptitude install sane xsane sane-utils
```
(for the above, you can use "apt-get" instead of "aptitude" if you must)

4) At this point everything worked for me.  To see if the same is true for you, you can try the following:
System >> Administration >> Printers
In the window tha opens, choose Server >> New >> Printer
(or hit ctrl + n)

5) Your system *should* detect the connected printer (the Lexmark).  Mine identifies it as "Lexmark 1200", so I click on that one.

Now select "PPD file" and enter this path:
/usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd
and continue.

If everything worked you should be able to use your printer and scanner (again, this worked for me, so I did not need to use the below method, but I'll include it for your reference.  Again, I did NOT try the proceeding method (no need).  This is what was originally done to create the .deb package above, though.

If not, here's a supplementary method:

Resume at 3) and we will continue

4') Open your terminal.
```

sudo aptitude install alien
sudo -s
mkdir lexmark
cd lexmark
```
5') Download the Lexmark z600 driver [here]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&emeaframe=&fileID=1151").
Download the file to: /home/USER/lexmark/ (where it says USER put your username)

6') Now, back in your terminal:
```

sudo -s
lexmark cd
tar xvzf CJLZ600LE-CUPS-1.0-1.tar.gz
tail-n +143 z600cups-1.0-1.gz.sh > install.tar.gz
tar xvzf install.tar.gz
alien-t-1.0-1.i386.rpm z600cups
alien-t-2.0-1.i386.rpm z600llpddk
sudo tar xvzf z600llpddk-2.0.tgz-C /
sudo tar xvzf z600cups-1.0.tgz-C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
sudo /etc/rc2.d/S50cups restart
```

(here your system might throw an error because the cups file could be named differently.  If that is the case, do the following:
```
sudo nautilus /etc/rc2.d/cups
```
and see what the filename is ((it could be s19cupsys or something else; but it should be in there.  Mine is called S04cups)),then restart cups using that name.)
```

cd /usr/lib/cups/backend
.Z600
```
You should see the following response:

direct z600: /dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"

If not, do this (I use vi instead of gedit-- use whatever file editor suits you)*:
```

sudo gedit /etc/fstab
```

Add the following line:
```

usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
```
Save that file and close it.

```

sudo mount usbfs
.Z600
```
Now it should work!

Let's go back to point 4)

System >> Administration >> Printers
Ctrl + n (etc)

*It is best practice to make a backup copy before editing files, especially critical ones.  If you delete this file, your system will no longer work.

---

### Post by JoojiSan on 2011-12-09
**[SIZE=2][B]Lexmark X1270 Series Printers**[/SIZE][/B]

 Should work with the z600 drivers. Follow the instructions for the z600 series from this link:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

