---
title: "ATI Drivers"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by Mrafcho001 on 2006-02-05
I downloaded the new drivers from the ATI website:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Then I did, as it said in the instructions:
./ati-driver-installer-8.21.7-i386.run

ERROR:
bash: ./ati-driver-installer-8.21.7-i386.run: Permission denied

And that is the error i get, I tried logging in as root and I still get that error.

---

### Post by o_fortuna on 2006-02-05
[QUOTE=Mrafcho001]I downloaded the new drivers from the ATI website:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Then I did, as it said in the instructions:
./ati-driver-installer-8.21.7-i386.run

ERROR:
bash: ./ati-driver-installer-8.21.7-i386.run: Permission denied

And that is the error i get, I tried logging in as root and I still get that error.[/QUOTE]
Do you absolutely need the new drivers? If the drivers included with ubuntu work, it's much easier to use them. Open up Synaptic (System-->Administration-->Synaptic) and look for xorg-driver-fglrx. Install that, and you'll have 3D support for your ATI card. It's much easier than using the one from the web site.

---

### Post by Mrafcho001 on 2006-02-05
It is way, way too slow.

On screen savers i barely get over 10FPS, and i have a Radeon 9800pro.

I dont think that is normal..

---

### Post by o_fortuna on 2006-02-05
[QUOTE=Mrafcho001]It is way, way too slow.

On screen savers i barely get over 10FPS, and i have a Radeon 9800pro.

I dont think that is normal..[/QUOTE]
Here, try this guide: [HOWTO: ATI fglrx driver - latest version]("http://ubuntuforums.org/showpost.php?p=423584"). All you have to do is change the version number.

EDIT: I changed to a better/easier/more complete guide.

---

### Post by Mrafcho001 on 2006-02-05
Ok installed the drivers but when i try to configure them it gives me an error:

/usr/X11R6/bin/aticonfig: error while loading shared libraries: libfglrx_pp.so.1 : cannot open shared object file: No such file or directory

Any thoughs?

ill try that guid in a second, o_fortuna

---

### Post by o_fortuna on 2006-02-05
[QUOTE=Mrafcho001]Ok installed the drivers but when i try to configure them it gives me an error:

/usr/X11R6/bin/aticonfig: error while loading shared libraries: libfglrx_pp.so.1 : cannot open shared object file: No such file or directory

Any thoughs?

ill try that guid in a second, o_fortuna[/QUOTE]
That might be solved by using the guide a mentioned above. It just seems like something isn't on your system that should be. The guide should have you install all the dependencies (I just changed to a better guide, so be sure you are using the one by mlomker, it's a easy guide).

---

