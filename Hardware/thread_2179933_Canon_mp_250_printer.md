---
title: "Canon mp 250 printer"
date: 2013-10-10
forum: Hardware
---

### Post by KegHead on 2013-10-10
Hi!

Anyone with any luck getting the above to work w/13.10?

Thanks!

KegHead

---

### Post by swedenfox on 2013-10-11
i have a similar canon and works with canon driver (scanner + printer)

have you tried to install the official driver ?
[Canon Driver for Mp250 (italian canon website)]("http://www.canon.it/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP250.aspx?DLtcmuri=tcm:80-822896&page=1&type=download")

---

### Post by KegHead on 2013-10-11
thanks!
i'll try

---

### Post by staustelladam on 2014-07-01
Hi,

Looking to install an MP250 and before starting a thread I found this.

I've successfully downloaded the .tar from the Italian site but not sure what to do next ... any help gratefully received.

Thanks,
Adam.

---

### Post by pdc on 2014-07-01
Hi staustelladam

welcome to the ubuntu forums: do you mind if I point you to the Canon Asia site; as I am familiar with their format there?

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100236101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236101.html) and when you click to download, if you **SAVE** the file, and it will be saved to your Downloads folder; you will be downloading [COLOR="#008000"]cnijfilter-mp250series-3.40-1-deb.tar.gz
[/COLOR]
If you open a terminal; (ok with you?) and copy and paste the commands below: **_line by line_**; and hit the **ENTER** key after each paste; Canon supply an install script and it will do the work; 

[COLOR="#FF0000"]cd Downloads
tar cnijfilter-mp250series-3.40-1-deb.tar.gz
cd cnijfilter-mp250series-3.40-1-deb
./install.sh[/COLOR]

...........the install script will run and ask you a couple of questions;

_______________________

the scanner side will be driven by [COLOR="#0000FF"]ScanGearMP[/COLOR] if you wish: you can get it from here: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100237401.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100237401.html) and installs in a similar way

to run it, the crucial command in a terminal ***when you have installed it***.......................is................ > [COLOR="#FF0000"]scangearmp[/COLOR]

buona fortuna!

---

### Post by staustelladam on 2014-07-02
Hi,

Thanks for this.

I managed to run a terminal session, and got as far as the second line and nothing happened. I then decompressed the file so that I had a new directory with the name of the third line and tried again, but getting to the install.sh bit I got the following message:

"An error occurred. The package management system cannot be identified.
adam@KLaptop:~/Downloads/cnijfilter-mp250series-3.40-1-deb$ "

Thanks,
Adam.

---

### Post by pdc on 2014-07-02
it is said this message > An error occurred. The package management system cannot be identified. is because the install script finds evidence of an rpm package in the system: it should all be deb packaging

........ anyway..........if you open a terminal and paste this command

> cd /Downloads/Canon Drivers/cnijfilter-mp250series-3.40-1-deb/packages

then have your sudo password ready for the install of the 2 packages you need:

................oh..............you don't say which bit version you have .......................32bit?

---

### Post by staustelladam on 2014-07-02
Sorry, 32 bit.

In the packages folder I have four files, and presumably I want:cnijfilter-mp250series_3.40-1_i386.deb

Looking inside that there are more files, but I don't know what's next. Do I need to decompress that file or can I just use terminal to install, and if so, how do I do that?

Thanks again ... I will get it eventually :)

Adam.

---

### Post by pdc on 2014-07-02
Hi Adam; so if you go

> [COLOR="#FF0000"]cd /Downloads/cnijfilter-mp250series-3.40-1-deb/packages[/COLOR] 

then once inside that directory .........

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-common_3.40-1_i386.deb[/COLOR]

(Canon say install the common package first)..........then 

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-mp250series_3.40-1_i386.deb[/COLOR]

........and that should have it installed .........

___________________

explanation: you need the sudo password to "do" things ie change/delete/install etc dpkg is addressing debian packages and the -i signifies install and if you type > man dpkg it tells you the many options that are around dpkg

---

### Post by staustelladam on 2014-07-03
Hiya,

I got through all of those steps, up until: sudo dpkg -i cnijfilter-mp250series_3.40-1_i386.deb

I then got the following message:

"(Reading database ... 579122 files and directories currently installed.)
Preparing to unpack cnijfilter-mp250series_3.40-1_i386.deb ...
Unpacking cnijfilter-mp250series (3.40-1) over (3.40-1) ...
dpkg: dependency problems prevent configuration of cnijfilter-mp250series:
 cnijfilter-mp250series depends on libtiff4; however:
  Package libtiff4 is not installed.

dpkg: error processing package cnijfilter-mp250series (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 cnijfilter-mp250series
adam@KLaptop:~/Downloads/cnijfilter-mp250series-3.40-1-deb/packages$ "

Noticing that libtiff4 was missing I went and installed that, ran the steps again, got the same error message so restarted the computer. Going through the steps again the error is still there ... so ... do I need to do something to make the computer recognise libtiff4 is installed?

Thanks,
Adam.

---

### Post by pdc on 2014-07-03
thanks Adam 

so what does 

> dpkg -l | grep libtiff4 give you please if you copy and paste into a terminal?

---

### Post by staustelladam on 2014-07-04
This is what I get, with the bold red text:

adam@KLaptop:~$ dpkg -l | grep libtiff4 
ii  **[COLOR=#ff0000]libtiff4[/COLOR]**-dev:i386                                           4.0.3-7ubuntu0.1                                    i386         Tag Image File Format library (TIFF), transitional package
adam@KLaptop:~$

I went through and applied all updates that were pending, restarted the machine, tried all the steps you suggested earlier, got the same results about libtiff4 being absent, and finally this step with the above result. I even went via the Ubuntu software centre and reinstalled libtiff4, did everything again, all with the same results.

Do you think I may have something installed that conflicts with the file? I haven't installed too many applications ...

Thanks,
Adam.

---

### Post by pdc on 2014-07-05
thanks; >  libtiff4-[COLOR="#FF0000"]dev[/COLOR]:i386

you have only got a development package installed: 

Debian still stock the pure strain of libtiff4 and you can get it here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)

scroll down below all the libtiff4-dev packages and choose the [COLOR="#008000"]libtiff4-3.9.6-11_i386.deb[/COLOR] package; 

re-run the install script after installing libtiff4

---

### Post by staustelladam on 2014-07-06
Hi,

Thanks for that. I installed the libtiff4 files, ran through the installation procedure again, and everything seemed to succeed. However, I'm not quite sure what happens next ... the printer shows up when I want to print documents, but I don't seem to have any way of configuring the printer as an independent piece of hardware. In Windows (yes, I know :) ) it was simply a matter of settings/hardware/printers/add printer, or something along those lines ... I can't find a similar task in KDE/Ubuntu.

Thanks,
Adam.

---

### Post by pdc on 2014-07-06
> but I don't seem to have any way of configuring the printer

.........I'm not sure what you want to do:

there are various ways to tweak; click on this link [http://localhost:631/printers/](http://localhost:631/printers/)  .....it should list options: there may be a gutenprint entry for your MP250 and a Canon driver (saying something like version 3.6 or something..........)

If you left-click on the left column, you should be able to alter settings;

another way is paste > system-config-printer in a terminal and the window that opens should have printer entries: is that helpful?

---

### Post by staustelladam on 2014-07-07
Hi,

Thanks, that's the sort of thing I was looking to see ... although there aren't that many options it is still very helpful.

Thanks again,
Adam.

---

### Post by pdc on 2014-07-07
You can get the manual: go here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

find your model; click on manuals

If you download the linux printer guide [http://support-asia.canon-asia.com/contents/ASIA/EN/0300277201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300277201.html)

you will find the command > [COLOR="#FF0000"]cngpijmonmp250 MP250[/COLOR]          .............set up a launcher if you repeatedly want to tinker .............

_________________________

best you download the guide: best you read through it; best you work it all out; best you come back and tell us what you learn; Ubuntu is a community of volunteers!!

---

### Post by Cinderboot on 2014-07-07
Not sure if this helps, but I have the MP 250 installed on both 12.10 and 13.04.
I'm using the gutenprint drivers (comes with kubuntu).

PS: Remember that the 13 series of [k]ubuntu makes printers "offline" or "disallowed" by default which I think is stupid... Correct me if I'm wrong, I'm not sure if they changed that in 13.10.


I just found out how to make it print in draft mode!!!
Advanced options->Resolution->600x600 draft

---

