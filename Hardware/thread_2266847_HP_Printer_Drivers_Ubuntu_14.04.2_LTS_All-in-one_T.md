---
title: "HP Printer Drivers Ubuntu 14.04.2 LTS: All-in-one Terminal Command"
date: 2015-02-25
forum: Hardware
---

### Post by MikeMecanic on 2015-02-25
**February 2015 Ubuntu 14.04.2 LTS.  For immediate release,**
Thanks God we now have a Doctor n the Ubuntu terminal. Here's how to install the drivers of any HP printer on Ubuntu 14.04.2 LTS.  Ubuntune automatically to HP via the terminal in a one line command only.
Need an active Internet connection and must be patient (takes a few minutes).  Follow the steps in the terminal by answering YES and ALL.  Please reply to this thread if it work for your printer by giving your printer model. It's **[SOLVED]** for the HP Laser Jet 1020 printer and should work for the most popular models. Waiting to ear from you...
[B]
Install printer driver:[/B]

**Connect your printer to your PC, and make sure to switch it on. Open the terminal and copy/paste the following command line :**   hp-doctor

Follow the process carefully and be happy!  

Make a print test page: Printer Test Page UBUNTU will be print with Job ID and drivers version: F002ZJS-.PPD / 1.1 ( for 1020 Laser Jet)
Should work for any HP printer and everyone using the latest version of Ubuntu.
All the best,

---

### Post by RumorsOfWar on 2015-02-26
HP p 1102w laserjet failed.  (Xubuntu 14.04) 
USB connected
"Test print" sends job without error.
Printer queue says "Pending"
Printer State says "Processing - Rendering completed"
..but nothing prints.
hp-doctor reads:
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                           
  --------------------------------  --------------------------------
  hp:/usb/HP_LaserJet_Professional  HP LaserJet Professional P 1102w
  _P_1102w?serial=000000000W44D5VA                                  
  PR1a                                                              

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Home
----
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_P_1102w?serial=000000000W44D5VAPR1a
PPD: /etc/cups/ppd/Home.ppd
PPD Description: HP LaserJet Professional P 1102w, hpcups 3.14.3, requires proprietary plugin
Printer status: printer Home now printing Home-0.  enabled since Thu 26 Feb 2015 07:59:3Rendering completed
Required plug-in status: Installed
Communication status: Good


--------------
| PERMISSION |
--------------

USB             Home                           Required        -        -        OK       Node:'/dev/bus/usb/002/005' Perm:'  root  lp rw- rw- rw- rw- r--'
 

Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.


Checking for HP Properitery Plugin's....
Plugin's already installed
 
Diagnose completed...

:END:

But nothing prints. Any ideas?

---

### Post by MikeMecanic on 2015-02-27
**I've notice that if you pass by file/print it works.  If you print directly in the text file icon on top it won't.**  Did you try to removed the pending file?  Did you try to print a regular text file.  Did you delete the old printer file in the process?  It should work! There.s many errors that appear when you start (in red) but go forward.  You must reach HP download center to complete.

---

### Post by tgalati4 on 2015-02-27
*hp-doctor* is a nice utility!  Word of advice:  Perform your updates first because some of the checks will flag dependencies that are out-of-date.

```
sudo apt-get update
sudo apt-get upgrade
```

Reboot if kernel or xorg-related updates are installed.  Set aside time to fix regressions because updates to the kernel and xorg (graphics) can cause issues on some machines.

Some printer problems can be traced to kernel and CUPS versions--they need to be syncronized--make sure you check for CUPS updates after performing any kernel updates.  Sometimes printer queues need to be deleted--just delete the printer--and reinstall the printer to fix this condition--not unlike how a bad printer can be fixed in Windows by deleting and reinstalling.

---

### Post by KPDXHAM on 2015-03-29
Thank You!!!! :)
I just installed Ubuntu 14.04.1 "MATE" on a refurbished HP Z400 Workstation that already had Windows 7 Pro on it. (I'm Dual Booting). The HP OfficeJet Pro 8610 (All-in-one Scanner-Fax-Printer) would only print, but I wanted it to work like it's supposed to. Like it does in Windows 7 where I could scan to my computer. I'm very grateful that you posted this info and I was able to get it working properly by following the HP online installation via the linux terminal. Now it does all that I need it to do. :)

---

