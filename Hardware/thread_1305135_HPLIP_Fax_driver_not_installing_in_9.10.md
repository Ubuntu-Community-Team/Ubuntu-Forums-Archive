---
title: "HPLIP Fax driver not installing in 9.10"
date: 2009-10-29
forum: Hardware
---

### Post by jedininja666 on 2009-10-29
Hi there! I'm a relatively new user to Linux, my previous experience being mainly embedded linux on the NSLU2. I had an old PC and decided to see what all the fuss was about, so today I installed Ubuntu for the first time. So far so good! Got it hooked up to my Sony Bravia via the vga port and got an old Geforce 2MX pumping out 1360x768 using the Nvidia driver, looks awesome! Also got all the extra restricted codecs and whatnot, no troubles at all.

The only trouble is the HPLIP fax driver. I did the sudo aptitude install hplip-gui "work-around", so that I could then do the sudo hp-setup. Everything went well, it detected my networked HP C7280 without problems, and I've since tested the printing and scanning and both are fine. However right at the end, terminal reports the following:

> \error: Unable to locate the HPLIP Fax PPD file: HP-Fax-hpcups.ppd.gz Fax setup has been disabledDoes anyone have any ideas as to how to fix this? Like I say I'm new to Linux really, although I think I'm doing pretty good so far!

---

### Post by dndrich on 2009-11-03
I am in the same boat. So, anybody that figures this out, great!

---

### Post by mutrax on 2009-11-03
I'm working on it... (a workaround that is)

I'll report back soon.

---

### Post by mutrax on 2009-11-03
Got it! 

Downloaded the tarball here;
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

And folowed Naga Samrat's instructions found here;
[https://answers.launchpad.net/hplip/+question/88043](https://answers.launchpad.net/hplip/+question/88043)
> 
go to System -> Administrator -> Synaptic Package Manager
      Search for "hplip" and remove if any previous installation of HPLIP is there.

In the hplip-3.9.8 directory execute the following commands

sudo apt-get update

sudo aptitude install --assume-yes libcupsys2 cupsddk cupsddk-drivers libcupsys2-dev cupsys-bsd libcupsimage2-dev libdbus-1-dev build-essential gs-esp openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit policykit-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

for 32-bit distro
./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --enable-doc-build --enable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-policykit --disable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build

for 64-bit distro
./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --libdir=/usr/lib64 --enable-qt4 --enable-doc-build --enable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-policykit --disable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build

make
sudo make install

Thank you for supporting HPLIP,
Naga Samrat.


Well, there seem to be more quirks in Karmic, but we'll get there!
Anyway, compiling it from the hplip source fixed it for me!:-\"

---

### Post by DrProtocols on 2009-11-03
An alternative (which the purists may not agree with) is to simply extract the missing files from a tarball and then copy them into the same directory as the other Fax ppds (/usr/share/ppd/hlip/HP from memory as I am at work now and not in front of my home machine). You need to do this as root to make sure that permissions are the same as the other files.

I had the same problem and this worked fine for me - but of course if you are not happy doing this then the more structured approach as suggested would be a better bet.

---

### Post by mutrax on 2009-11-03
Hey, I overlooked a solution that simple ;)

---

### Post by dndrich on 2009-11-03
OK, that method sounds better. So, which files do I need to copy to the hp driver folder?

---

### Post by Manyette on 2009-11-03
I'm a newbie, so perhaps this is out of order, but I had those problems too, and I missed the obvious answer because it was too simple for my feeble mind.  But did anyone just try "Asministration -> Printing"  and then selecting "NEW" at the top left of the box that appears.  After much convoluted efforts to to it the hard way, that simple effort installed my HP printer, and even enabled the Duplexer, which I was unable to get working in Jaunty.  Just a thought, and apologies for intruding.

---

### Post by DrProtocols on 2009-11-04
I copied the two files HP-Fax2-hpcups.ppd.gz  and HP-Fax-hpcups.ppd.gz - although hpsetup only complained about not finding one of these I saw no harm in copying both of them. I put them in the same directory as the existing HP-Fax*-hpijs.ppd.gz files which is /usr/share/ppd/hplip/HP. I would guess this would be the same directory on any standard install but in any case just look for the hpijs files and put the hpcups files in the same directory.

I got the files from hplip-3.9.8.tar.gz that I downloaded from the hplip project pages. The files were in the fax/ppd subdirectory.

I notice there is a new 3.9.10 version of hplip so perhaps that correctly installs the missing files.

---

### Post by DrProtocols on 2009-11-04
Hi Manyette, it's good that you were able to get that working on your system. Unfortunately I tried all available ways (including that one) and in every case although the printer aspect of my 6180 All-in-one installed correctly every time the fax part never did because of the reported missing file. 

Maybe there was something wrong with the hplip install so the needed files didn't get installedt. It would be interesting to know whether in your install the files as mentioned above are present in the /usr/share/ppd/hplip/HP directory without there having been any intervention on your part which would imply the install doing something different?

---

### Post by Manyette on 2009-11-04
> It would be interesting to know whether in your install the files as mentioned above are present in the /usr/share/ppd/hplip/HP directory without there having been any intervention on your part which would imply the install doing something different?

I do have the files in that directory, because I put them there myself, so I'm afraid that won't help you.  Before I found the "Administraton -> Printing" install option, I tried putting those files in every directory in which I found ppd files, all to no avail.  I had those files from my previous jaunty backup, and I installed them all over the place, and none of those places made it work.  I'm still confused over why the Printing function worked, when nothing I did trying to put the files in places where they should have been did not work.  I'm sorry I can't help, but finding my files in that directory did not fix the problem when I tried to do it manually, but everything worked when I used the Printer function.

---

### Post by DrProtocols on 2009-11-04
Hmm, not sure, perhaps using the Printing function caused the files to be "recognized" whereas other approaches couldn't see the copied files for some reason? For me what worked was copying the files into place and then doing System->Preferences->HPLIP Toolbox and going through the find printer and setup steps that it walks you through (after deleting the printer previously set up).

After a little nosing around what I did find was the the required files are actually in the hplip-cups package that Synaptic package manager lists. On my system this package is not installed. I guess it is not listed as a dependency of any of the installed packages (such as hplip) so it doesn't get installed by default. The interesting thing is that in the package details it specifically states that it doesn't provide ppds for the fax functionality for HPs multifunction devices and that no physical ppds are shipped with the package as these are dynamically generated - this would appear to be at odds with the package content which _does_ contain the ppd file that I need for my HP multifunction device...

I haven't tried installing this package as my system seems to work just with the copied files but I guess that installing it would do the trick (it only installs a few things other than the ppd files).

---

### Post by Manyette on 2009-11-04
As an afterthought, have you installed the HP Toolbox?  Seems to me that it helped me with the problem.

---

### Post by DrProtocols on 2009-11-04
Yes, if by that you mean the "HPLIP Toolbox" that is available in the Ubuntu Software Centre. I was using System->Administration->HPLIP Toolbox to try and do my printer configuration but it always failed to configure the fax because of the missing file(s).

As an update, I found that although copying the files into the /usr/share/ppd/hplip/HP allowed the fax to be recognized and "installed" I did then find it wasn't actually usable. In the end I had to use Synaptic to install hplip-cups package which also contained other required files and now the fax appears to actually work :-)

IMHO the hplip-cups package should probably be made a dependency or requirement or whatever of the main installed package or at a minimum if you try and configure a fax without that package having been installed there should be a message saying that the package is required for fax functionality. I don't know if this is a Ubuntu thing or an hplip thing.

---

### Post by dndrich on 2009-11-04
Well, son of a gun, that is what did it. I went into Synaptic and installed hplip-cups, and then my fax was recognized and installed. Go figure. So no other maneuvers were necessary. Faxing works perfectly now across the network. I guess it should be a dependency when hplip is installed, but for some reason with karmic, it isn't. Problem solved.

---

### Post by Manyette on 2009-11-16
> An alternative (which the purists may not agree with) is to simply extract the missing files from a tarball and then copy them into the same directory as the other Fax ppds (/usr/share/ppd/hlip/HP from memory as I am at work now and not in front of my home machine). You need to do this as root to make sure that permissions are the same as the other files.

I had the same problem and this worked fine for me - but of course if you are not happy doing this then the more structured approach as suggested would be a better bet.

Well, I have to come back to my original question. Does anyone know the correct location for the ppd files in Karmic?  I have placed the files in the following directores, after extracting them from the Jaunty tarball:

/etc/cups/ppd/HP-Officejet-j6400.ppd
/etc/cups/ppd/HP-Officejet-J6400_fax.ppd
/etc/cups/ppd/Officejet_J6400_fax.ppd
/etc/cups/ppd/Officejet_J6400.ppd
/usr/share/ghostscript/Officejet_J6400_fax.ppd
/usr/share/ghostscript/Officejet_J6400.ppd
/usr/share/ppd/ghostscript/model/Officejet_J6400_fax.ppd
/usr/share/ppd/ghostscript/model/Officejet_J6400.ppd
/usr/share/ppd/hplip/HP/Officejet_J6400_fax.ppd
/usr/share/ppd/hplip/HP/Officejet_J6400.ppd

When I did this, I noticed that there was one file which has apparently been renamed between Jaunty and Karmic.  Note the two entries which have filenames starting with "HP", as opposed to the Jaunty file names which started with "Office".  (I renamed the fax file myself just to try it in that directory, but that attempt failed also)

Since I failed trying to install it myself originally, I then discovered that the Administration -> Printer selection box set up the printer properly, but said it could not find the proper ppd file for the fax.  So I guess I still do not know either the proper name or the proper location for this needed file.  Please color me confused, at the very least.
My thanks to anyone who can offer help.

---

### Post by dndrich on 2009-11-16
It turns out that all I had to do to make it work was go to synaptic and add hplip-cups, and all was well.

---

### Post by Manyette on 2009-11-16
Thanks for the tip, but hplip-cups clearly states it has no fax ppd files, but I did reload hplip-ijs, which does have the fax filex, but it just didn't help.

---

### Post by Manyette on 2009-11-16
Hi DNDRICH, Well, live and learn.  Despite the fact it claims that it has no fax file, you were absolutely correct, and adding hplip-cups fixed the problem. So much for believing the description! :p  Many thanks, and consider this SOLVED

---

### Post by dndrich on 2009-11-16
I know! I notice the same thing, but it worked. Must be some other dependency that comes with it.

---

### Post by gdesilva on 2009-11-25
Hi,

> **DrProtocols said:**
> I copied the two files HP-Fax2-hpcups.ppd.gz  and HP-Fax-hpcups.ppd.gz -

You need to unzip the two files and copy the *.ppd files into /usr/share/ppd/hplip/HP directory.

Remove the printer and add it back again and then you will find both printer and fax being identified.

I just did the same and everything looks good now.

Hope this helps.

---

### Post by gdesilva on 2009-11-25
...also, make sure you switch to root (sudo su root) before you copy the files...

---

