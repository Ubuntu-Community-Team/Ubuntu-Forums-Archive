---
title: "Canon i250 printer install help"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by xodeus on 2005-03-24
Hi. I've installed ubuntu hoary prewiev and it's very nice.
Now the time has come to my printer and I really can't get it to work.
The System > Administration > Printing finds the printer without problems and installs the imageRunner 330s hpijs driver, but it doesn't work. When trying to print at test page the printer blinks and nothing happens. Can anyone help me install this printer.

//Xodeus

---

### Post by zipperback on 2007-09-08
> **xodeus said:**
> Hi. I've installed ubuntu hoary prewiev and it's very nice.
Now the time has come to my printer and I really can't get it to work.
The System > Administration > Printing finds the printer without problems and installs the imageRunner 330s hpijs driver, but it doesn't work. When trying to print at test page the printer blinks and nothing happens. Can anyone help me install this printer.

//Xodeus

You can use this to get it to work.
[http://www.turboprint.info/](http://www.turboprint.info/)

- Jack
- zipperback
:guitar:

---

### Post by xodeus on 2007-09-10
This is payware... Sorry. A new printer is much cheaper than a license to TurboPrint.
Canon i250
with these printers the FreeEdition works only as demo version: a logo is added to the printout in all resolutions

---

### Post by eddepet on 2007-09-20
try this,

get this files. You can download them from this site:

[http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.aspx](http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.aspx)

bjfiltercups-2.3-0.i386.rpm
bjfilteri250-2.3-0.i386.rpm

then follow the next steps:

sudo apt-get install fakeroot
sudo apt-get install alien

fakeroot alien -cd bjfiltercups-2.3-0.i386.rpm
fakeroot alien -cd bjfilteri250-2.3-0.i386.rpm
(.deb files wil be created).

dpkg --install bjfiltercups_2.3-0_i386.deb bjfilteri250_2.3-0_i386.deb
dpkg --install bjfilteri250_2.3-0_i386.deb bjfilteri250_2.3-0_i386.deb

Now restart cups with this line.

sudo /etc/init.d/cupsys restart

Finally, in Ubuntu 6.10 libtiff ver4 and libpng ver3 are installed and if not they can be installed from the synaptic package manager.

The drivers for i250 want libtiff ver3 and libpng ver2 so you need to create a couple of symbolic links from the versions required to the versions you have.
Do that with the following two lines.

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2 

Now go to System>Administration>Printing and add the printer.
On step 2 of the Add Printer section click the 'Install Driver' button and browse to /usr/share/cups/model/canoni250.ppd file. 

Once all is done you should be able to print a test page.... I could and after many hours of mucking around I was pleasently surprised when the printer sprang to life.

---

### Post by brazacka on 2007-10-14
eddepet:

Worked!  I created an account here just so I could thank you :)  I've had very few successes when using work-arounds or editing config files to get something to work, so I was shocked when my test page actually came through.  Thanks again!

---

### Post by StomUK on 2007-11-02
Is the information in this thread still relavent with gutsys extra printer support? I have a Canon i250 and it refuses to work so far for me :/

I do not have libpng v3 though, I have what I assume is v12. I have changed the 'sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2' line to 'sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2' (matches the file in my usr section..).

I try and print a test page and the 'Document Print Status' shows that a job has been added to the Queue but has been Stopped.

I am still a beginner with linux in general but am keen to learn (especially since I have given up playing WoW now I have much more spare time ;) ) any help or pointers would be greatfully appreciated :)

**edit**
after numerous restarts and other playing about it is now working for me.. bizzare

---

