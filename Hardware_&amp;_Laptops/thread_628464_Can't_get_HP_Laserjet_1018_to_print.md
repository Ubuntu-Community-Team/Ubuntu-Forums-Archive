---
title: "Can't get HP Laserjet 1018 to print"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by aquavitae on 2007-12-01
My HP laserjet 1018 won't print.  According to cups its printing fine, but it isn't.  The printer is just silent.  I've only just installed it, but it works on my sister's computer (feisty) and it has paper in it so its not the printer.  Anyone got any idea what the problem could be?

---

### Post by erginemr on 2007-12-01
Hello,

This is strange. HP line of printer products are well supported under Ubuntu and the following page:

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

reports it working under Linux. (There is also a script to install its firmwares there for problematic systems.)

Odds are your usb slot may not be functioning well. Can you see the printer when you issue "lsusb" from the console?

---

### Post by aquavitae on 2007-12-01
Ok, I plugged it back into my sister's computer, printed something to make sure the printer was still ok, then back into my computer. Now it works. Sounds dangerously like something that would happen in windows!  Anyone know why this would happen?

---

### Post by aquavitae on 2007-12-01
> **erginemr said:**
> Hello,

This is strange. HP line of printer products are well supported under Ubuntu and the following page:

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

reports it working under Linux. (There is also a script to install its firmwares there for problematic systems.)

Odds are your usb slot may not be functioning well. Can you see the printer when you issue "lsusb" from the console?

Yes, I tried that.  Anyway, it automatically installed the printer when I plugged it in so it must have seen it.

---

### Post by kavoura on 2007-12-02
I have been trying to get a friend interested in Linux, and recently she bought a HP Laserjet 1018 printer. It works perfectly in Windows XP Pro on her laptop. However, some parts  of XP do not work well, e.g. the sound. So I booted her laptop with into Ubuntu 7.04 (live CD) which loaded up well and quickly. The sound was perfect. The internet worked through her broadband router. 
But when trying to print, it would not work. I opened the printer control panel and selected New Printer, it found the HP 1018 and I added it to the printers and made it the default printer. But when trying to print to it, nothing happened. Ubuntu seemed to show the print job being sent, but the printer remained silent. It was still turned on, the green power light was no, but nothing happened to suggest that it was receiving any data, and the paper did not go through and nothing was printed.
I figured that a HP printer would work in Ubuntu, after having already read that HP put their drivers into the Linux kernel some time ago.
So it should have worked.
I notice that aquavitae could not get it to work, and then when plugging the printer back in it worked.
When I get the chance, I will try that. And probably next time take Ubuntu 7.10 on a live CD to boot from. If it will not print, I will disconnect and reconnect the printer, but if it should still not work, what else could I try? Is there anything in Ubuntu that needs to be set to ensure that printing works okay?

---

### Post by erginemr on 2007-12-03
> **kavoura said:**
> I have been trying to get a friend interested in Linux, and recently she bought a HP Laserjet 1018 printer. It works perfectly in Windows XP Pro on her laptop. However, some parts  of XP do not work well, e.g. the sound. So I booted her laptop with into Ubuntu 7.04 (live CD) which loaded up well and quickly. The sound was perfect. The internet worked through her broadband router. 
But when trying to print, it would not work. I opened the printer control panel and selected New Printer, it found the HP 1018 and I added it to the printers and made it the default printer. But when trying to print to it, nothing happened. Ubuntu seemed to show the print job being sent, but the printer remained silent. It was still turned on, the green power light was no, but nothing happened to suggest that it was receiving any data, and the paper did not go through and nothing was printed.
I figured that a HP printer would work in Ubuntu, after having already read that HP put their drivers into the Linux kernel some time ago.
So it should have worked.
I notice that aquavitae could not get it to work, and then when plugging the printer back in it worked.
When I get the chance, I will try that. And probably next time take Ubuntu 7.10 on a live CD to boot from. If it will not print, I will disconnect and reconnect the printer, but if it should still not work, what else could I try? Is there anything in Ubuntu that needs to be set to ensure that printing works okay?

If you are trying to convince her to install Ubuntu in her computer eventually, not and just use the Live CD whenever necessary, then I would recommend you to try running the script given in the following page to get the HP LaserJet 1018 Printer working:

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

It says reboot afterwards to put the changes in effect, but since you will try this from a Live CD, you cannot reboot else you will lose all changes. So, I believe restarting the cups printing daemon only will do:

sudo /etc/init.d/cupsys restart

If it works, it will surely work when installed to the hard drive.

---

### Post by hporter on 2007-12-08
You should write following commands in the terminal:

 wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1018
sudo make install
sudo make install-hotplug

that`s all
hporter

---

### Post by stchman on 2007-12-13
> **aquavitae said:**
> My HP laserjet 1018 won't print.  According to cups its printing fine, but it isn't.  The printer is just silent.  I've only just installed it, but it works on my sister's computer (feisty) and it has paper in it so its not the printer.  Anyone got any idea what the problem could be?

I have a script to automate the process of getting the Zenographics based printers working in Ubuntu.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Select the script for your distro.

---

### Post by msiner on 2008-01-03
The 1018 does not carry its own firmware in memory.  Because of this, the client computer must load the firmware each time the printer is turned on.  The HP Windows drivers take care of this on Windows.  That is why using it with Windows, leaving it on, and then using it with Linux can sometimes work.  The best way to interface with these products is by using HP's open source HPLIP software which handles this hotplugging issue.  If you look at the HPLIP supported device database, the 1018 needs HPLIP version 2.7.10+, while Gutsy ships with at 2.7.7 version.  I simply downloaded the automated installer from the HPLIP sourceforge site and ran it.  It will uninstall confilcting packages and install dependencies using apt-get.  After installing it runs a device check routine and you are done.  I have my 1018 working with Gutsy right now.

---

### Post by stchman on 2008-01-15
> **msiner said:**
> The 1018 does not carry its own firmware in memory.  Because of this, the client computer must load the firmware each time the printer is turned on.  The HP Windows drivers take care of this on Windows.  That is why using it with Windows, leaving it on, and then using it with Linux can sometimes work.  The best way to interface with these products is by using HP's open source HPLIP software which handles this hotplugging issue.  If you look at the HPLIP supported device database, the 1018 needs HPLIP version 2.7.10+, while Gutsy ships with at 2.7.7 version.  I simply downloaded the automated installer from the HPLIP sourceforge site and ran it.  It will uninstall confilcting packages and install dependencies using apt-get.  After installing it runs a device check routine and you are done.  I have my 1018 working with Gutsy right now.

When you install the driver I specified in my webpage.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

CUPS then loads the firmware to the printer each time the PC is turned on.

---

### Post by asafche on 2008-01-30
after we tryed to compile this driver under your instructions we got this.


daniel@daniel-desktop:~/foo2zjs$ make
#
# Dependencies...
#
      ***
      *** Error: /usr/include/stdio.h is not installed!
      ***
      *** Install Software Development (gcc) package
      *** for Ubuntu: sudo apt-get install build-essential
      ***
make: *** [all-test] Error 1

does anyone knows what to do?

asaf

---

### Post by erginemr on 2008-01-30
It seems you need to install the meta-package "build-essential", which envelops tools to develop basic programsunder Linux:
```
sudo aptitude install build-essential
```

---

### Post by sadeghi on 2008-03-07
> **hporter said:**
> You should write following commands in the terminal:

 wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1018
sudo make install
sudo make install-hotplug

that`s all
hporter

THANK YOU!

---

### Post by tedrampart on 2008-03-13
I've tried the above foo script, and it worked in dapper... however, it doesn't print with gutsy on our new system..

when I run cups from localhost, it sees the printer after I've installed it, and when I print a test page, it reports that it failed: "/usr/lib/cups/backend/lpd failed", or ipp as well..

I don't know what to think, as the printer worked great before plugging it into the new computer..

---

### Post by mlyons16 on 2008-03-18
> **stchman said:**
> I have a script to automate the process of getting the Zenographics based printers working in Ubuntu.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Select the script for your distro.

> **hporter said:**
> You should write following commands in the terminal:

 wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1018
sudo make install
sudo make install-hotplug

that`s all
hporter

> **msiner said:**
> The 1018 does not carry its own firmware in memory.  Because of this, the client computer must load the firmware each time the printer is turned on.  The HP Windows drivers take care of this on Windows.  That is why using it with Windows, leaving it on, and then using it with Linux can sometimes work.  The best way to interface with these products is by using HP's open source HPLIP software which handles this hotplugging issue.  If you look at the HPLIP supported device database, the 1018 needs HPLIP version 2.7.10+, while Gutsy ships with at 2.7.7 version.  I simply downloaded the automated installer from the HPLIP sourceforge site and ran it.  It will uninstall confilcting packages and install dependencies using apt-get.  After installing it runs a device check routine and you are done.  I have my 1018 working with Gutsy right now.

Hey, ya... same trouble. I'm gonna try each of these solutions. I really love Ubuntu and I'm getting used to that you have to get a bit technical to get stuff all working, but it would be really refreshing, and probably attract more users if this was all more seamless.

---

### Post by mlyons16 on 2008-03-18
[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

From the last suggestion, I went here and downloaded it.. how do I cd to the download directory, namely my desktop?

---

### Post by scottro on 2008-03-18
I vaguely remember having trouble with this printer that was fixed by using the 1100 drivers.  This was a couple of years ago and may no longer be relevant.

---

### Post by kavoura on 2008-03-18
I got it to work by using the script
```
cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0
```

I then put this into /etc/rc.local so that it runs at startup.
Now the PC can print to the LaserJet 1018 without any further messing around, it just works.

Such a pity that HP, who have done a lot to advance Linux, so I read, could not make the LaserJet 1018 work first time with any Linux installation; instead of which we have lots of users who are trying to figure out why it will not work. Compare this to my Brother HL-5150D laser. I just plugged it into the PC running Ubuntu and Ubuntu recognised it right away and let me print to it without any messing around or loading extra drivers, etc. Better at recognising printers than earlier versions of Windows ever were.

---

### Post by mlyons16 on 2008-03-19
So what is really the best way of doing this? There's a few options I've seen. I think I'm gonna start by installing the HP toolbox or something.

---

### Post by rickrich on 2008-03-27
Driver: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)
Follow ALL instructions.

---

### Post by mlyons16 on 2008-03-27
I think I'm just going to follow these instructions:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by 11hjpphty76lkjj on 2008-03-27
mlyons16:

If you have any problems following the script let me know and I can assist with any steps.  However the automatic installer should work great on Ubuntu.  The HP LaserJet 1018 is fully supported and you shouldn't experience any complication with using HPLIP.  If you do need any help let me know.

Regarding the 3rd Party Linux driver for the HP LaserJet 1018:

 [FONT=Futura Bk][SIZE=3]Hewlett-Packard supports Open Source  ideals and principals through the development and support of the HP  Linux Imaging & Printing (HPLIP) software which supports nearly  all IPG printing devices.  Hewlett-Packard recognizes that there  are alternatives to HPLIP in the market today and some of these software  solutions provide satisfactory results for Hewlett-Packard customers.[/SIZE][/FONT] 

 [FONT=Futura Bk][SIZE=3]Since HPLIP software is designed  by engineers with an in-depth understanding of Hewlett-Packard’s imaging  and printing technology, the result is software that provides outstanding  print quality, with fast, efficient printing, scanning and faxing solutions.   Furthermore, HPLIP customers can be assured that great care has been  taken to ensure all licensing issues have undergone the strictest legal  scrutiny, delivering a robust Open Source solution for their needs.[/SIZE][/FONT] 

A

---

### Post by mlyons16 on 2008-03-27
> **kalosaurusrex said:**
> mlyons16:

If you have any problems following the script let me know and I can assist with any steps.  However the automatic installer should work great on Ubuntu.  The HP LaserJet 1018 is fully supported and you shouldn't experience any complication with using HPLIP.  If you do need any help let me know.

Regarding the 3rd Party Linux driver for the HP LaserJet 1018:

 [FONT=Futura Bk][SIZE=3]Hewlett-Packard supports Open Source  ideals and principals through the development and support of the HP  Linux Imaging & Printing (HPLIP) software which supports nearly  all IPG printing devices.  Hewlett-Packard recognizes that there  are alternatives to HPLIP in the market today and some of these software  solutions provide satisfactory results for Hewlett-Packard customers.[/SIZE][/FONT] 

 [FONT=Futura Bk][SIZE=3]Since HPLIP software is designed  by engineers with an in-depth understanding of Hewlett-Packard’s imaging  and printing technology, the result is software that provides outstanding  print quality, with fast, efficient printing, scanning and faxing solutions.   Furthermore, HPLIP customers can be assured that great care has been  taken to ensure all licensing issues have undergone the strictest legal  scrutiny, delivering a robust Open Source solution for their needs.[/SIZE][/FONT] 

A

Hey, thank you so much.. Ya, I'm gonna give it a shot tonight. I mean, I'd rather use the HPLIP to get my printer up and running rather than any other third-party solution. The HP solution is free, just like the others, but it's supported and engineered like you say by HP. 

Thanks again for your offer of assistance.

---

