---
title: "Laserjet 1020 - How to:"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by dimeotane on 2006-07-22
Your Laserjet 1020 doesn't appear to work in Drake 6.06 even with the latest updates installed as of today (July 22 '06).  It is detected but when you send a file to be printed nothing actually is printed.  


Here are the instructions I've followed.  

This solution probably also applies to the HP laserjet 1018, HP laserjet 1005, and HP laserjet 1000. I'm just guessing.



Here's how you can get it to work:

1) Install build-essential files FIRST:
```
sudo apt-get install build-essential
```

2) go to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and follow the "Download and Install" instructions there: I've copied them here:
```
wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
tar zxf foo2zjs.tar.gz
cd foo2zjs
make 
./getweb 1020
sudo make install
sudo make install-hotplug
sudo make cups
```

The printer had to be restarted after every job, unless you do this next step:
```
sudo nano /etc/hotplug/usb/hplj1020
```

then change /etc/hotplug/usb/hplj1020 as follows:

   ```
 
    # Set $DEV to, e.g. /dev/usb/lp0, to force the device you want
    # Else, leave it null to automatically detect the device
    #
    DEV=/dev/usb/lp0
    #DEV= ""

```
i.e. comment out the DEV="" line, as the auto-detect script later on
messes things up, so ensure the location of the printer is forced.I found this tip listed on this site: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)

then create your printer profile:
```
sudo gnome-cups-manager  
```

create printer entries follow the examples shown here: 
[http://foo2zjs.rkkda.com/ubuntu/hp1020.html](http://foo2zjs.rkkda.com/ubuntu/hp1020.html)
It should autodetect your local printer.
Next reboot your system and turn your printer off and on to reset.
Should work alright with this solve... though the driver still needs work. 

there is a forum for this driver: post here if you have suggestions/ bug issues [http://s3.phpbbforfree.com/forums/foo2zjs.html](http://s3.phpbbforfree.com/forums/foo2zjs.html)  

************************************************************************



More instructions here: 
[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)



This issue is discussed in these other threads: 
[http://www.ubuntuforums.org/showthread.php?t=125545&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=125545&highlight=laserjet+1020)
[http://www.ubuntuforums.org/showthread.php?t=184580&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=184580&highlight=laserjet+1020)
[http://www.ubuntuforums.org/showthread.php?t=183557&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=183557&highlight=laserjet+1020)
[http://www.ubuntuforums.org/showthread.php?t=102372&page=3&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=102372&page=3&highlight=laserjet+1020)

I've read you need to remove the old foo2zjs first but can anyone post here how they've done that?

---

### Post by JohnDifool on 2006-08-28
> **dimeotane said:**
> 
This solution probably also applies to the HP laserjet 1018, HP laserjet 1005, and HP laserjet 1000. I'm just guessing.


Your solutions works for the HP Laserjet 1018. I've just installed it on my parent's box and after printing a couple of sheets I think the printer works as it should.
 
> 
$ ./getweb 1020


> 
$ sudo nano /etc/hotplug/usb/hplj1020

then change /etc/hotplug/usb/hplj1020 as follows:
DEV=/dev/usb/lp0
    #DEV= ""


I replaced all the ..1020 with ...1018 but that should be obvious of course.

That's all I did to make it work.
:grin:

---

### Post by saracen on 2006-09-01
Does this work for the laserjet 1022?  It's written on the webpage that it should.  I followed the steps and downloaded the firmware for the 1020 printer (no option for the 1022) but no dice...

---

### Post by beast2k on 2006-09-09
This how to worked for my 1018 perfectly, thank you for posting it.

As a side note should this sort of thing be autodetected and installed out of the box? If a linux newbie had this problem he/she would not bother with a how-to they would think it easier to return to using windows xp or another distro of linux. Basic hardware such as printers not working is what scares off newbies and we don't want to scare off newbies we want to attract them so as to increase the linux user base.

---

### Post by Laterix on 2006-09-22
Thanks for the howto. I applied it to my 1018 and it works well... but I would like to enable double sided printing. Does anyone know if this is currently supported by the driver?

---

### Post by jaywatkins on 2006-09-24
Does anyone know if this will work with Xubuntu ?

It should, but X is a bit different than Ubuntu.  Seems alot of work to enable printing...

/J

---

### Post by acorrigan on 2006-09-26
I've found that the problem isn't that it won't print at all, rather that it just won't print the first page of a particular job.  Has anyone else noticed this?

I think beast2k makes a very important point.  Should this issue be submitted as a bug report, so it's fixed for edgy?

---

### Post by inzpektor on 2006-10-27
My HP Laserjet 1020 is connected to my server, but I always work (and print) on my laptop.  If I print directly from the server, everything works fine, but if I print from my laptop, it prints "JZJZ4$ZZ" on the top of the first page and then keeps spitting out empty pages until I turn it off and back on again.

I've configured the printer on my laptop this way:

In gnome-cups-manager - New Printer.
Printer Type: Network Printer (CUPS Printer (IPP))
URI: http://<server>:631/printers/LaserJet-1020
Manufacturer: HP
Model: LaserJet 1020
Driver: foo2zjs (recommended) (Suggested)

Both my server and my laptop are running Ubuntu 6.06.  This worked on Ubuntu 5.10 and it works from a Windows box.

Out of frustration, I've installed the latest foo2zjs driver on both systems (giving some extra features in the printer-properties dialog, like Resolution and N-up Orientation, whatever that is) with no success.

Also, the LaserJet 1020 icon in the gnome-cups-manager shows a printer-rack instead of just a small, standalone printer-icon - not that it bothers me, but it didn't use to be this icon.

Any help appreciated!

---

### Post by s_h_a_d_o_w_s on 2006-11-04
Thanks workep perfectly on my dapper ubuntu isntallation. :-)

---

### Post by linorg on 2006-11-17
Works sucessfully in Kubuntu 6.10 Edgy Eft!

Two adaptations:

1) The file **/etc/hotplug/usb/hplj1020** was updated by my system. I had no need to edit it. The driver might have been updated since the original post?

2) Naturally gnome tools will not work (out of the box) in KDE ;) Use System Settings/Printers insted. ```
sudo gnome-cups-manager
```

---

### Post by robin-tre on 2006-11-21
Thanks very much,

This worked successfully with Ubuntu Edgy too. I'm new to Ubuntu and have been wrestling with various issues for weeks.

What a delight to find these step by step instructions... the effort of trying to understand every problem I've met to date, then of applying the sometimes incomplete explanations I found on the net was beginning to scramble my brain.

Robin

---

### Post by pickled on 2006-12-31
Using Kubuntu Edgy (6.10) I had to manually enter the URI in the printer dialog:
DeviceURI usb://HP/LaserJet%201020

Found Here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)

---

### Post by laharrin on 2007-01-07
Thanks for the concise how-to.  These instructions worked for a LaserJet1000 on Edgy.

---

### Post by falconisthebest on 2007-01-20
thanks alot MAN, 

worked like a charm... !

---

