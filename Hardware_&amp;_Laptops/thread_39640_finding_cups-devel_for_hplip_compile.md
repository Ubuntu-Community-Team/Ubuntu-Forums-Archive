---
title: "finding cups-devel for hplip compile"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by dmintz on 2005-06-05
Hello all, I am a brand new Ubuntu dude and loving it so far. Though I am stuck trying to compile hplip-0.9.3 for my HP Laserjet 3020

** ./configure --prefix=/usr** 
[lots of stuff goes ok, then....]
checking cups/cups.h usability... no
checking cups/cups.h presence... no
checking for cups/cups.h... no
configure: error: cannot find cups-devel support

Indeed it seems there is no cups.h, cups-devel etc anywhere on my system according to 'find.'  I have seen a couple of rpms out there, such as one for Fedora,  but I wonder about compatibility.

Does anyone know where I can get cups-devel package suitable for 5.0.4? Or is there some other way to get this HP Laserjet 3020 multifunction machine working?

Many thanks

---

### Post by jjross on 2005-06-05
Have you tried the hp site for instructions on how to do this for a linux system . try looking at his link it worked for me  .[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

---

### Post by dmintz on 2005-06-06
[QUOTE=jjross]Have you tried the hp site for instructions on how to do this for a linux system . try looking at his link it worked for me  .[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)[/QUOTE]

Absolutely -- that's where the adventure started.

---

### Post by David Haas on 2005-06-06
I'd first look in System>Administration>Synaptic Package Manager to see whether the  HPLIP package is installed. Perhaps it contains the files you need. First do a package upgrade before installing to be sure to get the latest package. I assume that you have all the cupsys and foomatic packages installed. 
David Haas

---

### Post by dmintz on 2005-06-17
in fact hlip is installed and is the latest version according to apt-get, but when I try to install my printer through the GUI it is not listed.

so, I  try following the manual driver installation instructions provided at [http://hpinkjet.sourceforge.net/install.php#HPLIP](http://hpinkjet.sourceforge.net/install.php#HPLIP) and run into the problem described above, i.e., missing dependencies. after some googling I finally figured out that the packages that provide the actual stuff you need go by different names for different distros. thus 'apt-get install cups-devel' brings you no joy but ' apt-get install libcupsys2-dev' does. here's what I had to do in order to make sure  'configure' would be happy:

```
    
   [B] sudo apt-get install libcupsys2-dev
    sudo apt-get install python-dev
    sudo apt-get install libsnmp5-dev
    sudo apt-get install python-qt3
    sudo apt-get install lsb
    sudo apt-get install libgd2 # maybe not necessary?
    sudo apt-get install libgd2-dev[/B]
```

Otherwise, follow those instructions till step 11, where the instructions say 
```

    Enter this command:
   **/etc/init.d/cups restart**

```
because you will actually want to say 
```

    **sudo /etc/init.d/cupsys restart**

```
Then you can go System->Administration->Printing or whatever it is (I am not at my ubuntu box right now) to the print admin GUI and add a new printer, and find your new driver there. Scanning support will be enabled too.

I hope this helps someone else

---

### Post by dodden on 2006-12-13
Thank you very much for posting this. I found that between my clean 6.06 install and 6.10 install I lost a lot of these capabilities. All is installing and working like it did the first time I did this.

Darren

---

