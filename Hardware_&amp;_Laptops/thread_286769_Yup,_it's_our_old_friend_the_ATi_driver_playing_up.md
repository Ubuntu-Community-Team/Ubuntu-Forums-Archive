---
title: "Yup, it's our old friend the ATi driver playing up again"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by happy-and-lost on 2006-10-28
Trying to get my ATi x300 working under Edgy, have failed using the drivers available in the repos, so have turned to ATi's official Linux driver, but, alas...
```
jo@jo-laptop:~$ sudo sh ati-driver-installer-8.29.6.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

```
](*,)

---

### Post by pony-tail on 2006-10-28
I had this error on my P4 with the latest (24 hours ago) version from ATI servers - Was working OK a week or so ago not sure if it is a bad package or bad xorg7.1 - 
I will be watcing for a version change on their server.
ATI + edgy = problems .....for me anyway

---

### Post by happy-and-lost on 2006-10-28
I tried an older version of the ATi driver, that had the same issue. Must be an Edgy problem.

---

### Post by Pathfinder_ on 2006-10-28
i had a similar issue but instead of saying > ./ati-installer.sh: 176: Syntax error: Bad substitution 
it said > ./ati-installer.sh: **165**: Syntax error: Bad substitution

i found solution [here]("http://www.ubuntuforums.org/archive/index.php/t-243342.html")
in the first post.

---

### Post by Malac on 2006-10-28
This is a dash/bash conflict ATI wants bash, Edgy uses dash.
Try running this before running ATI driver:
```
sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh
```Afterwards, once you've finished with ATI's driver run

```
sudo mv /bin/SH /bin/sh
```Hope this helps.

EDIT:
Just read the whole post sorry for the repeat :)

---

### Post by Roobert on 2006-10-31
Has anyone had any success with the proprietary ATI drivers? I'm thinking about trying this method, as I haven't had any success getting my ATI X300 working.

---

### Post by Ferrat on 2006-11-03
> **Roobert said:**
> Has anyone had any success with the proprietary ATI drivers? I'm thinking about trying this method, as I haven't had any success getting my ATI X300 working.

I have

[http://ubuntuforums.org/showthread.php?t=292208](http://ubuntuforums.org/showthread.php?t=292208)

Read the ATi part there (second post)

---

### Post by gekkehenkie on 2006-12-09
Thanks Malac, that did the job!

---

### Post by Malac on 2006-12-09
> **gekkehenkie said:**
> Thanks Malac, that did the job!
You're Most Welcome. :)

---

### Post by n0deal on 2007-04-03
Thanks for the instructions Ferrat.  Your howto on installing the ATI drivers helped me fix my xorg which I broke horribly trying to get Beryl running.  Now I have to decide if I'm brave enough to try again.  

Cheers!

---

### Post by espmartin on 2007-08-02
This is an old post, but...

I get this after following all instructions:

> [I]espmartin@linux-desktop:~/software/Linux$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.2.0

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install
espmartin@linux-desktop:~/software/Linux$ [/I]

---

### Post by laughter on 2007-08-29
I ran into the same error tonight.

It turned out for me that the 8.29 is an older version. Have you tried going to the ati.amd.com site and downloading the 8.40 drivers from there?

---

### Post by Bluemagic on 2007-10-25
I'm using Ubuntu 7.10 - the Gutsy Gibbon - and when I first installed everything looked great, but then I tried to enable my second monitor, logged out/in and then all of a sudden it can't find any graphics drivers and I'm stuck at 800x600.  I've tried everything in this thread but nothing seems to work.  

To clarify when I execute the ATI driver file from terminal I recieve './ati-installer.sh: /bin/sh: bad interpreter: no such file or directory Removing temporary directory: fglrx-install

When I try running sudo aptitude update that seems to update fine, however when I run sudo aptitude install xor-driver-fglrx  I receive 'The following packages are BROKEN:
xorg-driver-fglrx.  The following packages have unmet dependencies:
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) which is virtual package'

I think that's the driver I was using before trying to enable my second monitor broke it, right?

---

