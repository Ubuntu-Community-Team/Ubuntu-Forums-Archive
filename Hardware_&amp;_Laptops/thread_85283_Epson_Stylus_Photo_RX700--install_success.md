---
title: "Epson Stylus Photo RX700--install success"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by kurtk on 2005-11-02
Just thought I would share my success in installing the Epson Stylyus Photo RX700 all in one printer/scanner on my Ubuntu Notebook.  After googling for help on how to get the thing working and finding nothing, thought it might be usefult to someone, someday if I detailed the steps I took to get it working:

_**Printer:**_
[LIST]
Downloaded the .rpm printer file from [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) (pips-sprx700-cups-2.6.3-1.i386.rpm)[/LIST]
[LIST][*]Using Alien, installed the driver (sudo alien -di pips-sprx700-cups-2.6.3-1.i386.rpm)
[/LIST]
[LIST][*]Copied the file /usr/local/EPKOWA/SPRX700/ekpd.debian to etc/init.d calling it ekpd
[/LIST]
[LIST][*]Using ksysv, added ekpd to run levels 1 to 6
[/LIST]
[LIST][*]Start ekpd from ksysv
[/LIST]
[LIST][*]From gnome menu: system-administration-printing, added new priter, specifying the following:
[*]Driver--select Epson from Manufacturor, then immediately after the entry for 'Stylus Photo RX700' select "stylus photo series"
[*]Under connection, make sure "use a detected printer" is selected and "Photo Image Print System" is selected.
[/LIST]
You should now be able to print.

**_Scanner:_**

[LIST][*]Download Image scan from the same Avasys site (iscan-1.12.0-1.c2.i386.rpm)
[/LIST]
[LIST][*]Install with Alien. (sudo alien -di- iscan-1.12.0-1.c2.i386.rpm)
[/LIST]
[LIST][*]Follow instructions in accompanying manual and find where the scanner is connected (sane-find-scanner | grep 0x04b8 )
[/LIST]
[LIST][*]Result should return something like: "found USB scanner (vendor=0x04b8 [EPSON], product=0x0810 [USB2.0 MFP(Hi-Speed)]) at libusb:005:003" this last thing is important, enter new command to change mode of the USB port, using the address returned "sudo chmod 0666 /proc/bus/usb/005/003" (obviously the 005/003 will depend on what is returned by sane-find-scanner)
[/LIST]
You should now be able to run sane and detect the new scanner as a normal user and not have to run as root.

Hope this helps someone.

---

### Post by teaker1s on 2005-12-08
can the cx6600 be done in the same way?

---

### Post by stevebakerj on 2007-05-11
> **kurtk said:**
> 

Hope this helps someone.

Thank you, thank you, thank you, this has been driving me mad ](*,)  since I installed Kubuntu one simple change and hey presto.

Thanks again

:biggrin: :biggrin: :biggrin: :biggrin:

---

