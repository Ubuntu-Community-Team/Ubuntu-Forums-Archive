---
title: "HOWTO: Installation of Xerox Phaser 6125N printer"
date: 2009-07-05
forum: Hardware
---

### Post by kotpierdzibonk on 2009-07-05
It took me a while to find a solution so why not spread the knowledge...

How to install Xerox Phaser 6125N on Ubuntu in 12 simple steps :o)
==================================================================

1. Download Linux driver for Fuji-Xerox DPC525A:
[http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux](http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux)

2. Unpack the driver:
unzip dpc525a_linux_.0.0.tar.zip

3. Install Alien:
sudo apt-get install alien

3. Convert the RPM package:
sudo alien Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm

4. Install the converted package:
sudo dpkg -i fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb

5. Go to:
System -> Administration -> Printing
and click on 'New'

6. The printer will be properly recognized as:
Xerox Phaser 6125N <ip number>

7. Select it and press 'Forward'

8. When the window 'Choose Driver' appears select 'Provide PPD file' and click on the button below to find the file.

9. Go to:
/usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd
and click 'Open'. You are back to the previous window - click 'Forward'.

10. On the next window from 'Optional Tray Module' select '250 Sheet Feeder'.

11. Go to the next window and click on 'Apply'.

12. You can print the test page now but most probably you will have to feed the paper manually. To change that right-click on the printer and select 'Properties'. Go to 'Printer Options' and in 'Basic' section from 'Paper Source' select 'Tray 1 (250 sheets)'.

Done! Happy printing!


¡Muchas gracias Arturo!

---

### Post by binartu on 2010-06-20
Now, I'm trying to install it in a Ubuntu 10.4 64 bits but I don't do it still.

If anyone knows howto install it, please tell me.

Thanks.


Arturo.


[http://www.riveragallardo.es](http://www.riveragallardo.es)

---

### Post by luca2750 on 2010-06-26
> **binartu said:**
> Now, I'm trying to install it in a Ubuntu 10.4 64 bits but I don't do it still.

If anyone knows howto install it, please tell me.

Thanks.


Arturo.


[http://www.riveragallardo.es](http://www.riveragallardo.es)


Hi, i'm Luca
I have the same problem: xerox6125 and ubuntu 10.04 64b....
I tried to do what Kotpierdzibonk explaned...but it does not work.
Who can help me?
Thanks

---

### Post by RayVad on 2010-08-13
Guys, check my solution here:
[http://ubuntuforums.org/showthread.php?t=1552166]("http://ubuntuforums.org/showthread.php?t=1552166")

---

### Post by jeremyellman on 2010-09-19
Really useful reply. Thanks

---

### Post by dmjones63 on 2010-10-18
Works a treat in v10.10 Maverick Meerkat. Many thanks!!

---

### Post by mfrost on 2010-12-16
OK, managed to install driver as per instructions above. can print test pages and single-page pdf and doc files. but cannot print single-page odt files or any multi-page files of any format. Suggestions?



mark

---

### Post by jim.titcomb on 2011-02-23
> **mfrost said:**
> OK, managed to install driver as per instructions above. can print test pages and single-page pdf and doc files. but cannot print single-page odt files or any multi-page files of any format. Suggestions?



mark

I had the same problem, Ive just followed the advice at [http://notes.benv.junerules.com/all/software/linux-and-a-xerox-phaser-6125n/]("http://notes.benv.junerules.com/all/software/linux-and-a-xerox-phaser-6125n/")
and it is working a treat. Basicly change from socket to lpd.

---

### Post by alexcampbell2k101 on 2011-02-23
Hi

I am alexcampbell.

them We have a PC and we want to install an FTP Client on it and when a user want to upload something he goes on this PC and uplaod, so we want to keep a track of who used it, what uploads he made etc.
this is use mans guide ebook.
==============================




[Mans Guide Ebook]("http://www.plrprivatelabelrights.com/private_label_ebooks/dating_ebooks/Mans_guide/Sales_Material")

---

### Post by mcattem on 2011-03-10
Hello i have installed the printer like in the tutorial but i keep on having a problem with the paper tray when i set it on tray 1 all the time i have error no paper because he ask for paper on the manual paper feeder on the front of tray and in the printer its self its tray 2

how the chance the paper tray to 1 in the printer its self

---

### Post by drled on 2011-03-27
I have the same error (No paper)...

---

### Post by rickgt2 on 2012-01-31
Hi

For the error "No paper" or similar, I found the solution on [[COLOR="Blue"]this blog[/COLOR]]("http://www.riveragallardo.es/2009/06/instalar-xerox-phaser-6125-en-ubuntu.html")

It works for me

1. Download Linux driver for Fuji-Xerox DPC525A:
[http://www.fujixerox.com.au/support/...stemCode=Linux](http://www.fujixerox.com.au/support/...stemCode=Linux)
or
[ftp://ftp.fxa.com.au/drivers/dpc525a/dpc525a_linux_.0.0.tar.zip](ftp://ftp.fxa.com.au/drivers/dpc525a/dpc525a_linux_.0.0.tar.zip)


2. Unpack the driver:
unzip dpc525a_linux_.0.0.tar.zip

3. Install Alien:
sudo apt-get install alien

3. Convert the RPM package:
sudo alien Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm

4. Install the converted package:
sudo dpkg -i fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb

5. Go to:
System -> Administration -> Printing
and click on 'New'

6. The printer will be properly recognized as:
Xerox Phaser 6125N

7. Select it and press 'Forward'

8. When the window 'Choose Driver' appears select 'Provide PPD file' and click on the button below to find the file.

9. Go to:
/usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd
and click 'Open'. You are back to the previous window - click 'Forward'.

[B][SIZE="3"]10. On the next window from 'Optional Tray Module' select '250 Sheet Feeder'.
[/SIZE][/B]
11. Go to the next window and click on 'Apply'.

**[SIZE="3"]12. You can print the test page now but most probably you will have to feed the paper manually. To change that right-click on the printer and select 'Properties'. Go to 'Printer Options' and in 'Basic' section from 'Paper Source' select 'Tray 1 (250 sheets)'.[/SIZE]**

---

### Post by freebier on 2012-07-05
Not quite a complete newcomer to unix/linux and am old enough to have used dos but ATM linux (or at least Ubuntu) is not living up to the reputation of having drivers for everything. 

I appreciate the effort that has gone into finding these workarounds but unfortunately, this one does not work for me. I downloaded the fujitsu-xerox driver, unpacked it, installed alien but then the process failed at step 3 as alien (presumably) decided my pc was not an i386 (which it is). Not sure what is causing the problem but best guesses are that it does not recognize a dual processor or it is not compatible with Ubuntu 64 bit.

(Would I be better installing Ubuntu 32 bit overall? Not very far down the line so no great loss)

TIA

btw

---

### Post by YannBuntu on 2012-08-28
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1042747](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1042747)

Please select "Yes, it affects me" if you are affected.

---

### Post by jaxån on 2013-01-27
Ok, here is how to build a 64 bit version of this.  I uses multi-arch to support.

$ mkdir ~/XP-6125N
$ cd ~/XP-6125N
$ url -# -o dpc525a_linux_.0.0.tar_81c2.zip \
"http://onlinesupport.fujixerox.com/tiles/common/hc_drivers_download.jsp?system='Linux'&shortdesc=null&xcrealpath=http://www.fujixeroxprinters.com/downloads/uploaded/dpc525a_linux_.0.0.tar_81c2.zip"
$ # Install multi-arch support for libcups2:i386
$ sudo apt-get install libcups2:i386
$ # Unpack rpm-package using alien
$ fakeroot alien -g Fuji_Xerox-DocuPrint_C525_A_AP-1.0-1.i386.rpm 
$ cd Fuji_Xerox-DocuPrint_C525_A_AP-1.0
$ # Change #Architecture: i386" to "Architecture: amd64"  in debian/control
$ sed -i -e s/i386/amd64/ debian/control
$ # Create package and install it
$ fakeroot ./debian/rules binary
$ sudo dpkg -i ../fuji-xerox-docuprint-c525-a-ap_1.0-2_amd64.deb 

Happy printing.

---

