---
title: "can't install a HP PSC 500"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by vishnoo on 2005-06-07
Hello,

I d'like to install a HP PSC 500 on my parents computer (with a ubuntu hoary :) ) but I don't managed to get it detected either with the gnome printer setup tool nor with hpoj.

According to [www.linuxprinting.org](www.linuxprinting.org) it should "work perfectly".
And indeed in the gnome printer setup, if i choose parallel port #1 I can choose HP PSC 500 and i even have the choice between a bunch of drivers. But my printer doesn't print anything with this :(

I also tried to configure it with hpoj but "no device found", and finally i downloaded and compiled hpoj from source and used it's "ptal-init", but it's exactly the same :(

In my /var/log/messages I see this :
```

Jun  7 19:38:46 localhost ptal-mlcd: SYSLOG at ExMgr.cpp:3512, dev=<mlc:par:probe>, pid=20736, e=2, t=1118165926         Using parallel port '-porttype ecphw -base 0x378 -basehigh 0x778'.
Jun  7 19:38:46 localhost ptal-mlcd: SYSLOG at ExMgr.cpp:652, dev=<mlc:par:probe>, pid=20737, e=2, t=1118165926        ptal-mlcd successfully initialized.

```

My printer is *on* (  ;-)  ), my /dev/lp0 seems to work well according to dmesg, parport modules are present, and the printer works as is on windows.

Anyone would have some advice on what could I do ?
It's quiet annoying for me, as my parents and my sister use it and like it, and I don't want them to switch back only because they can't print....  ]

PS:
If I remember well, I already printed with It on Knoppix : maybe it would be a clue to get the configuration ?

---

### Post by David Haas on 2005-06-07
The HP Linux Web site ([http://hpinkjet.sourceforge.net/productsmf.php](http://hpinkjet.sourceforge.net/productsmf.php)) states that the backend (PPD file) for the PSC 500 is hpijs. Ubuntu Hoary has this file at /usr/share/cups/model/foomatic-ppds/HP. So, I'd start over by deleting the HP PSC 500 and selecting "New Printer" in the printer-manager GUI, selecting the HP PSC 500 (again) in the HP list, and selecting the ppd file (HP-PSC_500-hpijs.ppd.gz
) after clicking through the files to HP in the GUI. I've found that if one doesn't select correctly, it's best to begin anew. Once the ppd file is selected, Ubuntu places an unzipped copy in /etc/cups/ppd. I hope this helps.
David

---

### Post by ericBAEZ on 2006-02-06
hi, i installed really easy this printer, but the scanner doesnot work, do you have any suggestion to check? i installed hplip, checked the conf, but the scanner is not work

---

### Post by mpgarate on 2007-03-22
I am also having trouble installing this printer. It is not auto-detected, and when I select the proper driver It still will not print.

---

### Post by theRevMom on 2007-03-22
I have a different printer, but have had similar problems.  Here's a couple of things I did to work around it.

Check the printer properties interface (I right clicked the printing icon in the top panel after trying to print a test page).  There's an error message there?  

Check your permissions in CUPS and Foomatic-rip  [Here's ]("http://www.ubuntuforums.org/showthread.php?t=385231&highlight=permission+printer")link on how to do that.

Check also your permissions on your USB0 (or whichever one the printer is plugged into).  
 
I have the scanner working (using hplip), the fax from the computer, but, I get nothing on the printing. Not even an error code.  I'm getting ready to completely reinstall Edgy.  I've done so many things to straighten the printer out that I've messed up too much to fix it.  Another learning experience!  At this rate I'll either be an expert or give up before long!

---

