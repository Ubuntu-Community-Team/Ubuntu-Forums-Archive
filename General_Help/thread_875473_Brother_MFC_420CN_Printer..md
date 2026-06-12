---
title: "Brother MFC 420CN Printer."
date: 2008-07-30
forum: General Help
---

### Post by joewest on 2008-07-30
I downloaded the CUPS program directly from Brothers Site.  I installed it, and it seemed that everything worked fine.  Then when I tried to print from OfficeOrg, or from AbiWord, or any other form of printing, I get a box that comes up, shows the Brother MFC 420CN as the default printer, Shows the type as CUPS:MFC-420CN. When I press print, I get a small box in the middle of the screen telling me "OpenOffice.org 2."
                          "Error while printing"
                               "OK"

I tried printing from several programs, as well as from the command line, but I get the same  error msg.  What am I doint wrong?  

I have Hardy Heron installed in 114 GiB partition, with 2 GiB RAM, 8 GiB of Swap space, and the rest is home.  Gateway CPU, GT5228.  I'm lost.  Can anyone help me?  I really want to get away from Windows, but some of this is still cryptic to me.  

Joe

---

### Post by Shazaam on 2008-07-30
Enter this in a browser (Firefox, Opera, etc)....
```
http://127.0.0.1:631
```
This will get you to the cups interface. Try poking around in there.
BTW, I have a 420cn too. Ink hog unfortunately but it's a good printer/scanner.

---

### Post by plucky on 2008-07-31
> **joewest said:**
> I downloaded the CUPS program directly from Brothers Site.  I installed it, and it seemed that everything worked fine.  Then when I tried to print from OfficeOrg, or from AbiWord, or any other form of printing, I get a box that comes up, shows the Brother MFC 420CN as the default printer, Shows the type as CUPS:MFC-420CN. When I press print, I get a small box in the middle of the screen telling me "OpenOffice.org 2."
                          "Error while printing"
                               "OK"

I tried printing from several programs, as well as from the command line, but I get the same  error msg.  What am I doint wrong?  

I have Hardy Heron installed in 114 GiB partition, with 2 GiB RAM, 8 GiB of Swap space, and the rest is home.  Gateway CPU, GT5228.  I'm lost.  Can anyone help me?  I really want to get away from Windows, but some of this is still cryptic to me.  

Joe

The Brother printer drivers are now packaged in Synaptic,so you only have to open **Synaptic** and search for your printer and select the the two drivers to install.

In your case they are **brother-cups-wrapper-extra** and **brother-lpr-drivers-extra**.It might be a good idea to un-install the current driver you installed before doing this.

If your printer has a scanner as well,then you still have to download the relevant file from the Brother website and follow the installation instructions on the website.

Good Luck

---

### Post by joewest on 2008-08-03
OK, I downloaded so many drivers at this point that my head is spinning.  I got the drivers from brothers, and they installed fine, but nothing works yet.  So I downloaded the brother-cups-wrapper-extra and the brother-lpr-drivers-extra, and installed both of them.  Still no printing on the MFC 420CN.  When I boot from the XP side, everything works fine. 

At this point, I am scratching my head, because if I really want to print something, I have to leave linux, reboot into Windows XP, and do it from that side.  

Is there a decent book out there that will bring me up to speed on all this?  I have a DBA's Guide to Databases on LINUX, which is not much help at this point, and I have LINUX for dummies.  I must be a super dummy, cause I can't get anything working.  Games are fun tho!!!  

The two things I need in a big way are databases that will replace Windows Access, and printing capabilities.  I have not been successful at either at this point.   I do seriously want to thank plucky and Shazaam, both of whom tried to help me.  I guess I was just too dumb, cause I did what was suggested, and still no deal.  ????  I still have almost the entire 114 GiB dedicated to Ubuntu, separated of course into root, swap and home.  Since I can't get anything to work, I'd better hold on to XP for a while longer.  I'd like to get rid of it, PERIOD...   

Thanks guys!  I do appreciate it.    Joe

---

### Post by joewest on 2008-08-04
Thanks Shazaam!  The Site you sent me to was good, and I was finally able to figure it all out.  It works now.  I guess Patience "IS" a virtue when it comes to re-learning.  I hope others will follow the same advice if they have the same problem.  It does work.  Thanks again.  Joe

---

