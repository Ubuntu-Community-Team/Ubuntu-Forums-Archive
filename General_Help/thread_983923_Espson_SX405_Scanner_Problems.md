---
title: "Espson SX405 Scanner Problems"
date: 2008-11-16
forum: General Help
---

### Post by lewisjd on 2008-11-16
Hi all, I'm a noob to Ubuntu and so far so good!  However, I've installed my SX405 and the printer works however I cannot get the scanner to work and Xsane doesn't seem to have the printer listed.

Can anyone help me please?

Thank you.

Lewis

:)

---

### Post by Alexia_Death on 2009-01-04
Well.. [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) Get the iscan deb from the bottom of the page and install it. I still cant quite bellive that it WORKS! totally and utterly WORKS. \\:D/

---

### Post by mozbrowser on 2009-03-08
> **Alexia_Death said:**
> Well.. [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) Get the iscan deb from the bottom of the page and install it. I still cant quite bellive that it WORKS! totally and utterly WORKS. \\:D/

I just downloaded the iscan_2.17.0-3_i386.deb from the page you referred to. When I open the downloaded file it is opened using GDebi-gtk.
When I try to install the package it says [COLOR="Red"]Error: Dependency is not satisfiable: libltdl3[/COLOR]. I cannot install it using apt-get or Synaptic.

BTW, I just recently installed Ubuntu 8.10. Do I need a newer version of libltdl / iscan ? I used the form provided by Avasys to download this version. Ubuntu 8.10 was listed there. However, this Ubuntu-version is not in the test results: [http://avasys.jp/hp/menu000001300/hpg000001249.htm](http://avasys.jp/hp/menu000001300/hpg000001249.htm)

Thanks in advance,

Martijn

---

### Post by mozbrowser on 2009-03-08
OK, I finally managed to install libltdl3 for Ubuntu 8.10 using the package for Hardy as mentioned in [http://ubuntuforums.org/showthread.php?t=978407](http://ubuntuforums.org/showthread.php?t=978407)

Now I am going for solving the next problem: some like an access denied-message when trying to use the scanner from GIMP. But that should be something security-related I guess.

---

### Post by rbmorse on 2009-03-08
Could be a permissions problem. 

Use the Users and Groups administration facility to add your user to the "scanner" group. Log out of the session and log back in to make the change effective. 

Then, from a terminal try:

sudo chgrp -R scanner /usr/lib/iscan<enter>

---

### Post by mozbrowser on 2009-03-11
> **rbmorse said:**
> Could be a permissions problem. 

Use the Users and Groups administration facility to add your user to the "scanner" group. Log out of the session and log back in to make the change effective. 

Then, from a terminal try:

sudo chgrp -R scanner /usr/lib/iscan<enter>
Thank you for your reply. It was a permissions problem indeed. And the "log out and log back in" part did the trick ! I did not think about that. I thought that was something of Windows-systems, but now I know the same goes for Linux.

I just made my first scan using my new Epson all-in-one. Nice to see it works with Linux too.

---

### Post by nukeqler on 2009-05-21
I was able to get scanning with my nx 300 under 64-bit jaunty as follows:

I was able to install the iscan package with

```
sudo dpkg --ignore-depends=libltdl3 -i iscan_2.19.2-1_amd64.deb
```

And then I did the link from libltdl7 to libltdl3 as suggested earlier

```
cd /usr/lib
sudo ln -s libltdl.so.7 libltdl.so.3
```

And after power-cycling my nx 300 (dunno why, but the power light was blinking, and iscan didn't see it until I did), iscan works as expected.

Thanks to those who did the preliminary work.

---

### Post by anyusername on 2010-03-04
> **nukeqler said:**
> I was able to get scanning with my nx 300 under 64-bit jaunty as follows:

I was able to install the iscan package with

```
sudo dpkg --ignore-depends=libltdl3 -i iscan_2.19.2-1_amd64.deb
```

And then I did the link from libltdl7 to libltdl3 as suggested earlier

```
cd /usr/lib
sudo ln -s libltdl.so.7 libltdl.so.3
```

And after power-cycling my nx 300 (dunno why, but the power light was blinking, and iscan didn't see it until I did), iscan works as expected.

Thanks to those who did the preliminary work.
Thanks for that nukeqler, it worked for my Epson DX8400 too; however, synaptic now reports:
> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Repairing the package removes iscan. How do I stop Synaptic from reporting this as a broken package?

---

### Post by squinter on 2010-03-19
I got the same problem with the following

> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Please if anyone knows how to solve this.

---

