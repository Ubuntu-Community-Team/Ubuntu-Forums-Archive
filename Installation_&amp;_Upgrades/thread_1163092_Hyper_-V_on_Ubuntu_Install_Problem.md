---
title: "Hyper -V on Ubuntu Install Problem"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Bilal Tas on 2009-05-18
Hi,
I have test and trail Ubuntu Ubuntu 9.04 Desktop on Microsoft Hyper-V server.
Test Platform;HP DL 380 G5 on Microsoft Windows 2008 Enterprise Edt SP1 and all fix install. I create one virtual machine on Hyper-V and select disk type IDE and install no problem...if virtual machine disk type select SCSI no found disk... How to achive Hyper-V virtual machine scsi disk install ubuntu ?

---

### Post by matthew.mattoon on 2009-05-26
Hi Bilal,
 
Hyper-V does not support using SCSI as your boot volume on any guest OS.

So you have 2 options:
 
1) Use 2 VHD files one small one for /boot which is connected via virtual IDE interface.  Then use one bigger one for everything else which is connected via virtual scsi interface.
 
2) Install the Linux Integration Components for Hyper-V (which are not supported for Ubuntu - but can work).  When using the LICs the VM has "enlightened" drivers which will allow you to get near SCSI performance on the virtual IDE interface.  Additionally you also get 10Gbps connectivity to the virtual switch (if you use a Network Adapter instead of a Legacy Network Adapter - which gives you 100Mbps).
 
I have a write up on how to implement option 2.
 
[http://blog.allanglesit.net/Blog/tabid/66/EntryId/22/Hyper-V-Guests-Linux-Integration-Components-Ubuntu-and-Debian.aspx](http://blog.allanglesit.net/Blog/tabid/66/EntryId/22/Hyper-V-Guests-Linux-Integration-Components-Ubuntu-and-Debian.aspx)
 
Good Luck

---

### Post by msright1981 on 2009-10-03
Hi Bilal,

Following up on Matthew answer. Yes, Hyper-V does not support booting up any OS from SCSI at the moment. Furthermore, it does not support Ubuntu OS yet. A good reference on how to setup Hyper-V & then install Linux though & the Linux Integration Module can be found at: [MS Windows 2008 Hyper-V Installation & Linux Integration]("http://www.virtualizationteam.com/microsoft/hyper-v/microsoft-windows-2008-hyper-v-rtm-installation-steps.html")

Ah, yes its worth to mention, although Ubuntu is not supported yet it will work :).

---

### Post by matthew.mattoon on 2010-05-29
I have an updated article which allows for more choices when choosing your method of enlightenment.  It also has a much simpler process of installation.

[http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx)

-matt

---

### Post by Victor Miasnikov on 2011-02-24
> **matthew.mattoon said:**
> I have an updated article which allows for more choices when choosing your method of enlightenment. It also has a much simpler process of installation.
 
[http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx)
 
-matt
 
Thanks, but
 
-h-t-t-p://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx 
 
write
==
Comments are closed. 
==
and not show old coments :confused:
 
Matthew.Mattoon block posting comments to old msg of blog ( for «half-technical» reason) 
 
 
[SIZE=3][FONT=Times New Roman][http://ubuntuforums.org/showthread.php?p=10490121#post10490121](http://ubuntuforums.org/showthread.php?p=10490121#post10490121)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]==[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]. . . [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]On Russian language:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx](http://blogs.technet.com/b/abeshkov/archive/2011/01/30/3383495.aspx)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]. . . [/FONT][/COLOR]

[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]Mini How-To about [/FONT][/COLOR][COLOR=black][FONT=Verdana]_practically_ method for worked mouse in Linux guest:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Linux on Hyper-V How-To FIX &#8220;Mouse not captured in Remote Desktop session&#8221;[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/](http://vvm.blog.tut.by/2011/02/22/hyper-v_mouse_in_linux/)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]==[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]. . .[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Without Satori, mouse work in Linux Guest if connect to it from Windows _directly_[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]. . .[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]==[/COLOR][/FONT]
[/FONT][/COLOR]
[SIZE=3][FONT=Times New Roman]==[/FONT][/SIZE]

---

