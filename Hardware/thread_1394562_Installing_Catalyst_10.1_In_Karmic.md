---
title: "Installing Catalyst 10.1 In Karmic?"
date: 2010-01-30
forum: Hardware
---

### Post by curtissthompson on 2010-01-30
I'm trying to install the latest ATI Catalyst 10.1 Driver in Ubuntu Karmic for my Radeon HD 5850 graphics card.

I hit problems with the package and found this solution to it:
[http://www.phoronix.com/forums/showpost.php?p=110315&postcount=67](http://www.phoronix.com/forums/showpost.php?p=110315&postcount=67)

However when I try entering the first command, it returns:
"No such file or directory"

I placed the file on my desktop and my desktop directory is my current directory in the Terminal when I'm entering it.

I'm really hoping to get this driver to work as the previous ATI drivers weren't working for me, nor is the open source driver working particularly well.

Any help is greatly appreciated!

*EDIT: [SOLVED] Steps to solve this problem provided in the replies below.

---

### Post by Yellow Pasque on 2010-01-31
Maybe you need to make it executable with:
```
chmod +x *file*
```

---

### Post by curtissthompson on 2010-01-31
I tried that and got same message, here's the resulting terminal output:

```
curtissthompson@curtissthompson-desktop:~$ chmod +x ./ati-driver-installer-10-1-x86.x86_64.run
chmod: cannot access `./ati-driver-installer-10-1-x86.x86_64.run': No such file or directory
curtissthompson@curtissthompson-desktop:~$
```

---

### Post by Yellow Pasque on 2010-01-31
Heh, leave the ./ out of the chmod command 
```
chmod +x ati-driver-installer-10-1-x86.x86_64.run
```

---

### Post by curtissthompson on 2010-02-01
Same result:
```

curtissthompson@curtissthompson-desktop:~$ chmod +x ati-driver-installer-10-1-x86.x86_64.run
chmod: cannot access `ati-driver-installer-10-1-x86.x86_64.run': No such file or directory
curtissthompson@curtissthompson-desktop:~$ 
```

---

### Post by curtissthompson on 2010-02-01
I was wondering, if maybe it isn't being seen due to permissions.  So I right clicked and went to Properties, then clicked the Permissions tab.  The settings are as follows:

Owner: curtissthompson -- Curtiss Thompson
Access: Read and Write

Group: curtissthompson
Access: Read-only

Others
Access: Read-only

Execute: [Checkbox Unchecked] Allow _e_xecuting file as program
SELinux context: unknown

---

### Post by zwaardmeester on 2010-02-02
Just to be sure, what is the output of ```
ls -l
``` in the desktop folder?

---

### Post by Yellow Pasque on 2010-02-02
> curtissthompson@curtissthompson-desktop:~$
You're not in the Desktop folder. The name of your install has the word 'desktop' in it, which is confusing you.

```
cd ~/Desktop
chmod +x ati-driver-installer-10-1-x86.x86_64.run
sudo ./ati-driver-installer-10-1-x86.x86_64.run
```

---

### Post by curtissthompson on 2010-02-05
Yeah, I was suspicious about that myself, but I ended up doing the very thing you suggested, but by changing the settings under Permissions tab for the File Properties:

Execute: [Checkbox Unchecked] Allow executing file as program

By checking that box, then running it (by entering gksu nautilus and proceeding to open the installer), I was able to get through the end of the installer without problems.

I followed the [Custom Driver Installation Option]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat101-inst.pdf") (Page 7), and had success through Step 7 (on Page 9).

I ran into trouble on Step 8, which I'm sure is due to me forgetting how to navigate the file system in Ubuntu via the Terminal, since I haven't used it in years.  Could someone help me with this?

I'm running X.Org 7.4 so I should use user/bin/aticonfig -initial according to the directions.

---

### Post by markbuntu on 2010-02-05
sudo aticonfig --initial

should be all you need. It will ask for your pasword and then execute. It will give you a message like

found .....
and something about creating a new xorg.conf file

---

### Post by curtissthompson on 2010-02-05
It seems to have worked. This was the Terminal's output:

```
curtissthompson@curtissthompson-desktop:~$ sudo aticonfig --initial
[sudo] password for curtissthompson: 
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
curtissthompson@curtissthompson-desktop:~$ 
```

Is that all I needed to do (to complete the installation) before I reboot my system?

---

### Post by curtissthompson on 2010-02-05
Ok. It all installed find and works better than previous ATI Catalyst Drivers have, but my most annoying issue is still recurring.

My screen turns on and off very quickly at varying intervals, but seems to be worst at the highest resolution (1600x1200), but is still bad at lower resolutions.

I'm using a Dell 17 inch Trinitron CRT Monitor.

I don't know what the issue is, and it is a very debilitating problem. Any ideas on what the source of the problem is and what to do to resolve it?

EDIT: Turns out this particular issue was likely caused either by a loss cable connection or using the wrong type of DVI connector (I have both DVI-I & DVI-A-to-VGA converters), though it never occurred while using the same setup under the FOSS driver.

---

### Post by vertago1 on 2010-03-18
When I try to build the packages for either 10.1 or 10.2 I get this problem. Any help?

> dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2


---

