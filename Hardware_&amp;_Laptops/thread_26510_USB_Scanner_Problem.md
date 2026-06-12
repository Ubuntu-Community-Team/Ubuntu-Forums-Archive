---
title: "USB Scanner Problem"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by Svip on 2005-04-13
The problem is quite simple, I can't seem to add the scanner, as the title says it's an USB Scanner.

Model Number: MD 4394

Can anyone help? Ask any questions ( related to the subject ).

---

### Post by Gianni Exile on 2005-04-13
What is the output of the command "lsusb"?

Did you unpack the required firmware as mentioned in the sane-gt68xx manpage?


----------
Works with override "artec-ultima-2000". Maybe Artec Ultima 2000 E+ clone? If your scanner has product id 0x4003, use the artec_eplus48u backend instead.
-- [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

$ man sane-gt68xx 

FIRMWARE FILE
       You need a firmware file for your scanner. That’s a small file contain&#8208;
       ing  software  that will be uploaded to the scanner’s memory. It’s usu&#8208;
       ally named *.usb, e.g.  PS1fw.usb.  It comes  on  the  installation  CD
       that  was provided by the manufacturer, but it may be packaged together
       with the installation program in an .exe file. For Mustek scanners, the
       file can be dowloaded from the gt68xx backend homepage. For other scan&#8208;
       ners, check the CD for .usb files. If everything else fails,  you  must
       install  the Windows driver and get the firmware from there (usually in
       the windows/system or system32 directories).  Put  that  firmware  file
       into  /usr/share/sane/gt68xx/.   Make sure that it’s readable by every&#8208;
       one.

---

### Post by Svip on 2005-04-13
Thanks, I'll try that when I get home. ( at school now )

And no, I didn't knew about the man pages. :(

---

### Post by accuser on 2005-04-13
When you say you can't seem to add the scanner, what do you mean?

I presume that you have plugged the scanner in (and either it has its own power supply, or you have plugged it into a powered usb port/hub) and that when you start XSane you are informed that no devices are available. If not, what were you expecting?

Have you [checked](http://www.sane-project.org/sane-backends.html) that your scanner is supported?

---

### Post by Svip on 2005-04-13
[QUOTE=accuser]When you say you can't seem to add the scanner, what do you mean?

I presume that you have plugged the scanner in (and either it has its own power supply, or you have plugged it into a powered usb port/hub) and that when you start XSane you are informed that no devices are available. If not, what were you expecting?

Have you [checked](http://www.sane-project.org/sane-backends.html) that your scanner is supported?[/QUOTE]
What I mean is that it's plugged in and self supplied with power. But when I use that scanner program in Ubuntu; it seems not to find it or something. :|

---

### Post by Svip on 2005-04-13
[QUOTE=Gianni Exile]What is the output of the command "lsusb"?

Did you unpack the required firmware as mentioned in the sane-gt68xx manpage?


----------
Works with override "artec-ultima-2000". Maybe Artec Ultima 2000 E+ clone? If your scanner has product id 0x4003, use the artec_eplus48u backend instead.
-- [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

$ man sane-gt68xx 

FIRMWARE FILE
       You need a firmware file for your scanner. That’s a small file contain&#8208;
       ing  software  that will be uploaded to the scanner’s memory. It’s usu&#8208;
       ally named *.usb, e.g.  PS1fw.usb.  It comes  on  the  installation  CD
       that  was provided by the manufacturer, but it may be packaged together
       with the installation program in an .exe file. For Mustek scanners, the
       file can be dowloaded from the gt68xx backend homepage. For other scan&#8208;
       ners, check the CD for .usb files. If everything else fails,  you  must
       install  the Windows driver and get the firmware from there (usually in
       the windows/system or system32 directories).  Put  that  firmware  file
       into  /usr/share/sane/gt68xx/.   Make sure that it’s readable by every&#8208;
       one.[/QUOTE]
 Well, as I know now the lsusb returns this:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I found my device on the sane-gt68xx's website, but I need an ePlus2k.usb arcoding to that site. And it doesn't seem to be on the disc, there is an Artec48.usb on the disc.

Are there any commands that would help me? And please tell in detail how to do it. :(

These are the files;
svip@sviphandle:/mnt/cdrom0 $ find */*.usb
Win2000/Artec48.usb
Win98/Artec48.usb
WinME/Artec48.usb
WinXP/Artec48.usb

---

### Post by raphandmon on 2005-09-28
Hi to get the Artec E+48u scanner working (which is what the medion scanner you have really is), you need to copy the firmware file from the CD, Artec48.usb.  DOsen't matter where you put it, but I generally put it in etc/sane.d for simplicity.

You then need to gedit etc/sane.d/artec_eplus48u.conf, as root. 

Got to the line 25 (approx)
# option artecFirmwareFile........

remove the # and add in the path of the file you have just copied, i.e.

option artecFirmwareFile /etc/sane.d/Artec48.usb

Save the .conf file and X-sane will now work fine.  The scanner is ready in sane already, you just needed the firmware file.

---

### Post by cts on 2005-11-29
off-topic but Hoary5.04 runs our ancient hp 5200C scanner, and none of our Windows boxes (98,2000) will see it. 
Strike 1 for Linux!
It took a few minutes to find **xsane**
and** lsusb,** **sane-find-scanner**
nb **scanimage -L** may intefere with xsane?
maybe its actually attempting a scan?

---

### Post by Roadrunner777 on 2005-12-15
Raphandmon, Thank you for taking the time to document this, your solution worked perfectly for me, probably saved me hours.

Thanks again,
Phil

---

### Post by Second_Player on 2006-04-13
i did everything like he said and it still wont work, my guess is because i'm using a mac, but i dont really know, put it on line twenty five, copied it to the sane.d folder, everything, still didnt work

---

