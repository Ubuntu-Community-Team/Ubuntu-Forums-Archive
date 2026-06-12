---
title: "can't print to HP F4280 printer"
date: 2008-08-12
forum: General Help
---

### Post by pytheas22 on 2008-08-12
I bought an HP F2480 printer.  When I plugged it into Ubuntu 8.04, a bubble popped up saying that drivers had been installed, and I thought everything would be great.

Unfortunately, when I try to print anything, it doesn't work.  The job gets sent to the print queue, where it's listed as "processing" for a few seconds, and then it changes into "completed."  But nothing happens on the printer--nothing prints, and nothing even flashes or moves; the printer just sits there idle.  However, Ubuntu seems to think that the job printed without a problem, as it doesn't mention any errors--the job just moves to the "completed" list.

When I run the utility for printer configuration at System>Administration>Printing, it finds the printer.  But if I run "hp-setup" and tell it to detect connected USB printers, it says that none are connected.  XSane also doesn't detect any scanners (this printer also has a scanner), so it's almost as if the system doesn't really think that the device is present.  It does show up in lsusb, though, and I've tried plugging into different USB ports, all with the same results.

The printer works on Windows on the same computer, so I've ruled out hardware problems.

I googled for "ubuntu hp4280" and couldn't find anyone who had had problems with this device, so I don't understand why I can't get it to work.  I have a lot of experience with Ubuntu, but I've never had to troubleshoot a printer before.  If anyone could help me figure out what's going on, I'd really appreciate it.

This printer isn't for me, and if I can't get it to work on Ubuntu within a few days, the person who needs it is going to have to to use Windows again, which neither he, nor I, nor any of us want.  So any suggestions are very very welcome.  Thanks in advance.

EDIT: I finally got it to work by running the hplip setup automatic installer from [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html).  I don't know why the build of hplip that ships with Ubuntu didn't work, but the one from the hplip site is good.  After running it, hp-setup was able to detect my printer, and everything appears to work (including the scanner in XSane).

---

### Post by sportman1280 on 2008-08-17
I had the same issue.  I am currently trying the hp-lip from sourceforge.  Hoping it works.  Its a shame we have to do it this way though :(.

---

### Post by pytheas22 on 2008-08-18
Yeah, I was disappointed  too--I specifically chose this HP printer because I thought it would "just work."  I googled it beforehand and didn't find anyone who had issues with it on Linux.

But recompiling hplip definitely solved the problem for me (scanner also works great now), so if you still have trouble, let me know.

---

### Post by neba on 2008-10-28
I have the same printer, and I can't get it to work. I have tried the hplip, and that just told me that it can't find any printers on the usb. ? 
Thanks
Neba

---

### Post by pytheas22 on 2008-10-28
Neba: did you use the 'automatic installer' from hplip's site?  And are you sure your printer was connected to a working USB port (run the 'lsusb' command to make sure the computer can see something attached...it's possible that your USB connection was shot).  There should also be an option during the hplip setup to specify manually the address of the printer (which you can also figure out by using 'lsusb'); you may want to try that.

If you still can't figure it out, let us know.  Also, you may want to try using Ubuntu 8.10, which will hopefully have real out-of-the-box support for this printer.

---

### Post by silverhair on 2008-12-23
I have tried everything I can think of to get this printer [ HP F4280 ] to work.  When I ran ubuntu 8.10 as a Live CD the printer worked great. After I installed 8.10 the printer stopped working.  I then ran in HPLIP 2.8.12, this allowed me to print a test page.  Looked great. Now when I try to print from OO word, it says it is printing and then that the job is complete. But no output to the printer. To say the least this is giving me more silverhair.

Please help  

Silverhair

---

### Post by pytheas22 on 2008-12-23
silverhair: that's weird behavior.  Have you tried printing from other applications besides OO--perhaps the failure to print is OO-specific.  Also, make sure that the USB cable is firmly connected on both ends.

Can you use the scanner successfully?

I haven't tried this printer with Ubuntu 8.10--my brother who uses the printer at school still runs 8.04, where things have worked fine for the last several months since I installed the hplip driver--so I don't know  what might have changed since then.

---

### Post by dgerwin11 on 2008-12-23
I had most of these same issues with 8.04.  however after upgrading to 8.10 things just worked. I have HP F4240

But I am having trouble printing spreadsheets from OO.  My work around was to go back to using Google Docs for my spreadsheets

---

### Post by pytheas22 on 2008-12-23
> But I am having trouble printing spreadsheets from OO. My work around was to go back to using Google Docs for my spreadsheets

You could also print to pdf, then open in Document Viewer and print from there.

Also, maybe upgrading to OO 3.0 would make a difference.

Just a couple of thoughts...

---

### Post by silverhair on 2008-12-24
I have tried the text editor still no lock

---

### Post by pytheas22 on 2008-12-24
> I have tried the text editor still no lock

Can you scan?  Also, if you go through the hplip install again, does it solve things?

---

### Post by silverhair on 2008-12-24
> **pytheas22 said:**
> Can you scan?  Also, if you go through the hplip install again, does it solve things?


Thank You  after I did a reinstall from the 8.10 disk I was able to get the printer running.  I had to set the default printer to Deskjet-4200 from Deskjet Plus.

---

### Post by stanjest on 2008-12-25
The hplip-2.8.12.run works great. The printer even works in Open Office.
Thanks a lot to the guys/gals that created this package for us newbies

---

### Post by Littlejohn on 2009-01-10
speaking of newbies, how do we run the hplip-2.8.12.run?

I've never heard of a .run yet.

Jean.

---

### Post by pytheas22 on 2009-01-10
```
speaking of newbies, how do we run the hplip-2.8.12.run?

I've never heard of a .run yet.

Jean.
```

I think it's just a bash file, but I could be wrong.  Try cd'ing into the directory where it's located (for example, if it's on your desktop, type 'cd ~/Desktop'), then type:
```

sudo sh hplip-2.8.12.run
```

I think that would work.  If it doesn't, try:
```

sudo chmod +x hplip-2.8.12.run
sudo ./hplip-2.8.12.run
```

Let me know if this doesn't work.

---

### Post by Chica-D on 2009-10-12
hi i have the same problem with the f2480 hp printer and i went on the hplp url you (pytheas22) recommended, however, it does not appear to support this model of hp all in one. i have ubuntu version 9.04, would that make a difference in which ones they support? i shouldnt think so though...did you choose another printer model on the installation wizard to get it working? pls if anyone has some advice i would be rly grateful..thanks. p.s this is rly frustrating :(

---

### Post by pytheas22 on 2009-10-12
Chica-D: I think hplip should support your model, and [this thread]("http://forums.linuxmint.com/viewtopic.php?f=51&t=34094&p=197063") seems to imply that it will.  Did you actually try installing it or are you just worried because your model isn't mentioned on the website?  Are you able to see a printer at all if you go to System>Administration>Printing and configure a new printer?

Also, if this is a USB printer, what is the output of:
```

lsusb
```

when the printer is connected and turned on?

---

### Post by arjang60 on 2009-11-24
> **Chica-D said:**
> hi i have the same problem with the f2480 hp printer and i went on the hplp url you (pytheas22) recommended, however, it does not appear to support this model of hp all in one. i have ubuntu version 9.04, would that make a difference in which ones they support? i shouldnt think so though...did you choose another printer model on the installation wizard to get it working? pls if anyone has some advice i would be rly grateful..thanks. p.s this is rly frustrating :(


I just installed the F2480 on ubuntu 9.04 and all went well. Go to [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) and then answer the 5 steps. At step 4 you will see that HP Deskjet F2480 All-In-One printer is selectable. From there follow the rest of the instructions and it all will be working.

---

