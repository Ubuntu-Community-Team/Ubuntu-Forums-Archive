---
title: "HP LaserJet 1020, USB-printer"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by fwendt on 2006-02-04
This printer is not supported "out of the box" with Ubuntu 5.10, there is no suitable driver for this printer. (A MacIntosh user used the drivers for LaserJet 1022 under Mac OS X, but the linux/cups driver for 1022 does not work.)

Rick Richardson has some software that he has got working on [http://foo2zjs.rkkda.com/ubuntu/hp1020.html](http://foo2zjs.rkkda.com/ubuntu/hp1020.html) - I'll try it out and see if I can set it up.

---

### Post by fwendt on 2006-02-04
If you add the universe packages to /etc/apt/sources.list you can install a package called foo2zjs which will make CUPS aware of how to convert documents to the format the printer expects. So that's good, but there are still two more issues to resolve before we're all done:
- There's no PPD (Postscript Printer Description) file for the LaserJet 1020 model
- The printer expects it's firmware (software running on the printer, not your computer) to be sent each time it boots up.

If you download the software from Rick's site, you get "add ons" to the hotplug system, that will send this firmware each time your computer detects the printer.

I'll see if I can solve these two in a good way.

---

### Post by fwendt on 2006-02-04
There was a couple of similar posts about this, but none were really accurate for me (such as [http://ubuntuforums.org/showthread.php?t=78272](http://ubuntuforums.org/showthread.php?t=78272))

To get things working:
```
- do not install the foo2zjs package from "universe"
- download the foo-source code from Rick's site, unpack
- build the software
  - you need ubuntu packages make and gcc to do this (sudo aptitude install make gcc) and a couple of library-packages (aptitude will install them for you)
  - make
  - sudo make install
  - sudo make hotplug-install
- add a PPD (Postscript Printer Description) file that is suited for LaserJet 1020
  - cd /usr/share/ppd/HP
  - sudo bash
    - cp *HP*1005*ppd.gz HP-LaserJet_1020-foo2zjs.ppd.gz
    - gunzip *1020*ppd.gz
    - vim (or any other editor) *1020*ppd and replace all occurances of "1005" with "1020"
    - gzip *1020*.ppd
    - exit (leave "root bash")
- restart cupsys (sudo /etc/init.d/cupsys restart)
- restart the printer
- add the printer (menu System -> Administration -> Printers)
  - the printer should be identified automatically
```

Enjoy

---

### Post by Shutdownrunner on 2006-04-22
[QUOTE=fwendt]There was a couple of similar posts about this, but none were really accurate for me (such as [http://ubuntuforums.org/showthread.php?t=78272](http://ubuntuforums.org/showthread.php?t=78272))

To get things working:
```
- do not install the foo2zjs package from "universe"
- download the foo-source code from Rick's site, unpack
- build the software
  - you need ubuntu packages make and gcc to do this (sudo aptitude install make gcc) and a couple of library-packages (aptitude will install them for you)
  - make
  - sudo make install
  - sudo make hotplug-install
- add a PPD (Postscript Printer Description) file that is suited for LaserJet 1020
  - cd /usr/share/ppd/HP
  - sudo bash
    - cp *HP*1005*ppd.gz HP-LaserJet_1020-foo2zjs.ppd.gz
    - gunzip *1020*ppd.gz
    - vim (or any other editor) *1020*ppd and replace all occurances of "1005" with "1020"
    - gzip *1020*.ppd
    - exit (leave "root bash")
- restart cupsys (sudo /etc/init.d/cupsys restart)
- restart the printer
- add the printer (menu System -> Administration -> Printers)
  - the printer should be identified automatically
```

Enjoy[/QUOTE]
I confirn. But in dapper the only thing you have to do is to remove foo2zjs and compile the one from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/). Just follow Download and Install instructions and your hp 1020 will load firmware automatically and work without any problems. Thanks dapper team for forcing me to spend some hours on solving this problem:)

---

### Post by Archarius on 2006-06-02
Hello
I`m new in linux and have the same problem with hp 1020 on Dapper 6.06
I`ve installed drivers from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) but without uninstalling the built-in ones. 

So my question is: how can I uninstall 'original' drivers (provided with kubuntu) and later uninstall drivers that I made (I suppose that they won`t work anyway) to make space for a new compilation and instalation?

---

### Post by k.mankiller on 2006-06-10
Yeah, I had this printer working in Breezy, and then I upgraded.  :(  The printer is no longer detected.

---

### Post by k.mankiller on 2006-06-11
Never mind.  It's working now.  I had to reinstall from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and ignore the instructions I used to get it working under Breezy.

---

### Post by cohenzd on 2007-05-18
I have a question for all of you clearly more adept at all of this than I am: I'm using these drivers with my laserjet 1020 and trying to print using a custom size: a 3 X 5 index card size. I know the printer supports this size, but cannot figure out how to configure the printer. Any help would be appreciated, 
Thanks,
            -Z

system info if it matters: macbook pro 2.33 intel core 2 duo, running mac os x version 10.4.9 - using microsoft word 2004 for mac, version 11.3.5, printer: hp laserjet 1020, using foomatic.

---

### Post by lancest on 2007-05-18
[http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/](http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/)
This works!!! I have used this method on laptop and desktop with my HP Laserjet 1020. Its was joy when I found it 2 months ago! Finally my 1020 under Linux. Happy days.

---

