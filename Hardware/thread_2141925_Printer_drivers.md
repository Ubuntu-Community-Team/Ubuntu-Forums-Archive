---
title: "Printer drivers"
date: 2013-05-04
forum: Hardware
---

### Post by clementchiew on 2013-05-04
So guys, I new with Ubuntu and I have bought a Canon mf4750 printer. Obviously they only provided the Windows drivers. I tried running the CD with Wine but it did not work. Where do u think I can get the Linux drivers?

---

### Post by Cheesemill on 2013-05-04
The Canon website has a Linux driver you can download for that printer.

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF4750.aspx?type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF4750.aspx?type=download)

---

### Post by Mark Phelps on 2013-05-04
For future reference, Wine can NOT be used to install Windows drivers -- which even if could, would do you no good -- as Linux needs Linux drivers for the hardware, not Windows drivers.

---

### Post by pdc on 2013-05-04
Hi Clement;

you don't tell us if you are using 32bit or 64bit Ubuntu; can you tell us please

Canon supply their UFR driver for these MFseries of printers;

the latest version is 2.6 and you can get it as Cheesemill kindly pointed out;

this latest version has 64bit .deb packages; so it should install fine in Ubuntu;

if 64bit you need > [COLOR="#FF0000"]sudo apt-get install ia32-libs[/COLOR] before installing the UFR driver 

..however I think folks are also still needing some symbolic links to tell their system where to..

but I suggest you just install and see if it works firstly 

get the driver from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

it comes down as Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz

if you save it to you Downloads directory; open with archive manager; select extract and extract to your desktop; drill down to the appropriate package; right click on the COMMON (cndrvcups-common_2.60) of each pair first; select "install with gdebi installer" and then the cndrvcups-ufr2-uk_2.60 package after that

---

### Post by clementchiew on 2013-05-15
oh. thanks. im new and i thought wine help installs all windows apps. thanks for pointing that out.

---

### Post by pdc on 2013-05-15
...........as in my previous post 

> [B][SIZE=5][COLOR="#FF0000"]Hi Clement;

you don't tell us if you are using 32bit or 64bit Ubuntu; can you tell us please[/COLOR][/SIZE][/B]  :D   :D

help us to help you

---

### Post by clementchiew on 2013-05-15
thanks. i have installed the cups or sth from the software center. but i have no idea how to run them via the terminal so that it installs the contents. help me pls?

---

### Post by clementchiew on 2013-05-15
32bit. sorry.

---

### Post by pdc on 2013-05-15
well that is tremendous Clement as it should install easily for you

If I suggest some commands ....... you are happy to open a terminal??             .if so............ paste the commands in; using the menu option on the top line 

if you get the driver from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

it comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz
[/COLOR]
if you select to SAVE it as it comes down 

the commands would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]


that should make a directory called [COLOR="#0000FF"]Linux_UFRII_PrinterDriver_V260_uk_EN[/COLOR] in your Downloads directory

if you leave the terminal alone now ............ and instead go to your GUI desktop ...........

if you open that UFR directory from your desktop ..remember.......it is inside the Downloads directory ...........once you can see in it ..open the [COLOR="#0000FF"]32bit Driver[/COLOR] directory and then open the [COLOR="#0000FF"]Debian[/COLOR] directory and there should be two packages;

RIGHT-CLICK on the [COLOR="#008000"]cndrvcups-common_2.60-1_i386.deb[/COLOR] and select "install with gdebi installer" and then select the other package: [COLOR="#008000"]cndrvcups-ufr2-uk_2.60-1_i386.deb[/COLOR] and do the same

.........that should have you up and running ......

---

### Post by clementchiew on 2013-05-15
[/QUOTE] "install with gdebi installer" [/QUOTE]

no problem. erm. i cant see the gdebi installer. just open with software center or archive manager in my context menu. i have opened them in software center and installed them btw. but nth happens.

---

### Post by pdc on 2013-05-15
OK ...........so let's see what is installed

If you copy and paste the command

> [COLOR="#FF0000"]sudo dpkg -l | grep cndrvcups[/COLOR]

into a terminal............can you copy and paste back here what you get.........we are looking to see if it says ..does it detail [COLOR="#008000"]cndrvcups-common_2.60-1_i386.deb[/COLOR] and [COLOR="#008000"]cndrvcups-ufr2-uk_2.60-1_i386.de[/COLOR]b

............if those are detailed............and thus installed, ..that is good so far .........

I think we need to register the printer for you;

can you copy and paste back what you get with this command please?

> [COLOR="#FF0000"]sudo /usr/sbin/lpinfo -v[/COLOR]

to register the printer we need the command 

> [COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -p [printer name for registration] -P [PPD file path] -v lpd:[device URI] -E[/COLOR]

..tell you more later ..

---

