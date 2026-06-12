---
title: "Scratching head on Wubi Install..."
date: 2008-08-06
forum: General Help
---

### Post by NJ0E on 2008-08-06
Hello all,

System
Dell Inspiron 5150 with 30 G HD, 512 Ram Intel P4, Windows XP.
Used Wubi 8.04.1 for this install try

(I do have a Live CD of ubuntu 8.04, but havent used it yet)

HD partitioned 3 x 
C) Windows area
D) Other data area(safe sotrage area)
F) Empty space for Ubuntu

Downloaded Wubi and installed same.  When I was asked in the GUI what drive selected F.  After reboot came to selection windows or Ubunt.  Selected Ubuntu. Now to install of ubuntu -- step 2 select time checked Chicago.  Next info 
Partman failed.  retry or ignore -- selected retry computer froze for 10 hrs (let it go to see what the HD was doing)

turned computer off restarted windows to shut down correctly.  Retried install -- this time I selected continue in Partmanfail, went to step 4 Theis on e also failed.  

Both failures advised to check the var/log/syslog file -- kinda hard to do that without ubuntu loaded.  uninstalled entire mess.

Questions:

1) What went wrong?
2) What do I need to do to get this going?

Thanks,

---

### Post by thawkins1 on 2008-08-08
> **NJ0E said:**
> Hello all,

System
Dell Inspiron 5150 with 30 G HD, 512 Ram Intel P4, Windows XP.
Used Wubi 8.04.1 for this install try

(I do have a Live CD of ubuntu 8.04, but havent used it yet)

HD partitioned 3 x 
C) Windows area
D) Other data area(safe sotrage area)
F) Empty space for Ubuntu

Downloaded Wubi and installed same.  When I was asked in the GUI what drive selected F.  After reboot came to selection windows or Ubunt.  Selected Ubuntu. Now to install of ubuntu -- step 2 select time checked Chicago.  Next info 
Partman failed.  retry or ignore -- selected retry computer froze for 10 hrs (let it go to see what the HD was doing)

turned computer off restarted windows to shut down correctly.  Retried install -- this time I selected continue in Partmanfail, went to step 4 Theis on e also failed.  

Both failures advised to check the var/log/syslog file -- kinda hard to do that without ubuntu loaded.  uninstalled entire mess.

Questions:

1) What went wrong?
2) What do I need to do to get this going?

Thanks,
It's no need to Partition your hd to install ubuntu through Wubi. Just run the installer select how much space you want ubuntu to use and set up your username and password and click continue and ubuntu will install right on your C drive under a folder called Ubuntu. Also it has a uninstall feature so you can install with no worries. Hope I helped.

---

### Post by FXEF on 2008-08-08
First make sure your CD is good. Put the CD in the drive then boot system. Choose check the CD option. If CD checks out OK, boot into Ubuntu with the LiveCD option. When Ubuntu loads from CD you can make sure all hardware will work with Ubuntu.

To install Ubuntu inside Windows using wubi from the CD, you must shutdown the LiveCD session, remove the CD, then reboot into Windows. While Windows is up and running place the CD in the drive. Next choose the option to install inside Windows, follow the prompts and Ubuntu will install inside Windows. Once install is completed, from now own each time you boot the machine, you will have the option to boot Windows or Ubuntu.

---

### Post by ago on 2008-08-11
> **NJ0E said:**
> 
Downloaded Wubi and installed same.  When I was asked in the GUI what drive selected F.  After reboot came to selection windows or Ubunt.  Selected Ubuntu. Now to install of ubuntu -- step 2 select time checked Chicago.  Next info 

There should be no step 2... Something went wrong. Try to reinstall and if it happens again press CTRL+ALT+F4 and see if there is any relevant error.

For a more exhaustive log, press CTRL+ALT+F2 and run:

sudo sh /custom-installation/hooks/failure-command.sh

---

