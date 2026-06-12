---
title: "libusb-dev and drivers for the HP Ink Advantage 3525"
date: 2014-06-01
forum: Hardware
---

### Post by cdb10 on 2014-06-01
I am trying to install the drivers for the HP Ink Advantage 3525.
I downloaded and ran the file:
```

sh hplip-3.14.4.run 

```
output in program:
```

error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

```
When I tried to install the requirements:
```

This APT has Super Cow Powers.
lap1@laptop:~/Pobrane$ sudo apt-get install libusb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by Yellow Pasque on 2014-06-01
```
sudo apt-get install libusb1.0-0-dev
```

---

### Post by cdb10 on 2014-06-01
```

sudo apt-get install libusb1.0-0-dev
[sudo] password for lap1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libusb1.0-0-dev
E: Couldn't find any package by regex 'libusb1.0-0-dev'

```

---

### Post by Yellow Pasque on 2014-06-01
What version of Ubuntu are you using? Precise/12.04?

---

### Post by cdb10 on 2014-06-02
```

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

```

---

### Post by steeldriver on 2014-06-02
It's 

```

libusb[COLOR=#ff0000]**-**[/COLOR]1.0-0-dev

```

I think (note the extra dash)

---

### Post by cdb10 on 2014-06-02
```

$ sudo apt-get install libusb-1.0-0-dev
[sudo] password for lap1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-1.0-0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by steeldriver on 2014-06-02
in that case you will need to dig in to the HP installer to see exactly what package/version it is testing for, I guess

---

### Post by cdb10 on 2014-06-02
```

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes libusb-1.0.0-dev'
Please wait, this may take several minutes...
error: A required dependency 'libusb (libusb - USB library)' is still missing.



```
As far as I understand, HP installer wants exactly libusb-1.0.0-dev that is already installed on the system. This is nonsense. I do not understand why HP installer  states absence package.

---

### Post by Yellow Pasque on 2014-06-02
You can probably spare yourself the frustration of building your own hplip if you grab the 3.13.9 version from the precise-backports repo. That's a fairly recent version of hplip and it should work for your model according to HP: [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3520_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3520_series.html)

---

### Post by cdb10 on 2014-06-02
As far as I know this is hplip-3.14.4.run(HP installer) the program that I am trying to run.

---

### Post by Yellow Pasque on 2014-06-02
^Okay... but it's not building (for some reason).

I am suggesting you get a pre-built package from precise-backports repo.

---

### Post by cdb10 on 2014-06-02
I do not understand. What is pre-built package from precise-backports repo? 
If I go in to the directory hplip-3.14.4 and  I run program ./configure I get:
```

checking for cups/cups.h... yes
checking for libusb_init in -lusb-1.0... yes
checking libusb-1.0/libusb.h usability... no
checking libusb-1.0/libusb.h presence... no
checking for libusb-1.0/libusb.h... no
configure: error: cannot find libusb-1.0-devel support

```

Accordance with the recommendation:
```

$ sudo apt-get install libusb-1.0-devel 
[sudo] password for lap1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libusb-1.0-devel
E: Couldn't find any package by regex 'libusb-1.0-devel'

```

---

### Post by steeldriver on 2014-06-02
What exact version do you have? maybe there is a ppa that's pulled in a *newer* version than the installer is expecting

```

apt-cache policy libusb-1.0-0-dev

```

It seems to work on my 12.04 box with libusb-1.0-0-dev version 2:1.0.9~rc3-2ubuntu1

---

### Post by cdb10 on 2014-06-02
```

$ apt-cache policy libusb-1.0-0-dev
libusb-1.0-0-dev:
  Installed: 2:1.0.9~rc3-2ubuntu1
  Candidate: 2:1.0.9~rc3-2ubuntu1
  Version table:
 *** 2:1.0.9~rc3-2ubuntu1 0
        500 http://pl.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Yellow Pasque on 2014-06-02
```
gksu software-properties-gtk
```

Go to 'Other Software' tab and check backports repo.
[IMG]http://i.stack.imgur.com/3qhj0.png[/IMG]

Close that and run:
```
sudo apt-get update
sudo apt-get install hplip
```

After that, you'll probably want to disable the backports repo, since it's generally not desirable to install everything in it.

---

### Post by cdb10 on 2014-06-03
```

$ sudo apt-get install hplip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by Yellow Pasque on 2014-06-03
Yes, but what version? Did you follow all the directions above?
```
apt-cache policy hplip
```

---

### Post by cdb10 on 2014-06-03
SOLVED!
How I did it:
I  removed libusb-1.0 and I downloaded source from [http://www.libusb.org/ ]("http://www.libusb.org/") and I compiled and installed. Subsequently I ran HP Installer. The device HP works. I do not understand why then did not work, and it works now.  So theoretically, what happened?

---

### Post by steeldriver on 2014-06-03
Maybe some files (e.g. /usr/include/libusb-1.0/libusb.h) got manually deleted - I would have suggested **re**installing libusb-1.0-0-dev (apt-get install --reinstall) as a next step, rather than installing from source - but whatever

---

