---
title: "Canon iP1600 in Feisty."
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by kaj on 2007-05-04
I have installed 7.04 Feisty Fawn and I wanted to ad my printer with the help of this site:

[http://forum.ubuntu-fr.org/viewtopic.php?id=61554](http://forum.ubuntu-fr.org/viewtopic.php?id=61554)

But it seems, that it doesn't work.

I once installed the same printer in 6.06 Dapper Drake using the same tutorial, and it went fine.

In the meantime it seems, that canon have closed the driver site, but I had them on a pen-drive, so that was no problem.
I installed the deb-packages with dpkg -i, I made the symbolic link, did the ldconfig and restartet cupsys without problems.
But when i was adding the printer, the driver was not found.

Do I have to follow another procedure in Feisty?

Afterwards I did the same installation in MEPIS 6.5, and it went fine without any problems at all.

Could anyone give me a hint of what to do?

Kaj
from Denmark

---

### Post by ramjet_1953 on 2007-05-05
This link may help:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600)

This may also help, as it lists a driver for the ip1500, which may be compatible:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Of course, you can always download the TurboPrint demo, to make sure it works OK for you. The full version is not free, but heaps cheaper than buying a new printer.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Regards,
Roger :cool:

---

### Post by kaj on 2007-05-05
I followed the instructions on linuxprinting.org

As I mentioned, I have previously got to work in Ubuntu 6.06, but here i 7.04 Feisty the driver wasn't autodetected as it was supposed to be.

By the way, now it seemes, that I have solved the problem.
I clicked on the button for installing a .ppd driver, and after a lot of searching, I found this:
/usr/share/cups/model/canonip2200.ppd and it was accepted.

I can print a test side, and I can print from Openoffice, but I haven't tried in other applications yet.

Kaj

---

### Post by arzanulhaq on 2007-06-27
I can use ip1600 in Feisty with this manual [http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html]("http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html").
I hope it's work for others.
Sorry for my bad English.

---

### Post by HappyBird on 2007-07-01
I've also followed the instructions from: [http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html](http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html)
and . . . .  it worked for me.:p:p
Many thanks to : Iffan Arzanul Haq :popcorn:

---

### Post by mrwilloby on 2007-07-26
I followed the instructions from 

[http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html](http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html)

as well, and there seems to be a problem...

On the CUPS page I get this message next to the name of the printer:

"Filter "pstocanonij" for printer "iP1600" not available: No such file or directory"

I've installed the files twice, but I don't know how to remove the .deb installation. How can I completely remove those files to try again?

Also, does anyone know how to remove the TurboPrint drivers? I have no use for them when they print that logo all over everything. Purchasing a license would be twice as much as I paid for this printer.

Thanks,
–Tommy

---

### Post by mrwilloby on 2007-07-28
**UPDATE:** I was able to get my printer working by basically following this document

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

**EDIT:** When I said basically, this is what went differently:

In Step 6 this happened (probably because of all the other things I have been trying):

```
. . .$ sudo dpkg -i *.deb
Selecting previously deselected package cnijfilter-common.
(Reading database ... 138863 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_2.60-2_i386.deb) ...
Selecting previously deselected package cnijfilter-ip2200.
Unpacking cnijfilter-ip2200 (from cnijfilter-ip2200_2.60-2_i386.deb) ...
dpkg: error processing cnijfilter-ip2200_2.60-2_i386.deb (--install):
 trying to overwrite `/usr/lib/libcnbpess256.so.2.2.2', which is also in package libcnbj-2.6
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Setting up cnijfilter-common (2.60-2) ...
Errors were encountered while processing:
 cnijfilter-ip2200_2.60-2_i386.deb
```

So I did this before running Step 6 again:

```
. . .$ sudo aptitude remove libcnbj-2.6
```

In Step 7 I have a feeling this part is wrong:

> 
and /usr/lib/libxml2.so.2 should point to /usr/lib/libxml.so.1 If not, type:

```
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 
```


because I got this message:

```
. . .$ sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
ln: creating symbolic link `/usr/lib/libxml.so.1' to `/usr/lib/libxml2.so.2': File exists
```

At that point, after trying to fiddle with those files a bit, I just ignored it and continued and everything worked fine. I was able to print a test page from [http://localhost:631/printers/iP1600](http://localhost:631/printers/iP1600) and also a page from OpenOffice.org Writer.

---

### Post by leicester on 2007-08-13
hi guys. im a new convert to ubuntu and any help would be greatly appreciated. Can someone help me install canon ip1600 in 64bit feisty? i tried everything but nothing seems to work....

---

### Post by Tech Provider on 2007-09-08
I manage to get this printer to work on Feisty.
Run step by step the commands on this page : [LINK]("http://didier.misson.net/didier/index.php?2006/11/20/25-ubuntu-610-et-imprimante-canon-pixma-ip-1600").
Use Google to translate the link if you want in english.

At the last step .. I used sudo instead of the simple command.

**sudo /etc/init.d/cupsys restart**

In Feisty the driver is not added to the driver list by default. 
Go to System - >Administration->Printing - >New Printer -> Select your iP6000 detected printer ,->Forward->Install Driver 

Go to /usr/share/cups/model/canonip2200.ppd and select the ppt file for iP2200 Ver.2.60.
Finish the installation.

---

### Post by leicester on 2007-09-26
i cant translate the site in google... :(

---

### Post by leicester on 2007-09-26
well that instruction was for 32 bit ubuntu.. i really have to know if someone was able to install ip1600 in a 64 bit feisty

---

### Post by natureboy on 2007-11-06
I'm having the same problem with Gutsy amd64. Alien says that the Canon RPMs are for ia32 and won't convert them.
I'm pretty sure that there is some way to run 32 bit apps/drivers in a 64 bit OS. Has anyone tried that?

---

### Post by Seisen on 2007-11-06
Good luck with that that is why I don't use 64-bit Ubuntu on my laptop because I couldn't get the printer drivers to work with my laptop, they were for the iP1500 drivers.

---

### Post by natureboy on 2008-02-11
It's been a while....
It looks like it should be possible to convert the ip2200 RPM file to a deb file using alien, on a 32 bit machine. Then the deb file can be installed on 64 bit using "dpkg -i --force-architecture"
But I haven't tried it yet.

---

### Post by natureboy on 2008-02-28
Bum, it didn't work. I think the ip2200 driver wants to access gtk and png libraries, and those being amd64 are probably not working with the driver.

I am starting to think that my next printer will not be a Canon....

---

