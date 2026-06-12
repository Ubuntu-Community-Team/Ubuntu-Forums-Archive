---
title: "got this message after trying to do this:::::"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by nnebular22 on 2009-01-17
i went to this site and tried this:
[http://flavor8.com/index.php/2006/03/26/how-to-back-up-your-dvds-in-ubuntu](http://flavor8.com/index.php/2006/03/26/how-to-back-up-your-dvds-in-ubuntu)

and got this:



Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.' 




what happened how do i fix this?

---

### Post by nnebular22 on 2009-01-17
heres the results after i followed the instructions from the site....





benn@karen-laptop:~$ sudo su -c 'echo deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free >> /etc/apt/sources.list'
benn@karen-laptop:~$ sudo su -c 'echo deb deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free >> /etc/apt/sources.list'
benn@karen-laptop:~$ sudo apt-get update
E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)
benn@karen-laptop:~$ sudo apt-get install libdvdcss2 libdvdread3-dev mkisofs dvdbackup dvdauthor transcode lsdvd
E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
benn@karen-laptop:~$ wget [http://www.flavor8.com/dvd/streamanalyze_0.4-9_i386.deb](http://www.flavor8.com/dvd/streamanalyze_0.4-9_i386.deb)
--16:24:43--  [http://www.flavor8.com/dvd/streamanalyze_0.4-9_i386.deb](http://www.flavor8.com/dvd/streamanalyze_0.4-9_i386.deb)
           => `streamanalyze_0.4-9_i386.deb.4'
Resolving [www.flavor8.com](www.flavor8.com)... 208.97.191.106
Connecting to [www.flavor8.com|208.97.191.106|:80](www.flavor8.com|208.97.191.106|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,160 (9.9K) [text/plain]

100%[====================================>] 10,160        40.11K/s             

16:24:44 (39.95 KB/s) - `streamanalyze_0.4-9_i386.deb.4' saved [10160/10160]

benn@karen-laptop:~$ wget [http://www.flavor8.com/dvd/streamdvd_0.4-9_i386.deb](http://www.flavor8.com/dvd/streamdvd_0.4-9_i386.deb)
--16:24:44--  [http://www.flavor8.com/dvd/streamdvd_0.4-9_i386.deb](http://www.flavor8.com/dvd/streamdvd_0.4-9_i386.deb)
           => `streamdvd_0.4-9_i386.deb.4'
Resolving [www.flavor8.com](www.flavor8.com)... 208.97.191.106
Connecting to [www.flavor8.com|208.97.191.106|:80](www.flavor8.com|208.97.191.106|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 62,802 (61K) [text/plain]

100%[====================================>] 62,802        93.79K/s             

16:24:45 (93.64 KB/s) - `streamdvd_0.4-9_i386.deb.4' saved [62802/62802]

benn@karen-laptop:~$ sudo dpkg -i streamdvd_0.4-9_i386.deb
(Reading database ... 178181 files and directories currently installed.)
Preparing to replace streamdvd 0.4-9 (using streamdvd_0.4-9_i386.deb) ...
Unpacking replacement streamdvd ...
Setting up streamdvd (0.4-9) ...
benn@karen-laptop:~$ sudo dpkg -i streamanalyze_0.4-9_i386.deb
(Reading database ... 178181 files and directories currently installed.)
Preparing to replace streamanalyze 0.4-9 (using streamanalyze_0.4-9_i386.deb) ...
Unpacking replacement streamanalyze ...
Setting up streamanalyze (0.4-9) ...
benn@karen-laptop:~$ wget [http://www.flavor8.com/dvd/DVD-Duplicator.gz](http://www.flavor8.com/dvd/DVD-Duplicator.gz)
--16:24:46--  [http://www.flavor8.com/dvd/DVD-Duplicator.gz](http://www.flavor8.com/dvd/DVD-Duplicator.gz)
           => `DVD-Duplicator.gz.3'
Resolving [www.flavor8.com](www.flavor8.com)... 208.97.191.106
Connecting to [www.flavor8.com|208.97.191.106|:80](www.flavor8.com|208.97.191.106|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,453 (3.4K) [text/plain]

100%[====================================>] 3,453         --.--K/s             

16:24:46 (25.56 KB/s) - `DVD-Duplicator.gz.3' saved [3453/3453]

benn@karen-laptop:~$ gunzip DVD-Duplicator.gz
gzip: DVD-Duplicator already exists; do you wish to overwrite (y or n)? y
	not overwritten
benn@karen-laptop:~$

---

### Post by cariboo on 2009-01-17
Open /etc/apt/sources.list in gedit, enable line numbering and fix line 59. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

This will open the text editor as root,so that you can edit and save the file. To enable line numbering got to Edit-->Preferences-->Line Numbers.

That tutorial is rather old, the best way to enable the Medibuntu repositories is to go [here]("http://help.ubuntu.com/community/Medibuntu") and follow the instructions.

Jim

---

### Post by nnebular22 on 2009-01-17
then when i tried going in package manager i got this error message:

E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by nnebular22 on 2009-01-17
cariboo907..... what do i do after i do that?

---

### Post by nnebular22 on 2009-01-17
sorry.....  noob here...

---

