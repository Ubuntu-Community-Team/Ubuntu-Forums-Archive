---
title: "cant get wireless scanner cannon ts6060 working"
date: 2018-01-28
forum: Hardware
---

### Post by camman2000 on 2018-01-28
Hi I need so assistance I have a cannon printer scanner pixima ts6060
using ultimate 5.1 based on ubuntu and kde, 

I have the printer working ok (wireless) but can not get the scanner to work
I have tried installing scangear2 program package from cannon
I would like sane or another gui scan program to work without having to use the terminal to do a scan.
xsane scanner not recognising scanner
any advice on what to do?
Thanks
Chris

I have searched the Internet but find instructions too complicated to set up scanner program.

---

### Post by pdc on 2018-01-28
so Chris: that looks a very fine printer/scanner you have there; 

the hard-working volunteers at SANE; who provide the back-end; that drives the graphical front-ends like xsane and simple scan;

they need testers to get the TS6000 series working: [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) ........ so sane doesn't work at present ...........

____________

so sounds like ScanGearMP worked well .. you can create a launcher for it from here [http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)
the commands are 
```
sudo apt-get install gnome-panel
``` and 
```
gnome-desktop-item-edit ~/Desktop/ --create-new

```

and the link says [HTML]In the launcher-creation window choose the type and location of the target. Click OK.[/HTML] so maybe save it to your Desktop and whatever name you wish

__________

back to SANE; the open-source way to get the scanner scanning ........ 

You can help the linux community; that is full of volunteers: by going here [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel) and joining the mailing-list; they are very friendly and helpful folks; you have the hardware; they have the software abilities; an excellent match; they need testers; please help them; and let us know how it goes; then you can get your scanner working on sane

---

