---
title: "NEW Canon Printer Problem"
date: 2010-08-06
forum: Hardware
---

### Post by gallifrey on 2010-08-06
Hi all,
        havig struggled for nearly a week to get my Canon Pixma ip1900 to work on Ubuntu, I finally did, thanks to this forum. Extracted drivers, changed references to libcupsys2, changed filter permissions, dpkg -i --force-architecture (I'm on 64 bit), etc. And it worked wonderfully. Until last week. 

Now, when I try and print, I get nothing. Zip. Just a message in Printing:

/usr/lib/cups/filter/pstocanonij failed

pstocanonij is present in the directory. I haven't, to my knowledge changed anything. I have reinstalled the drivers, restarted cups, but to no avail. 

Anybody have any ideas?? I really need to get this going. I would get a more linux friendly printer, but I am on a tight budget for the time-being. 

Would be most grateful for assistance! :popcorn:

---

### Post by gallifrey on 2010-08-06
Update: 

Tried adding the printer via the Cups server (localhost:631). 

Problem persists, but this time I checked the error log, and found these messages:

/usr/lib/cups/filter/pstocanonij: No such file or directory
(/usr/lib/cups/filter/pstocanonij) stopped with status 22!

I have checked, the file is definitely present where it should be, and also appears in /lib64. Permissions are set correctly. 

I am at my wits end. Incidentally, I tried this on my desktop (running 10.04 i386), and it works fine, so this seems to be an amd64 issue. 

Any ideas??

---

### Post by utilitytrack on 2010-08-06
Is simple idea: in last cups server release somethings is broken (it's my guess). Conclusion: fallback to previous version. Also post here [FONT="Courier New"]dpkg -l *cups*[/FONT]

---

### Post by gallifrey on 2010-08-06
> **utilitytrack said:**
> Is simple idea: in last cups server release somethings is broken (it's my guess). Conclusion: fallback to previous version. Also post here [FONT=Courier New]dpkg -l *cups*[/FONT]

I already rolled back the cups version to the one that originally came with 10.04, but the problem remained. Sorry, I should have mentioned that. Here is the output to dpkg -l *cups* :

>  ||/ Name           Version        Description
+++-==============-==============-============================================
ii  bluez-cups     4.60-0ubuntu8  Bluetooth printer driver for CUPS
ii  cups           1.4.3-1ubuntu1 Common UNIX Printing System(tm) - server
ii  cups-bsd       1.4.3-1ubuntu1 Common UNIX Printing System(tm) - BSD comman
ii  cups-client    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - client pro
ii  cups-common    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - common fil
ii  cups-driver-gu 5.2.5-0ubuntu1 printer drivers for CUPS
un  cups-pdf       <none>         (no description available)
un  cups-ppdc      <none>         (no description available)
un  cups-pt        <none>         (no description available)
un  cupsddk        <none>         (no description available)
un  cupsddk-driver <none>         (no description available)
un  cupsomatic-ppd <none>         (no description available)
un  cupsys         <none>         (no description available)
un  cupsys-bsd     <none>         (no description available)
un  cupsys-client  <none>         (no description available)
un  cupsys-common  <none>         (no description available)
un  cupsys-driver- <none>         (no description available)
ii  ghostscript-cu 8.71.dfsg.1-0u The GPL Ghostscript PostScript/PDF interpret
un  hal-cups-utils <none>         (no description available)
un  hplip-cups     <none>         (no description available)
ii  libcups2       1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Core libra
ii  libcupscgi1    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - CGI librar
ii  libcupsdriver1 1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Driver lib
ii  libcupsimage2  1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Raster ima
ii  libcupsmime1   1.4.3-1ubuntu1 Common UNIX Printing System(tm) - MIME libra
ii  libcupsppdc1   1.4.3-1ubuntu1 Common UNIX Printing System(tm) - PPD manipu
un  libcupsys2     <none>         (no description available)
ii  libgnomecups1. 0.2.3-3build2  GNOME library for CUPS interaction
ii  python-cups    1.9.49-0ubuntu Python bindings for CUPS
ii  python-cupshel 1.2.0+20100408 Python modules for printer configuration wit
un  python2.6-cups <none>         (no description available)


---

### Post by utilitytrack on 2010-08-06
I see cups v1.4.3 packages in your system. But it's not fallback. On the contrary cups v1.4.1 (that is from karmic) it's fallback.

---

### Post by gallifrey on 2010-08-06
> **utilitytrack said:**
> I see cups v1.4.3 packages in your system. But it's not fallback. On the contrary cups v1.4.1 (that is from karmic) it's fallback.

Oh, I know. After rolling back to 1.4.1 (and 1.3.9), and not getting anywhere, I reinstalled 1.4.3.

This only seems to be affecting the 64 bit, as I am running it on Ubuntu 32-bit, and all is fine. When I first installed the printer on my 64-bit machine, it was fine also. this problem has only existed a week or so.

---

### Post by utilitytrack on 2010-08-06
Drivers for your printer are 64-bit? What drivers do you use?

---

### Post by gallifrey on 2010-08-06
> **utilitytrack said:**
> Drivers for your printer are 64-bit? What drivers do you use?

No, I use the 32 bit drivers, with dpkg -i --force-architecture. It worked fine for me through Karmic 64 and Lucid 64, up until last week. I didn't change anything, that I can remember. 

It just seems to have stopped 'seeing' the pstocanonij file, for some odd reason.

---

### Post by utilitytrack on 2010-08-06
*(aside)*

Do you mix 32- and 64-bit software? Well, it means then that your processor (it's probable AMD64) constantly use a legacy mode (32-bit) and never switch to long mode (really 64-bit). Then what for you use 64-bit distribution? I don't understand. Migrate to general 32-bit distro and you will see that troubles ended.

---

### Post by gallifrey on 2010-08-06
> **utilitytrack said:**
> *(aside)*

Do you mix 32- and 64-bit software? Well, it means then that your processor (it's probable AMD64) constantly use a legacy mode (32-bit) and never switch to long mode (really 64-bit). Then what for you use 64-bit distribution? I don't understand. Migrate to general 32-bit distro and you will see that troubles ended.

Ah, I see. Well, the only 32 bit software I use would be the Canon drivers. I use 64-bit distribution because of my RAM, which is currently 8GB. I used to use 32-bit with PAE enabled, but I find 64-bit is much faster for video encoding.

---

### Post by utilitytrack on 2010-08-06
Oh, I don't know that you have 8GB RAM. Then I see it all.

---

