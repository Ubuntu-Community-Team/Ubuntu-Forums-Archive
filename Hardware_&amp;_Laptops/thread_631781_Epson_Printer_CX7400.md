---
title: "Epson Printer CX7400"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Cris(c) on 2007-12-04
Hi guys, 

     I'm new in the Linux world. I am using Ubuntu 7.10 and I've been trying to install my all-in-one  Epson CX7450 printer. I managed to make it work (at least the printer) by using the default Epson Stylus CX7700F driver (which is the one installed by default when connecting the printer to the USB port). However, I also found the pipslite-1.0.1 file in avasys.jp site which is supposed to contain the particular driver for the CX7400 series (and so, it should also make the scan work I suppose). I follow the instructions in the INSTALL file but when doing make, I get the following output:

cristian@cristian-laptop:/opt/pipslite-1.0.1$ make
make all-recursive
make[1]: Entering directory `/opt/pipslite-1.0.1'
Making all in m4
make[2]: Entering directory `/opt/pipslite-1.0.1/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/pipslite-1.0.1/m4'
Making all in intl
make[2]: Entering directory `/opt/pipslite-1.0.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/opt/pipslite-1.0.1/intl'
Making all in libltdl
make[2]: Entering directory `/opt/pipslite-1.0.1/libltdl'
make[2]: Leaving directory `/opt/pipslite-1.0.1/libltdl'
Making all in src
make[2]: Entering directory `/opt/pipslite-1.0.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/local/lib/liblite.so\" -DRSC_PATH=\"/usr/local/etc/pipslite/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/local/share/locale\" -DPRTOPT_PATH=\"/usr/local/etc/pipslite/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/share/pipslite/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/local/lib/cups/filter\" -g -O2 -Wall -MT getstat.o -MD -MP -MF ".deps/getstat.Tpo" \
-c -o getstat.o `test -f 'getstat.c' || echo './'`getstat.c; \
then mv -f ".deps/getstat.Tpo" ".deps/getstat.Po"; \
else rm -f ".deps/getstat.Tpo"; exit 1; \
fi
getstat.c:34:18: error: ltdl.h: No such file or directory
getstat.c: In function ‘str_extract’:
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c: In function ‘get_printer_peculiar’:
getstat.c:141: error: ‘lt_dlhandle’ undeclared (first use in this function)
getstat.c:141: error: (Each undeclared identifier is reported only once
getstat.c:141: error: for each function it appears in.)
getstat.c:141: error: expected ‘;’ before ‘lib_h’
getstat.c:147: warning: implicit declaration of function ‘lt_dlinit’
getstat.c:150: warning: implicit declaration of function ‘lt_dlerror’
getstat.c:150: warning: passing argument 2 of ‘fprintf’ makes pointer from integer without a cast
getstat.c:153: error: ‘lib_h’ undeclared (first use in this function)
getstat.c:153: warning: implicit declaration of function ‘lt_dlopenext’
getstat.c:155: warning: passing argument 2 of ‘fprintf’ makes pointer from integer without a cast
getstat.c:159: warning: implicit declaration of function ‘lt_dlsym’
getstat.c:159: warning: cast to pointer from integer of different size
make[2]: *** [getstat.o] Error 1
make[2]: Leaving directory `/opt/pipslite-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/pipslite-1.0.1'
make: *** [all] Error 2


Honestly, I have no idea what is going on....could you help me understand what I am doing wrong and how I can solve the problem?

Thanks a lot for your help....

---

### Post by ZanexGt on 2007-12-06
Just bumping this thread as I am interested in buying this printer and would like to know how its used. 

Cris, did you notice that avasys has released linux drivers for this printer? You might be able to convert the RPM's to .DEB packages using Alien. 

[http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

Can anyone confirm or deny? 

Thanks

---

### Post by Cris(c) on 2007-12-06
Hey ZanetxGT,,

I already tried what you suggest... I used alien to convert the rpm file into deb one. I sort of succeeded on that, though I got lots of complains about the dependencies and more importantly I got this:

dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

What I get from this is that the rpm (or deb) will not work with my architecture (amd64). In addition, when I tried the pislite-install I got something like this:

cristian@cristian-laptop:/opt/pipslite-1.0.1$ pipslite-install
pipslite-install: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

So, I ended up keeping my old driver (CX 7700F)...Any idea about what I could do???? (by the way, I haven't been able to install the scanner...pretty much because I have no idea how!)

---

### Post by Cris(c) on 2007-12-08
Hi....can someone give me a hand in solving this problem????

---

### Post by Askeptykal on 2007-12-08
I'm stuck on this too, been working on it all day. I've tried so many things up to this point, I'm not sure quite what I did anymore, but now I can get up to printing a test page on this printer. That works okay... my problem then comes when I try to print anything else. The job just stops automatically... the properties dialog tells me that "/usr/lib/cups/filter/rastertopips failed". I checked that folder, and the reason is that there isn't a file named rastertopips. Where do I get that?

It would be a lot easier if I could get pipslite-install to work, but it won't detect the printer, even though it's plugged in, on, and the system recognizes it. I'm just tired of messing with it right now... any help?

---

### Post by froy02 on 2007-12-09
I you were able to convert to deb, try to install the i386 driver with:
dpkg  with option of "force-architecture"
If you still cannot print, install  "ia32-libs"

It's worth a try.

---

### Post by MilitantPotato on 2007-12-11
Just got this printer working on Kubuntu 7.10.
I followed[ _this guide_]("http://translate.google.com/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D142737.msg941930&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3DLunix%2BEpson%2BCX7400%2BPPD%26hl%3Den%26sa%3DG")  
 [This is the untranslated version so you can copy the commands since google translator messes them up.]("http://forum.ubuntu-it.org/index.php?topic=142737.msg941930")

The only thing I did different was use Alien to make .deb files. 
I used this command:   sudo alien -dkv --scripts pipslite-cups-1.0.1-1.i386.rpm
You can get alien via synaptic/adept.

escputil doesn't work for this printer as of yet, so no special features.

The scanner also works, but for some odd reason I need to run xsane as root.

I'll try and sort that out later.


Edit: Well, changing /dev/bus/usb/###/### to group scanner worked, so did unplugging the USB and plugging it back in.  Seems it doesn't like being used as a user unless it's been hotplugged.

---

### Post by Cris(c) on 2007-12-17
Hey guys,

    Thanks a lot for your posts. I think I figured out a simple way to make the printer/scanner work properly with Ubuntu 7.10 (my architecture is amd64). 

1) Printer. 

After some hours trying to install from source (alien did not work for me), I succeeded with the pipslite file. My previous problems (see my previous posts) were due to the lack of some packages needed to compile the file (g++, gcc, some libraries). In any case, my surprise was huge when I configure the printer using the new CX7400 ppd...this ppd turned out to be much more limited than the CX7700f one that Ubuntu installs by default! For instance, the CX7400 does not allow me to choose the quality of the printing, while CX7700f does it. In other words, I believe it is not worth trying to get the customized CX7400 ppd as the default one (CX7700f) is much more complete and flexible. 

2) Scanner

There is no need to install the iscan 2.10 file you find in avasys.jp or to try to alien the rpm. It suffices with the installation of the[ sane-backends-extra]("https://launchpad.net/ubuntu/hardy/+source/sane-backends-extras/1.0.18.12") package (you need to compile it). It runs smoothly and installs all the necessary files for the scanner to work...the only extra work you have to do is to modify the epcowa.conf file to allow for USB recognition (as described in the [guide]("http://forum.ubuntu-it.org/index.php?topic=142737.msg941930") provided by MilitantPotato). The only remaining issue is the execution of xscan as root. I tried what MilitantPotato suggested but I had no luck so far with it. Aside from this, the scanner works perfectly.

Cris.

---

### Post by Fangorn59 on 2007-12-18
I am using an Epson DX7450 on Ubuntu 7.10
Followed the instructions in the link above from Militant Potato
Used  "sudo alien -dkv --scripts pipslite-cups_1.0.1-2_i386.deb"
and " sudo alien -dkv --scripts iscan_2.10.0-1.c2_i386.deb" to load the necessary files from avsys - 
Used  "sudo chmod 0666 /dev/bus/usb/004/007" as this was where my Epson is located (gleaned from System/Preferences/Hardware Information)

I had added the libsane-extras package from Synaptic Package Manager and so to get the scanner working I added this line to etc/udev/libsane-extras.rules: 
EPSON Stylus DX7400 
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0838", MODE="664", GROUP="scanner"
just before the last line of text (LABEL="libsane_extras_rules_end")

Like Cris(c) I didn't have much success with the compiled ppd - either eklite or eksdx7400 (which are in usr/share/cups/model).  The test page printed fine but I got the same error message as Askeptykal when I tried printing from an application.  Anyway the recommended driver from Cups works just fine - mine gives me the Epson Stylus DX4800 - CUPS+Gutenprint v5.0.1 Simplified  - but I had to change the ink order to the same as my printer (CMYK) and put it on High Print Quality (from Printer Options tab) before the Test Page would come out looking like it was meant to.  With all the above I now have a working printer and scanner (it is recognised by Xsane) and the added bonus of a status monitor available in terminal by typing "ekpstm" - and it only took me a day!!!

---

### Post by MilitantPotato on 2008-02-01
I switched to the CX4800 driver.  I can't be happier now.
The only problem I have is it doesn't fully eject the paper after printing.

---

### Post by susanpenter on 2008-03-12
Following the advice I have managed to get my DX7400 printer working however I can't get the scanner sorted.  I tried to use Adept Manager to download the sane-backend-extras but it would'nt download them and said it would break something.  I downloaded them from the website but I don't know how to compile them.  I'm using Kubuntu 7.10. I thought perhaps they would only work with Hardy.

Thanks for any advice.
Susan

---

### Post by azelter on 2008-05-13
I had the scanner working out of the box in Hardy. The printer colors are still not quite right though. When I get home I'll post the drivers it's using. The was an extra sane development package I think I had to install from the repos to get the scanner working, but that was it.

---

### Post by azelter on 2008-05-14
OK the print driver (that gives the wrong colors) installed by Hardy by default is:
Epson Stylus CX7000F - CUPS+Gutenprint v5.0.2 Simplified
I will try the one recommended above and see whether that solves the color issues.
The scanner package that needed installing to get the scanner working was libsane-extras, this can be installed in Hardy by doing:
sudo apt-get install libsane-extras
The scanner side of things worked fine after installing that package.

---

### Post by azelter on 2008-05-14
OK so I tried the pipslite-cups_1.0.3-1_i386.deb generated from the rpm following the instructions on this thread. The driver I mentioned above does not give the correct colors regardles of wheather one selects RGB or CMYK or any other permutation. The eklite.ppd file gives the correct colors, but, as pointed out by Cris above the new ppd does not have almost any options. For me this is a problem as it doesn't even have letter size paper options - just A4. Thus it seems the driver is good but the two ppd files need merging in some way. Cris - what did your final ppd file look like?

---

### Post by empty_spaces on 2008-06-16
hey azelter,
thanks for the tip to get the scanner working, mine works great now.

---

