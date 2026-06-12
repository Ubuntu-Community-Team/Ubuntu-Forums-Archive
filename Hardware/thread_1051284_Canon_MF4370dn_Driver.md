---
title: "Canon MF4370dn Driver"
date: 2009-01-26
forum: Hardware
---

### Post by trungd_t on 2009-01-26
Hi all,

Does anyone knows if there's a driver for this multifunction model? I just realized, after purchasing the unit, that there's no Linux support for it. I searched this forum and googled the net, but have come to dead end. I've read about Linux drivers provide abroad (Asia and Europe), but still this model is not available. 

I don't want to return this unit and get another, because I really like it. It works very well and has everything I need, including duplex and networking. Is there any work around to make the unit work with Linux (e.g. Wine)? In the meantime, I'm printing via Windows, and it's working fine. 

Hope Canon realize the growing number of Linux users out there and provide corresponding drivers update.

Thank you,
Trung

---

### Post by Francewhoa on 2009-04-19
openprinting.org doesn't not have a driver yet for the Canon model MF4370DN. When available it will be posted on the following page. This is all their Canon printer drivers available for Ubuntu:

[LIST]
[*][http://openprinting.org/printer_list.cgi?make=Canon](http://openprinting.org/printer_list.cgi?make=Canon)
[/LIST]
 
List of Canon supported printers on wiki.ubuntu.com:

[LIST]
[*][https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon)
[/LIST]
 
Related pages:

[LIST]
[*][http://www.linuxquestions.org/questions/linux-software-2/canon-mf4370dn-drivers-700077/](http://www.linuxquestions.org/questions/linux-software-2/canon-mf4370dn-drivers-700077/)
[*][http://forums.linux-foundation.org/read.php?25,8335](http://forums.linux-foundation.org/read.php?25,8335)
[/LIST]

---

### Post by trungd_t on 2009-05-04
Hey thanks Onopoc. I saw your other posts and have also searched those links. I went to Canon.com and gave them a piece of my mind about not being Linux friendly :D. Next step, call support and give them hard time about the same Hehe.

I took my laptop to work the other day, and it automatically detected three HP printers on the network. I was so happy to be able to just select the printer and everything printed nicely.

With Canon, I'm :((.

Thanks man.

---

### Post by Francewhoa on 2009-05-23
I can confirm that the Canon driver works for another model (Canon ImageCLASS MF4270): [*HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver.*]("http://ubuntuforums.org/showthread.php?t=1140724")

---

### Post by trungd_t on 2009-06-21
> **Onopoc said:**
> I can confirm that the Canon driver works for another model (Canon ImageCLASS MF4270): [*HOWTO: Install Canon ImageCLASS MF4270 Multifunction driver.*]("http://ubuntuforums.org/showthread.php?t=1140724")

Onopoc,

Thanks a lot for the help. I've installed the Canon MF4100 Series UFRII LT ver.1.8, and with the USB connection, the printing works fine. However, the networks printing doesn't even works.

---

### Post by Francewhoa on 2009-06-23
Same here. I'm using USB connection. Never tried Network connection.

---

### Post by trungd_t on 2009-07-24
Hi Onopoc,

Are you able to get the scanning function to work in Ubuntu? I've been searching but no success. I tried to install the supplied scangear and toolbox from the CD using wine. Both installed fine, and in fact, the scangear even works. However, the toolbox failed to come up saying it can't register the Start key. If I can just some how get past this point, the software might come up and scan may just work.

If you have any information, please let me know.

Thanks,
Trung

---

### Post by Francewhoa on 2009-07-25
@trungd_t: Nope. Never tried scanning with the printer.

---

### Post by kmauser on 2009-07-31
I see your comments are relatively recent.  Has anyone attempted the scanning features yet?  I'm interested to know because I want to set up a Ubuntu network and really like the MF4370dn - but having the print and scan feature working is a must.

---

### Post by quackeroni_pizza on 2009-08-22
I can't speak for scanning on 4370, but I've got scanning to work on the 4150...

Details here:[http://ubuntuforums.org/showthread.php?t=878966](http://ubuntuforums.org/showthread.php?t=878966)

Hope the instructions help.. the more recent xsane distribution might already be packaged to work with the scanner...

---

### Post by haruska on 2009-08-26
I can confirm this works on 64-bit Jaunty through the network on a MF4370dn.

To get it working, just "alien" the *.rpm files in the 64-bit folder and install the resulting debian packages. When the new printer dialog asks you what driver you want, provide the PPD file described above.

Thanks a ton!

---

### Post by kss18 on 2009-09-17
I found the linux printer driver for the Canon MF4370dn on the Canon Singapore site: [http://support-sg.canon-asia.com/](http://support-sg.canon-asia.com/) 

Both RPM and Debian binaries and sources are available under the download section. After I installed the deb packages, it showed up in CUPS and works beautifully. The complete URL for the drivers page for this printer: 

[URL="http://support-sg.canon-asia.com/P/search?category=Multifunctional+Printers&series=ImageCLASS&model=imageCLASS+MF4380dn%2FMF4370dn%2FMF4350d%2FMF4320d&menu=download&filter=0"]http://support-sg.canon-asia.com/P/search?category=Multifunctional+Printers&series=ImageCLASS&model=imageCLASS+MF4380dn%2FMF4370dn%2FMF4350d%2FMF4320d&menu=download&filter=0
[/URL]
Do post here if anyone can use the network fax or scan functionality like the Windows clients are able to.

krishna

---

### Post by tworthenn on 2009-10-20
Onopc's June 29, 2009 procedure for MF4270 also works well for Canon ImageClass MF4350d on UBUNTU 9.04. Even better that now there's a specific driver listed for the MF4350d. Kudos to CANON!! 
Printer was on sale at FRY's this weekend for $100. (Now if I can just get the scanner and Fax to work)
Regards to all and thanks to Onopc.

---

### Post by ant_999 on 2009-11-08
did anyone get MF4350d work on Karmic 9.10 (fresh karmic installation, not upgrade)?

I tried to install it, but it complaints about libcupsys2 (this package is obsolete in 9.10).
I also tried to install it from source.  Ubuntu is able to recognize the driver but wasn't able to print?

---

### Post by your imaginary friend on 2009-11-17
I solved this [the dependency issue in 9.10] by modifying the tutorial at [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248) for the 4370dn:

First, I downloaded and extracted the drivers as described previously in this thread.

Then open up a terminal and go to the Downloads folder:
```

cd Downloads/Canon_UFRII_Linux_V1.90_EN/32-bit_Driver/Debian/
dpkg-deb -x cndrvcups-common_1.90-1_i386.deb common
dpkg-deb --control cndrvcups-common_1.90-1_i386.deb 
cd DEBIAN/
gedit control

```Then change the depends line to read libcups2 instead of libcupsys2, and save.

copy the entire** DEBIAN** folder into **common**.

Then:
```

cd ../
dpkg -b common cndrvcups-common_1.90-1_i386.deb

```Once you've rebuilt the deb, you can install them normally.  I have this printer working  on 32 and 64 bit machines.

---

### Post by ant_999 on 2009-11-18
Nice, got it work 
thanks a lot

> **your imaginary friend said:**
> I solved this [the dependency issue in 9.10] by modifying the tutorial at [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248) for the 4370dn:

First, I downloaded and extracted the drivers as described previously in this thread.

Then open up a terminal and go to the Downloads folder:
```

cd Downloads/Canon_UFRII_Linux_V1.90_EN/32-bit_Driver/Debian/
dpkg-deb -x cndrvcups-common_1.90-1_i386.deb common
dpkg-deb --control cndrvcups-common_1.90-1_i386.deb 
cd DEBIAN/
gedit control

```Then change the depends line to read libcups2 instead of libcupsys2, and save.

copy the entire** DEBIAN** folder into **common**.

Then:
```

cd ../
dpkg -b common cndrvcups-common_1.90-1_i386.deb

```Once you've rebuilt the deb, you can install them normally.  I have this printer working  on 32 and 64 bit machines.

---

### Post by dobedeux on 2009-12-04
Works like a charm.  

Thanks friend!

---

### Post by jccann on 2009-12-07
[QUOTE=your imaginary friend;8337773]I solved this [the dependency issue in 9.10] by modifying the tutorial at [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248) 

THANK YOU for the workaround to fix the Canon control file bug.  

Version 1.90 driver is working for my MF4100

Anyone know how to report this to the Canon developer team?

---

### Post by bertmanphx on 2010-01-27
> **haruska said:**
> I can confirm this works on 64-bit Jaunty through the network on a MF4370dn.

To get it working, just "alien" the *.rpm files in the 64-bit folder and install the resulting debian packages. When the new printer dialog asks you what driver you want, provide the PPD file described above.

Thanks a ton!

Haruska,
This has been unsuccessful for me.  I tried the same thing, but get an error -

"src = libcanon_pdlwrapper.c, line = 511, err = 0(strange symbol)nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2"

Any idea?

---

### Post by bertmanphx on 2010-02-02
> **trungd_t said:**
> Onopoc,

Thanks a lot for the help. I've installed the Canon MF4100 Series UFRII LT ver.1.8, and with the USB connection, the printing works fine. However, the networks printing doesn't even works.


Hello,
Did you ever get network printing to work on this model?

I've tried the 1.90 and 2.00 versions of this driver, and keep getting an error when trying to print via the network.

bertmanphx

---

### Post by seajayf on 2010-03-10
> **bertmanphx said:**
> Hello,
Did you ever get network printing to work on this model?

I've tried the 1.90 and 2.00 versions of this driver, and keep getting an error when trying to print via the network.

bertmanphx

I got the 4370 to print on the network with the URF ver. 2. but haven't got scan to work yet (haven't tried real hard)

---

### Post by bertmanphx on 2010-03-11
seajayf,
I have not tried to scan to it.  From what I've read, people have been successful when using this printer connected via USB.  scanning by network, may be dependent upon the back-end in sane?  Not sure.



bertmanphx

---

### Post by ridgeland on 2010-03-11
I didn't see this thread before I started a new one about the MF4350d.  I got the printer and scanner working.  I never got the printer going with 64 bit 9.04, so I installed 32 bit 9.04 and it was fine.  Lots of detail in my thread.
[http://ubuntuforums.org/showthread.php?t=1427330]("http://ubuntuforums.org/showthread.php?t=1427330")
Our MF4350d is connected to my wife's 32 bit laptop.  Using our home network I can print to the MF4350d from my Ubuntu 9.04 which is 64 bits, no drivers were installed on my PC.

---

### Post by your imaginary friend on 2010-05-26
> **ridgeland said:**
> I didn't see this thread before I started a new one about the MF4350d.  I got the printer and scanner working.  I never got the printer going with 64 bit 9.04, so I installed 32 bit 9.04 and it was fine.  Lots of detail in my thread.
[http://ubuntuforums.org/showthread.php?t=1427330]("http://ubuntuforums.org/showthread.php?t=1427330")
Our MF4350d is connected to my wife's 32 bit laptop.  Using our home network I can print to the MF4350d from my Ubuntu 9.04 which is 64 bits, no drivers were installed on my PC.

Ridgeland, does this work for network scanning?

Using UFRv2 on my 64bit ubuntu 10.04 works for network printing but not scanning.  It looks likes ridgeland's solution is for usb scanning only.  Can anyone confirm?

---

### Post by ridgeland on 2010-05-27
I have a MF4350d.  I think the "dn" models are network ready. The MF4350d only works as a USB printer through the PC that hosts it.  We use printer sharing PC to PC, not router to printer.  I don't see any way to share the scanner the way the printer is shared.  Anyone doing that?

---

### Post by cyberkost on 2010-06-08
your imaginary friend, I'm struggling making my Canon D480 print on 64-bit 10.04.  It installs ok, cups sends the file, but I'm getting this in /var/log/cups/error_log:
```
E [08/Jun/2010:23:30:39 -0400] [Job 17] src = libcanon_pdlwrapper.c, line = 512, err = 0¥nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2
```
.. and nothing ever comes out of the printer.  Any words of wisdom?

> **your imaginary friend said:**
> Ridgeland, does this work for network scanning?

Using UFRv2 on my 64bit ubuntu 10.04 works for network printing but not scanning.  It looks likes ridgeland's solution is for usb scanning only.  Can anyone confirm?

---

### Post by cyberkost on 2010-06-09
tried USB printing (the above was network printing) -- does not print with the same error message in var/log/cups/error_log

---

### Post by your imaginary friend on 2010-10-06
Hi Cyberkost,

Using v2.00 drivers (had v1.9 in prev post, i think) all i did was alien the 64bit rpm.  worked beautifully.

> **cyberkost said:**
> your imaginary friend, I'm struggling making my Canon D480 print on 64-bit 10.04.  It installs ok, cups sends the file, but I'm getting this in /var/log/cups/error_log:
```
E [08/Jun/2010:23:30:39 -0400] [Job 17] src = libcanon_pdlwrapper.c, line = 512, err = 0¥nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2
```
.. and nothing ever comes out of the printer.  Any words of wisdom?

---

### Post by cyberkost on 2010-10-06
I got v2.1 drivers when they become available and everything works now (including network printing) ... still need to figure out scanning though

---

### Post by jbachman on 2010-10-13
I'm having the same scanning issue as everyone else. I went through and installed the sane backend and had no luck with getting it to work so far.

If only canon would come to our aid and give us something to make it work.

---

### Post by skeezer65134 on 2011-01-07
Thanks haruska! Just got the driver working on my 64-bit 9.04 install. Old, I know, but it's stable so I haven't wanted to mess with it.

All I did was use alien to convert the 2 RPMs in the 64-bit_Driver/RPM and dpkg -i them both. Then I added the printer (from System > Administration > Printing) and chose to provide my own PPD file. I used **/usr/share/cups/model/CNCUPSMF4390ZK.ppd** specifically as it claimed to cover 4360-4390 models. Printed the test page and a PDF and it worked like gangbusters!

No attempts at scanning, just excited that I got it printing and thought I'd give input as to exactly which PPD file to use (took a little trial and error on my end). HTH someone.

---

### Post by deuscapturus on 2011-02-25
I just updated to Ubuntu 10.10 and the alien install of cups-common-2.20-1.x86_64.rpm and cndrvcups-ufr2-uk_2.20-2_amd64.rpm no longer works.  Building from source still doesn't work.

I now get the error 

```
src = libcanon_pdlwrapper.c, line = 512, err = 0¥nDEBUG: Wrote 1 pages...
```

If anybody finds a solution please post it.

---

### Post by paterick on 2011-03-10
I think some libraries (to satisfy the dependencies of some canon supplied binary libraries) are missing. Try

$ sudo apt-get libc6-i386 install ia32-libs lib32z1

---

### Post by fusion71 on 2011-08-04
I want to confirm Patrick's post above  to install libc6-i386 and ia32-libs before the 64 bit aliened drivers  will work (I have a MF4350d).    Had the same error as @*[I]deuscapturus*[/I]  on Ubuntu Lucid & Natty x64 ie
 "src = libcanon_pdlwrapper.c, line = 512, err = 0¥nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2"
 which was fixed once the above 32bit libraries were installed.  Also  of the 4 entries which appear when adding the printer via the CUPS web  interface ([http://localhost:631/admin/](http://localhost:631/admin/)), I chose
 Canon MF4320-4350 (UFRII LT) CNUSB #1 (Canon MF4320-4350 (UFRII LT)).   It won't print if you accidently chose the fax connections!

---

### Post by your imaginary friend on 2012-04-16
**UPDATE for Ubuntu Precise 12.04:**

Using alien on the RPM driver packaged worked for me through Natty and Oneiric (Ubuntu 11.04 and 11.10) but DOES NOT currently work on Precise (Ubuntu 12.04).

I'm using an up-to-date fresh install of the Precise beta and neither the older drivers (v2 and 2.2) nor the most recent ones (v 2.4) work. I'm not sure why :S

The drivers themselves seem to install fine, and I can add the printer, but when I go to print it fails, with this status message:
```
Idle - /usr/lib/cups/filter/pstoufr2cpca failed
```

Any suggestions?

---

### Post by Lu Timdale on 2012-04-29
Yes, same problem here with 4270.

I tried using the binary versions of the debs and following the instructions here:
[http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/]("http://queleimporta.com/installing-canon-imageclass-mf4270-on-ubuntu-64-bit/http://")
However, there is the cupsys issue.  I think the library got renamed or something.

I created alien version of 64-bit .deb files.  This installs fine, but then get 
```
Idle - /usr/lib/cups/filter/pstoufr2cpca failed
```
when printing a test page.

Any ideas appreciated.  

Thanks.

Lu

---

### Post by ridgeland on 2012-04-29
See Post #80 here
[http://ubuntuforums.org/showthread.php?t=1427330&page=4](http://ubuntuforums.org/showthread.php?t=1427330&page=4)

Worth a try.

---

### Post by omegamormegil on 2012-11-24
Printing with an imageCLASS D420 and similar printers works on Ubuntu 12.04 and 11.10 using the instructions in the first post on this thread:

[http://ubuntuforums.org/showthread.php?t=1427330](http://ubuntuforums.org/showthread.php?t=1427330)

---

### Post by your imaginary friend on 2012-12-24
Thanks to the previous few posts, I've been able to piece together the details to get the MF4370dn working on Ubuntu 12.04 (64bit).

I will recap the entire process using the latest drivers (v2.50):
[LIST=1]
[*]BE SURE TO UNINSTALL (PURGE) ALL PREVIOUS VERSIONS OF THE DRIVER AND REMOVE THE PRINTER USING THE GUI:
```
sudo apt-get purge cndrvcups-common cndrvcups-ufr2-uk
```
[*]Get the drivers from [http://support-au.canon.com.au/contents/AU/EN/0100270808.html]("http://support-au.canon.com.au/contents/AU/EN/0100270808.html")
[*]Open a terminal window.
[*]If you don't already have Alien installed, do it now. This will allow us to convert RPM packages to DEB packages, which we will need to do to properly install the drivers.
```
sudo apt-get install alien
```
[*]You may also need to install some dependencies:
```
sudo apt-get install libc6-i386 ia32-libs lib32z1
```
[*]Go to the Downloads directory and extract the drivers:
```

cd ~/Downloads
tar -xzf Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz

```
[*]Navigate to the 64-bit driver directory:
```

cd Linux_UFRII_PrinterDriver_V250_uk_EN/64-bit_Driver/RPM/

```
[*]Create the .deb packages from the .rpm ones, using alien:
```

sudo alien -ck cndrvcups-common-2.50-1.x86_64.rpm
sudo alien -ck cndrvcups-ufr2-uk-2.50-1.x86_64.rpm

```
[*]Create symlinks to 64-bit libraries:
```

sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64

```
[*]Install the drivers:
```

sudo dpkg -i cndrvcups-common_2.50-1_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.50-1_amd64.deb

```
[*]Configure apparmour to allow printing (need to do this as root):
```

sudo -i
echo "/usr/lib64/cups/backend/cnusb Uxr," >> /etc/apparmor.d/local/usr.sbin.cupsd
echo "/usr/lib64/cups/filter/pstoufr2cpca Uxr," >> /etc/apparmor.d/local/usr.sbin.cupsd
exit

```
[*]Restart cups and exit the root shell:
```

sudo service cups restart

```
[*]Add the printer using the gui: launch the Printing application from the Unity dash and add a printer, following the prompts along the way.
[/LIST]

---

