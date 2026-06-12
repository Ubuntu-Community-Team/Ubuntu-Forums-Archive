---
title: "Ubuntu and Epson Stylus (NX-415)"
date: 2009-09-14
forum: Hardware
---

### Post by countryjake on 2009-09-14
I do not know where this will work for other epson stylus, but i have it working perfectly with the nx-415 printer and scanner! here is how to do it:

Go to this webpage: [http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)
on the left side press All-in-ones
Go towards the bottom and select the option with NX-415 in it
Go to the bottom and select your distribution and other options

Now, download the corresponding .ppd file for your printer (for nx-415 it will be [COLOR=Black][Epson-Stylus_NX415-pipslite-en.ppd]("http://javascript%3Cb%3E%3C/b%3E:Dl_File%28%27P000000844%27%29;")[/COLOR])
```

sudo cp /path/to/file/DRIVER_NAME.ppd /usr/share/cups/model
cd /usr/share/cups/model
sudo chmod 644 DRIVER_NAME.ppd

```Now download the SOURCE FILE for PIPSLite (the rpm and deb files DO NOT WORK!!!!)
```

tar xvfz /path/to/file/pipslite_1.4.0-5.tar.gz (make sure this is the right name! pipslite might be updated by the time you read this)
cd path/to/folder/pipslite_1.4.0-5
./configure --prefix=/usr
make
sudo make install
sudo /etc/init.d/cups restart

```Now plugin the printer and stop ubuntu from adding it using the printer GUI
go to [http://localhost:631/admin](http://localhost:631/admin)
Select Find a Printer
Epson Stylus NX-415 should show up (might be called Nx-410) and select it
Another screen will show up with printer name, etc, just press continue as they should already be filled out
It will ask for a driver, browse to /usr/share/cups/model and select your .ppd file
Congratulations! It should now be installed! Go to Printers and try printing a test page! If the printer makes some funny noises and nevers installs, just cancel it, reset the printer and take the paper out and reload it, now try again and it should work!

Scanner:
Go back to the same page where you downloaded the source file and the ppd, go to the bottom and download iscan_2.21.0-6_i386.deb or iscan_2.21.0-6.ltdl7.i386.deb and open it. Now the scanner should work with all scanning programs including xSane and your newly installed iScan program

---

### Post by radioraheem on 2009-09-14
I actually found another guide elsewhere online with similar instructions to yours, and of course I finished it (and got the printer working!) less than a few minutes before I got an email about your thread post  :-)   lol

Thank you anyway, and I'm sure someone will find this useful when they run into the same issue.

---

### Post by radioraheem on 2009-09-14
I forgot to ask, did you by any chance get the scanner working?  I started playing around with it but didn't get very far, just wondering if you had used a particular source file.

Thanks again!

---

### Post by countryjake on 2009-09-14
yes it was extremely easy to get the scanner to work! (and i forgot that part in my thread so i will edit it now!

---

### Post by radioraheem on 2009-09-15
Ahhh, cool, thank you!  I wasn't sure if I would need to recompile iscan after the first steps or not.

---

### Post by countryjake on 2009-09-15
nope, and did that work for you? luckily IScan will install using the .deb file and doesnt need to be compiled from the source

---

### Post by bluemanfu on 2009-10-22
I am having the same problem with Epson nx415,  What and where is "iscan"???  I need o get my scanner working.
thanks

---

### Post by radioraheem on 2009-10-22
Follow all of the instructions above as you need to get the first part installed before you can install the iscan package.  The iscan deb files can be found on the same pages that you will download the other files from.

> **bluemanfu said:**
> I am having the same problem with Epson nx415,  What and where is "iscan"???  I need o get my scanner working.
thanks

---

### Post by bluemanfu on 2009-10-22
That fixed my problem both printer and scanner are working fine.  
Thanks a bunch

---

### Post by jman405 on 2010-01-08
This post helped me get my NX-415 up and running.  I also had the problem of only being able to scan as root, but with the help of these two posts:

[http://forums.gentoo.org/viewtopic-p-3311185.html#3311185](http://forums.gentoo.org/viewtopic-p-3311185.html#3311185)
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

I was able to create a custom udev rules file:

```

cat /etc/udev/rules.d/45-sane-scanner.rules
# Permissions for EPSON Stylus NX415
BUS=="usb", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0851", MODE="664", GROUP="scanner"

```

Then I had to restart udev and add myself to the scanner group.  The last piece was cycling power on the printer so that the new udev rule would be applied.

---

### Post by DanFoxDavies on 2010-03-05
Attempted to use the source on a 64 bit 9.10 with an Epson Stylus SX415 - the make command ended up with this:

```
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../src/filter-l2/magick    -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -I../../lib-l2 -I../../src/filter-l2/ -g -O2 -Wall -MT l2filter.o -MD -MP -MF .deps/l2filter.Tpo -c -o l2filter.o l2filter.c
l2filter.c:45:25: error: cups/raster.h: No such file or directory
l2filter.c:68: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c:76: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c: In function &#8216;main&#8217;:
l2filter.c:125: error: &#8216;cups_raster_t&#8217; undeclared (first use in this function)
l2filter.c:125: error: (Each undeclared identifier is reported only once
l2filter.c:125: error: for each function it appears in.)
l2filter.c:125: error: &#8216;cups_ras&#8217; undeclared (first use in this function)
l2filter.c:126: error: &#8216;cups_page_header_t&#8217; undeclared (first use in this function)
l2filter.c:126: error: expected &#8216;;&#8217; before &#8216;header&#8217;
l2filter.c:137: error: &#8216;header&#8217; undeclared (first use in this function)
l2filter.c:188: warning: implicit declaration of function &#8216;cupsRasterOpen&#8217;
l2filter.c:188: error: &#8216;CUPS_RASTER_READ&#8217; undeclared (first use in this function)
l2filter.c:201: warning: implicit declaration of function &#8216;cupsRasterReadHeader&#8217;
l2filter.c:204: warning: implicit declaration of function &#8216;convert_cups_to_jpeg_1st&#8217;
l2filter.c:228: warning: implicit declaration of function &#8216;resize_jpeg&#8217;
l2filter.c:252: warning: implicit declaration of function &#8216;cupsRasterClose&#8217;
l2filter.c: At top level:
l2filter.c:779: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
l2filter.c:1202: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
make[3]: *** [l2filter.o] Error 1
make[3]: Leaving directory `/home/danfox/.epson/pipslite-1.4.0/src/filter-l2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/danfox/.epson/pipslite-1.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/danfox/.epson/pipslite-1.4.0'
make: *** [all] Error 2
```help?

---

### Post by DanFoxDavies on 2010-03-11
Problem solved - SX415 works with CUPS SX405 & SANE SX410 drivers.

---

### Post by malibusurfer2 on 2010-03-12
I have an Epson NX-415 installed and working, but Jaunty thinks it is a new printer and tries to add it every time I turn it on. I have to cancel the add printer screens in order to use the existing printer. Any ideas?

---

### Post by addux on 2010-03-30
I don't recommend installing this printer driver (although the scanner portion worked for me) because it is lacking in any features for controlling printer quality or any other more advanced features one might need.  Instead try this: [http://ubuntuforums.org/showthread.php?p=9048839#post9048839](http://ubuntuforums.org/showthread.php?p=9048839#post9048839)

---

### Post by scuba_suit on 2010-05-11
this information is very useful. i downloaded the .ppd file for my epson stylus nx415. i have gutsy. after i dl it what next? i see the code you posted and i entered it in the terminal, but to no avail. is there a specific directory i have to dl the .ppd file to? i'm a noob on this and i would really like my printer to work on my computer (i currently have it hooked up but does not print anything, the computer recognizes it as "Epson Stylus NX410", if anyone could post step by step on how to install it after dl please let me know, thanx a bunch.

---

