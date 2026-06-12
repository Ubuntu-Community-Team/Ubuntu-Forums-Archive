---
title: "Upgraded to 14.04 from 13.03 and my MP230 canon printer stopped working"
date: 2014-05-08
forum: Hardware
---

### Post by o-l-lewinsohn on 2014-05-08
I ment 13.10 of course =P
I tried deleting and reinstalling the printer through gnome 3 setting and through the cup administration interface, tried to download them again from the web and googeled a lot in hope to find some information. Nothing seems to work, with the normal drivers (3.80 from their site)
it will endlessly print blank pages, though test pages are printed just fine. 

With the driver which comes with ubuntu (CUPS Gutenprint 5.2.10-pre something) the printer may make some noises but nothing other than that.

It did work without any problem what so ever before the upgrade. 

Any ideas how I could find out whats wrong and whether it could be somehow solved?

Been using linux for more than 10 years and I program for a living, so feel free suggesting some more creative ideas as well. Sometimes I just want things to work without all that trial and error =/

---

### Post by pdc on 2014-05-08
Can I suggest you try the Canon drivers: from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465901.html)

It comes down as a compressed debian package cnijfilter-mp230series-3.80-1-deb.tar.gz

___________________

commands to install would be 

cd Downloads
tar -zxvf cnijfilter-mp230series-3.80-1-deb.tar.gz
cd cnijfilter-mp230series-3.80-1-deb
./install.sh

_____________________

.....it may need libtiff4............... you can check before install if you have this already installed (as I am sure you already know) by > dpkg -l | grep libtiff4

It seems to have left the ubuntu repositories in 14.04 but can be found in the debian repositories 

[ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)           ..............just choose which version is good for you ......

__________--

I hope we can get your printer going again (Canon also provide scanning drivers) [http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469501.html)

---

### Post by o-l-lewinsohn on 2014-05-08
Like I said I have those installed and I even tried to download them again and reinstall, doesn't seem to help, thanks for the replay though =)

---

### Post by tgalati4 on 2014-05-08
Send some feedback to Canon.  Check the log files in /var/log/cups for clues.  I'm guessing there is a regression in 14.04.  Ten years of linux experience will teach you--don't mess with a working system.

---

### Post by o-l-lewinsohn on 2014-05-08
Went through the log though haven't spent enough time trying to figure out the problem yet, anyhow I'll surly contact canon as well.
I guess I should have made a new installation and only migrate to it after everything was running smoothly, oh well...

---

### Post by pdc on 2014-05-08
Canon give their contact as <sup-debian@list.canon.co.jp> (quoted in various readme.txt files)

_______________________

one can also print directly from command line with > lpr -P MP230USB [filename] {-o option}

[http://linuxcommand.org/man_pages/lpr1.html](http://linuxcommand.org/man_pages/lpr1.html) suggests -D as debugoptions   Debugging  is  controlled  using  the -D option. This accepts a comma-separated list of debugging settings. These settings take one of two forms: facility=value, or value to set an overall default value.

---

### Post by o-l-lewinsohn on 2014-05-09
I'm happy to say the printer works right now (on 14.04) with the normal drivers from canon with no problem including scanning of course.
I have no Idea what the problem was though. I just reinstalled Ubuntu which was a lot faster than to keep looking for the source of the problem and I needed to solve that problem quickly, thanks for the help =)

---

### Post by pdc on 2014-05-09
glad this is working: as *initiator of the thread*, you can add **SOLVED** to the title with thread tools.........................reassuring to hear the Canon drivers are fine; alarming to think that our initial recommendation to you should have been: just wipe what you have and re-install;

---

