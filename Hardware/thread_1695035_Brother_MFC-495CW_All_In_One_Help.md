---
title: "Brother MFC-495CW All In One Help"
date: 2011-02-25
forum: Hardware
---

### Post by roof_top_eagle on 2011-02-25
Hi Linux Peeps! :D

I've been using Ubuntu for a while and was my first exposure to Linux and has been the only distro I've used with any consistency other than trying others out.I guess you could say Ubuntu took my Linux virginity!

Well here is my problem I am hoping you guys can help me with as my first real need for tech support in almost a year of full time use of Ubuntu.

I've got a Brother MFC-495CW, I got it with my last computer at a decent price but I can't get it to print with Ubuntu 10.10 or 10.04.

I've tried all the threads I could find on getting this printer to work and while some users have reported success (if my memory serves me right) I haven't been able to get it to work.

My PC specs in case they can help us figure this out is as follows:

Toshiba Satellite L500 Laptop
4gb RAM
640GB hard drive

I am running Ubuntu 10.10 Maveric
Kernel Linux 2.6.35-25-generic-pae
Gnome 2.32.0

If you need any more information please don't hesitate to ask!

---

### Post by alenis on 2011-02-25
Brother has a Liunx driver for your printer, did you try it? I have a Brother printer too, although a different model. It works well enough with the Brother driver but works much better with the HP PCL driver.

---

### Post by TomSerato on 2011-02-25
Is it a network printer?

---

### Post by roof_top_eagle on 2011-02-25
> **alenis said:**
> Brother has a Liunx driver for your printer, did you try it? I have a Brother printer too, although a different model. It works well enough with the Brother driver but works much better with the HP PCL driver.

Thanks!  I got it working.

Funny how after a long time of searching with google I was unable to find it under all the ads on the search but I found it on the first try with startpage.com!

---

### Post by walt.smith1960 on 2011-02-25
I've had quite good luck with Brother & Linux though it's not as easy as HP.  First, have you looked here?  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html).  Be sure to read the pre-required procedures.  Those are kind of confusing because they combine .rpm & .deb instructions in one document. I printed this out then crossed out the parts that don't apply to Ubuntu.  If you're using 64 bit Ubuntu, you'll need to use the command line install--the .deb packages are for 32 bit and you have to use the --force-all switch to install on 64 bit systems.  I tried to install using the gdebi installer which works great in 32 bit distros.  I got a message to the effect that the package was the wrong one.  The package was correct, it just needed the force-all switch.

When working in the command line remember that capital letters are not the same as lower case letter in Linux.  That fact caused me much grief 'til I figured out why there was "no such directory." For example 'desktop' and 'Desktop' are not the same in Linux--they would be in Windows or DOS.  Openprinting.org has a user report that this printer works perfectly but there's no foomatic software for it yet.  Good luck, you should be able to get your machine to work well.  I have an MFC-7820N using wired networking and MFC-6490CW using wireless networking. Both work as advertised for printing & scanning.  I have no need to use the fax function so I can't address that.

---

