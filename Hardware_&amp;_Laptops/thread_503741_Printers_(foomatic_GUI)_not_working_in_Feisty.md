---
title: "Printers (foomatic GUI) not working in Feisty"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by wickstopher on 2007-07-18
Hey, there.  I have an HP Deksjet 3845 printer that I had configured in Edgy using the "Printers" (foomatic GUI) application.  I had tried using the CUPS manager with no success (see [thread]("http://ubuntuforums.org/showthread.php?t=345952")).  In any case, I had my printer working great in Edgy with this application, but since reinstalling with Feisty, I haven't been able to get the application to work (and still no success with the CUPS system).  I installed "Printers" via Add/Remove, and the application simply won't start.  I get prompted for my administrative password, and I get the little tab that says "Starting Administrative Application", and then nothing.  Any advice here?  It's very frustrating having to boot into XP any time I need to print!  Thanks!

---

### Post by pbcartwright on 2007-07-18
do you have the hplip HP printer driver installed???
check the HP web site for Linux drivers, specifically hplip and hplij.
works great. I have the 5610 all in one.

---

### Post by wickstopher on 2007-07-19
I'm still getting the same results here (after installing hplips with the auto-installer), i.e. when I try to print the paper feeds through the printer but nothing is printed.  the printer, as configured with this tool, is still saying that the driver is hpijs, and does not allow me to select hplips as the driver.  perhaps this is the problem?  i'm kind of at a loss here.  thanks!

---

### Post by wickstopher on 2007-07-24
After no response and more fooling around with hplip, I still have had no luck printing in Feisty (so I suppose this is a bump of sorts).  Does anybody out there know why the foomatic Printers tool  won't run (it ran fine in Edgy)?  Any help would be greatly appreciated.

---

### Post by wickstopher on 2007-07-24
This is interesting, and may shed some light onto the situation (although I'm not sure what to make of it).  I just enabled the ubuntu-studio repository and have been installing the packages, and after every installation has finished downloading and installing, I get this error message regarding hplip:

```
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

not sure what this means, but i still can't print!  thanks!

---

### Post by wickstopher on 2007-07-25
Update: I am now getting the above error message regarding hplip EVERY time i install a software package.  This seems strange to me.

---

### Post by wickstopher on 2007-07-26
Just for anyone who is looking, I finally broke down and did yet another install with the hplip auto-installer, and for some reason, despite all the error messages I received, and despite the fact that I've tried the same thing 3 times before, this time it works.  All of my problems have been solved.  I'm not sure how, because I went through the exact same process, but it worked.

---

