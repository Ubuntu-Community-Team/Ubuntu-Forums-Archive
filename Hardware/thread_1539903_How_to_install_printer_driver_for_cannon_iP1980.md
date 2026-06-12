---
title: "How to install printer driver for cannon iP1980?"
date: 2010-07-27
forum: Hardware
---

### Post by mahela007 on 2010-07-27
I've googled for this topic can come up with two different methods of doing it. 
here 
[http://www.dedyisn.net/2009/04/install-printer-canon-pixma-ip1980-in-ubuntu-904/](http://www.dedyisn.net/2009/04/install-printer-canon-pixma-ip1980-in-ubuntu-904/)

and here
[http://all-about-ubuntu.blogspot.com/2008/12/canon-ip1880-ip1700-ip1980-printer.html](http://all-about-ubuntu.blogspot.com/2008/12/canon-ip1880-ip1700-ip1980-printer.html)

Both these seem to be a bit hazy (to me) so I would really appreciate it if someone could clarify this for me.. thanks

EDIT: 
I tried downloading the deb file for the driver and 'double clicking to install'. However, it says it needs a dependency called libcupsys2 and neither can I install this libcupsys2.

First I tried 
dpkg -i ~/Desktop/<name of driver_deb_file>

That gave 
```

Selecting previously deselected package cnijfilter-ip1900series.
(Reading database ... 198745 files and directories currently installed.)
Unpacking cnijfilter-ip1900series (from cnijfilter-ip1900series_3.00-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-ip1900series:
 cnijfilter-ip1900series depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
 cnijfilter-ip1900series depends on cnijfilter-common (>= 3.00); however:
  Package cnijfilter-common is not installed.
dpkg: error processing cnijfilter-ip1900series (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-ip1900series
mahela007@Ubuntu-panora:~/Desktop$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cnijfilter-ip1900series: Depends: libcupsys2 (>= 1.2.1)
                           Depends: cnijfilter-common (>= 3.00) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Then I tried sudo apt-get install libcupsys2 which returned 
```


mahela007@Ubuntu-panora:~/Desktop$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cnijfilter-ip1900series: Depends: libcupsys2 (>= 1.2.1)
                           Depends: cnijfilter-common (>= 3.00) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by hansdown on 2010-07-27
Hi mahela007.

Try this.

```
sudo apt-get -f install
```

---

### Post by ronnielsen1 on 2010-07-27
[http://ubuntuforums.org/showthread.php?t=1493787](http://ubuntuforums.org/showthread.php?t=1493787)

[http://www.dedyisn.net/2009/04/install-printer-canon-pixma-ip1980-in-ubuntu-904/](http://www.dedyisn.net/2009/04/install-printer-canon-pixma-ip1980-in-ubuntu-904/)




I couldn't find anything for 10.04 but this should work

---

