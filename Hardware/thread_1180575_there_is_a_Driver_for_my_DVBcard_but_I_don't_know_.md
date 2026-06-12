---
title: "there is a Driver for my DVBcard but I don't know how to use it"
date: 2009-06-07
forum: Hardware
---

### Post by abushouk on 2009-06-07
hi all 

I have DVB Card named [DVB-S PCI (S420) and ]("http://www.tevii.com/product_s420.html")
there are driver for it from the company web site 
but I'm beginer in Linux word I don't know what to do whith this fie
here it is::
[http://www.tevii.com/Tevii_linuxdriver_0815.rar](http://www.tevii.com/Tevii_linuxdriver_0815.rar)
there is one file and 2 folders:
fw  howto.txt  multiproto_plus_patched_tevii_0815
 
1///HowTo.txt
```
1) unzip the multiproto_plus_patched_tevii_0815.tar.gz 
2) make and make install 
3) copy fw/dvb-fe-cx24116.fw && dvb-usb-s600.fw && dvb-usb-s650.fw >> \lib\fireware 
4) reboot pc 
```
2/// fw (fireware):
dvb-fe-cx24116.fw  dvb-usb-s600.fw  dvb-usb-s650.fw

3///multiproto_plus_patched_tevii_0815:
(mutch files and folders)
COPYING   INSTALL  mailimport  README          v4l        v4l_experimental
hgimport  Linux    Makefile    README.patches  v4l2-apps

may u ask I'm using ubuntu 9.4 kernel version 2.6.28-11-generic 

please help and sorry for my bad languages hope u understand me.

---

### Post by Chronon on 2009-06-07
It sounds like you already have the firmware files, so maybe you don't have to make and make install.  Try just putting those firmware files in /lib/firmware/ first and see if your DVB card gets recognized.

You should probably extract the .tar.gz and take a look at the INSTALL document, though.

---

### Post by abushouk on 2009-06-07
[COLOR=Blue]yes I have done that... I put the firmware files in /lib/firmware/ already and I don't know how to see if my DVB card  recognized or not howto?>>>anyway I use Kaffeine and when I begining searching for the sattlite there is chaneals apper but often in this point my CPU gest Crash or Hanging...

I had extract the .tar.gz file and the Installation document "read me"is::

```

V4L and DVB documentation are at:
    linux/Docummentation directory.

To compile both v4l and dvb, just do:
    make

To install over kernel's old files:
    make install

A more complete list of other possible usages for the building system
can be found at:
    INSTALL

if you want to contribute by offering your work to V4L/DVB, please read:
    README.patches

Notice: v4l dir is used also as a temporary dir for building v4l/dvb modules.
```

when i do "make"in the terminal apper that i need to install full source kernel i tray to install the [COLOR=#000000][COLOR=#0000BB]headers but that didn't work >>>

so i use this command beleving it ro the full source kernel 

[/COLOR][/COLOR]```
[COLOR=#000000][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get build[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]dep linux[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]image[/COLOR][COLOR=#007700]-$([/COLOR][COLOR=#0000BB]uname [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]r[/COLOR][COLOR=#007700])
[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get source linux[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]image[/COLOR][COLOR=#007700]-$([/COLOR][COLOR=#0000BB]uname [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]r[/COLOR][COLOR=#007700])  [/COLOR][/COLOR]
```

it toke time but after restartting my cpu and do make still the same problem

I'm beginer and this is my only problem after that i will surf in the linux word say byby to microsoft forever plz help me

thank u 
[COLOR=#000000][COLOR=#0000BB]

[/COLOR][/COLOR][/COLOR]

---

### Post by abushouk on 2009-06-08
anyone plz help

---

