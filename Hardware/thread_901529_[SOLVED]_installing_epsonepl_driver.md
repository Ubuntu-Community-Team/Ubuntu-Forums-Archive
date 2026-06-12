---
title: "[SOLVED] installing epsonepl driver"
date: 2008-08-26
forum: Hardware
---

### Post by klausthorn on 2008-08-26
Ubuntu 8.04: installing driver for Epson EPL-5900L, Epson EPL-5700L, Epson EPL-5800L, Epson EPL-6100L, Epson EPL-6200L

- download "epsonepl" driver from [http://sourceforge.net/project/showfiles.php?group_id=69547](http://sourceforge.net/project/showfiles.php?group_id=69547) (Version 0.4.1 (current) worked in my case)

- install ubuntu package build-essential

- install commands as root, example with EPL-5900L:

```

 cd /usr/src
 tar zxvf  /download-place/epsoneplijs-0.4.1.tgz
 cd epsoneplijs-0.4.1/
 ./configure
 make
 make install
 mkdir -p /usr/share/cups/model/foomatic-ppds/Epson/
 cp -av ../foomatic_PPDs/Epson-EPL-*-cups.ppd.gz /usr/share/cups/model/foomatic-ppds/Epson/
 cp foomatic/driver/epl5900l.xml /usr/share/foomatic/db/source/driver/
 cp foomatic/opt/epsonepl-* /usr/share/foomatic/db/source/opt/
 cp foomatic/printer/Epson-EPL-5900L.xml /usr/share/foomatic/db/source/printer/
 /etc/init.d/cupsys restart

```

- probably not necessary, but done in my case while searching the solution:
```

ln /usr/local/bin/ijs_server_epsonepl  /usr/bin/
 cp /usr/share/cups/model/foomatic-ppds/Epson/Epson-EPL-5900L-epl5900l-cups.ppd.gz /etc/cups/ppd/EPSON-EPL-5900L.ppd.gz
 gunzip /etc/cups/ppd/EPSON-EPL-5900L.ppd.gz

```
 
- interesting:

 /usr/src/epsoneplijs-0.4.1/foomatic_scripts/install_customfoomatic
 [http://openprinting.org/show_driver.cgi?driver=epsonepl&fromprinter=Epson-EPL-5900L](http://openprinting.org/show_driver.cgi?driver=epsonepl&fromprinter=Epson-EPL-5900L)

- then I created a new printer named "EPSON-EPL-5900L" via the cups web interface on [http://localhost:631](http://localhost:631)

klaus at trillke dot net

---

### Post by hounddog on 2009-04-30
Thanks for the tutorial.  I got my Epson6100L working in Jaunty by following your tutorial.  Just a few changes to your tutorial is required to get things working under Jaunty, not much really, it's such a great tutorial! :-

1.  /etc/init.d/cupsys restart needs to be changed to /etc/init.d/cups restart under Jaunty

2.  ln /usr/local/bin/ijs_server_epsonepl /usr/bin/ is a must as the program ijs_server_epsonepl is saved in the /usr/local/bin/ folder instead of /usr/bin/ when it is really needed in the /usr/bin folder, so you either have to copy the program to the /usr/bin/ folder or create an artificial link as you did.

Again, thanks for the great tutorial.  You have my deepest gratitude.  I spent too many moons trying to get this printer to work under Linux.

---

### Post by huwie59 on 2009-06-25
The original post plus amendments worked for me too after weeks of frustration. Thank you both.

---

### Post by klabog on 2009-11-09
Thanks for the great HowTo!
I did it with Ubuntu Karmic and it worked well with my epl-6200L.
Used the changes from hounddog and corrected one line in your code (naturally substituted epl5900l by epl6200l)
from
```
cp -av ../foomatic_PPDs/Epson-EPL-.....
```
to
```
cp -av foomatic_PPDs/Epson-EPL-.....
```

Klaus

---

### Post by mikebenny71 on 2009-11-24
I posted a complete guide to solve the problem with Espon EPL6200L with the last version of Ubuntu 9.10. 
It's from Ubuntu version 7.04 that I am updating this guide. 
Now I updated and tested it with the last version of Ubuntu. the same guide is also working with Ubuntu 9.04!

You can download it from:

[http://grappafsd.homelinux.org](http://grappafsd.homelinux.org)   (select LINUX DOC from menu)


Take fun!   :p
Mike

---

### Post by six616 on 2009-12-15
when I do ./make , my problem is below

...
~/Desktop/epsoneplijs-0.4.1$   ./make
bash: ./make: No such file or directory

---

### Post by stefanhuglfing on 2010-02-18
I did it like klausthorn wrote with the tips of hounddog and klabog. After creating the new printer via [http://localhost:631](http://localhost:631) I can see the printer EPSON EPL-5900L but it doesn't work.

If I want to print a text, the printer appears, but at "status" I can read: "Printer 'EPSON_EPL-5900L'  may not be connected".

But I HAVE conncted it via USB and power is on.

Who can help?

---

### Post by tetebueno on 2010-03-20
Oh my dog... mikebenny71's tutorial worked great with a Epson EPL 6200L through a parallel port after hours of searching for a solution. Thanks, dude.

---

### Post by ulli.winter on 2010-03-27
Hi,
i think that i've installed the driver correctly but after clicking in "add printer" in cups "scsi" is the only local printer type offered. In the next step i would have to enter "Connection:
Examples: [http://hostname:631/ipp/](http://hostname:631/ipp/)
[http://hostname:631/ipp/port1](http://hostname:631/ipp/port1) ..."
Is this the right way? What should i use as connection adress?

---

### Post by six616 on 2010-04-13
> **mikebenny71 said:**
>  the same guide is also working with Ubuntu 9.04!

You can download it from:

[http://grappafsd.homelinux.org](http://grappafsd.homelinux.org)   (select LINUX DOC 
it works for my Ubuntu 9.10 , THANKS!

---

### Post by mettavihari on 2010-06-02
Hello

I have installed the Printer on 8.10 and 9.04 and it worked fine
BUT
The driver does not work on the new version Lucid

regards
Mettavihari

---

### Post by seitenwurm on 2010-07-27
Just installed without a problem my Epson EPL 5900L under Lucid Lynx (Ubuntu 10.4) with this package.
(At least the test page printed)

Thanks!

I had the .ppd file before.

---

### Post by john.v.kesteren on 2010-09-21
[QUOTE=klausthorn;5668830]Ubuntu 8.04: installing driver for Epson EPL-5900L, Epson EPL-5700L, Epson EPL-5800L, Epson EPL-6100L, Epson EPL-6200L
 
This post is from 2007, we are now in 2010. Does it still work the same way under Ubuntu 10.04???? I am a novice to Linux and eager to get my printer working. A few silly questions:
 
What is "ubuntu package build-essential" where do I get it?
 
"commands as root, example with EPL-5900L:" Where do I type these commands? is it a script, how do I get it in the root?
 
In other words, can anyone provide me with step by step instructions (without using the words "simply" or "easy", I generally get stuck at that point, it has nothing to do with easy, but with knowing what buttons to press. I can press buttons, but cannot do "simply" do "easy" things). Or is this frustration from the Windows age still talking.
 
Thanks for any help. JOHN

---

