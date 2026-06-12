---
title: "xerox workcentre 3119"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by Victor.Barna on 2007-03-24
Hi, i've recently bought a xerox wc 3119 multifunction USB printer and i have no ideea on how to install the linux drivers.
Here's a link to the actual drivers [http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC3119&Xlang=en_GB&Xcntry=GBR](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC3119&Xlang=en_GB&Xcntry=GBR)

thanks in advance.
vic.

---

### Post by Victor.Barna on 2007-03-24
by the way, running install.sh gives me:

install.sh: 11: source: not found
[: 670: ==: unexpected operator

---

### Post by Victor.Barna on 2007-03-25
bump ](*,) :(

---

### Post by bamakojeff on 2007-05-03
I just got it working with large doses of help from Google! :-)  It mostly has to do with Ubuntu's changing which shell '/bin/sh' points to.  The 'dash' shell that Ubuntu uses doesn't have all the functionality of the 'bash' shell, which the xerox installer expects., so we need to make the installer use the bash shell. Change it with the following commands:

cd /bin
sudo rm -f sh
sudo ln -s bash sh

Now go back to the xerox installer program which you downloaded and run it again as root.  You'll get a couple of errors about files not being found, but that's OK.

Now open the Ubuntu Printer Administration program.  That's "System->Administration->Printing" in Gnome.  (I did this in Gnome, but it ought to similar in KDE.)  You'll see that the installer has installed the printer, but that one didn't work for me.  So you need to delete it and then add a new printer.  (I think you need to be in Administrator mode for this to work.)  

When you add a new printer it should see a local printer - "Xerox WorkCentre 3119 Series" printer on a USB port.  Choose that one and click Next.  Then for the driver you need to use the driver that was just installed.  So click the "Install Driver" button and select "/usr/share/cups/model/xerox/wc3119.ppd.gz".  Then click Next, fill in any information that you want about the location, etc. and click Apply.

Now the printer should work.  (At least it does for me.)  YMMV :-)

Next, let's get the scanner working. First you need to edit (as root) the file '/etc/udev/rules.d/60-symlinks.rules' and add the following two lines to the bottom of it:

# Create symlink for usb printer to /dev/usb/lp*
BUS=="usb", KERNEL=="lp[0-9]*",         SYMLINK+="usb/%k"

Then restart udev:

sudo /etc/init.d/udev restart

Then add yourself as a user to the 'lp' group so you can use the scanner:

sudo adduser <username> lp

where <username> is the linux user you log in as.  So if you are logged in as "victor" then you would run:

sudo adduser victor lp

Now once you log out and log back in (so the changes to your group memberships get applied) the scanner should work.  I've tested it with xsane as well as the Xerox MPF Configurator which the install.sh program installs.  It doesn't work for me with Kooka, but I haven't bothered to see why not since I don't use it.

Finally, we change the 'sh' link back to the 'dash' shell like it was originally.

cd /bin
sudo rm -f sh
sudo ln -s dash sh

That's it.  Printing and scanning should both be working now.  Hope this helps.

---

### Post by Victor.Barna on 2007-06-27
Sorry for bumping the thread, bamakojeff I LOVE YOU :lolflag: , it finally works.
there was a slight problem though...it kept setting my device address to usb://xerox/workcentr...etc  so the printing didn't work but i changed it to mfp:/dev/mfp4 -wich is the first usb port.

thanks a lot bamakojeff, i owe you one!

---

### Post by mike dan on 2007-11-01
I have been to try install my 3119 by the way, stated by bamakojeff.

But I had some problems. At the time of my device was installing 3119,  Ubuntu was writting message about errors of next contents:" &#1055;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1072; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080; CUPS: 'server-error-internal-error'" (Take place error in the time of operation CUPS: 'server-error-internal-error')

The device  standing up and correctly printing "Test Page", BUT when I trying to print in FireFox, the job went to device and it printing page not correctly, it printing next message on the paper:
INTERNAL ERROR - FALSE
POSITION :  0x20a846 (2140230) - the number is different every time
SYSTEM    : H6FW/xl_tbl
LINE         : 407
VERSION  : QPDL 1.40 11-14-2005

If I printing by OpenOffice - OpenOffice - fall out and shut down
Ubuntu 7.10

Sorry, at my English.

P.S. &#1044;&#1083;&#1103; bamakojeff - &#1089;&#1091;&#1076;&#1103; &#1087;&#1086; &#1092;&#1072;&#1084;&#1080;&#1083;&#1080;&#1080; &#1091; &#1074;&#1072;&#1089; &#1077;&#1089;&#1090;&#1100; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1077; &#1082;&#1086;&#1088;&#1085;&#1080;, &#1080; &#1077;&#1089;&#1083;&#1080; &#1042;&#1099; &#1089;&#1084;&#1086;&#1075;&#1083;&#1080; &#1087;&#1088;&#1086;&#1095;&#1080;&#1090;&#1072;&#1090;&#1100; &#1101;&#1090;&#1086; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1077;, &#1079;&#1085;&#1072;&#1095;&#1080;&#1090; &#1079;&#1085;&#1072;&#1077;&#1090;&#1077; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081; - &#1077;&#1089;&#1083;&#1080; &#1042;&#1072;&#1089; &#1085;&#1077; &#1079;&#1072;&#1090;&#1088;&#1091;&#1076;&#1085;&#1080;&#1090; &#1090;&#1086; &#1087;&#1088;&#1086;&#1076;&#1091;&#1073;&#1083;&#1080;&#1088;&#1091;&#1081;&#1090;&#1077; &#1087;&#1083;&#1080;&#1079; &#1086;&#1090;&#1074;&#1077;&#1090; &#1085;&#1072; &#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1084;, &#1084;&#1086;&#1081; &#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080;&#1081; &#1077;&#1097;&#1077; &#1087;&#1086;&#1082;&#1072; &#1086;&#1095;&#1077;&#1085;&#1100; &#1089;&#1083;&#1072;&#1073;&#1099;&#1081;

---

### Post by u2c4 on 2008-01-15
Hi,
I'm trying to get my wc 3119 xerox working in Gutsy Gibon 7.10 using the above method but only succeeding getting the printing function to work but not the scanner.

   xsane complaint -->  insmod: can't read '/lib/modules/2.6.22-14-generic/kernel/drivers/mfpportctrl/mfpport.ko': No such file or directory.

Is this port or driver issue?
My printer configuration device url pointed to usb://Xerox/WorkCentre%203119%20Series

Newbie here needs help. thanx

---

### Post by gpothier on 2008-04-10
I struggled for hours with this printer...
The most difficult part was getting the scanner to work. In recent ubuntu versions (from gutsy onwards it seems), the usb fs in /proc is disabled. So I had this symptom: the scanner was detected by sane-find-scanner but not by scanimage -L.
Here is the remedy: in /etc/init.d/mountdevsubfs you have to uncomment the four last lines of:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Works like a charm now!

---

### Post by shazbut on 2008-05-05
This is a very useful thread for people like me who've bought this cheap and nasty printer based on its linux "compatibility".  Has anyone managed to get it going under Hardy yet?  I've done a clean install and having trouble setting it up under cups.  Scanner works with gpothier's fix, got the MFP configurator and drivers loaded, but adding the printer in system-admin-printing and choosing the ppd.gz file fails.

Edit: but choosing the printer from the models list works.  But I still get the qdpl errors that mike dan mentioned earlier, particularly printing from a browser or graphics program.

---

