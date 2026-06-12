---
title: "Canon MX870 scanner drivers on i386"
date: 2014-07-29
forum: Hardware
---

### Post by Fred T on 2014-07-29
Starting a new thread, the previous has me completely confused.

My system is dual boot, Win 7 64 bit & Ubuntu 14.04 with an i386 processor.. On advice from another part of this forum I loaded 64 bit Ubuntu, was supposed to make the dual boot easier to load.

Trying to set up the printer/scanner to run from both sides. I have the printer working, but am at a loss on the scanner. I have downloaded the [COLOR=SeaGreen]scangearmp-mx870series-1.50-1-i386-deb.tar.gz[/COLOR], but haven't installed it. An install script was mentioned, but I need help running that.

---

### Post by Fred T on 2014-07-30
[COLOR=#000000]Okay. My old adage of if you stumble around in the forest you will eventually run into the right tree finally worked. Don't know if it was the right tree, but it worked.

Download the scanner driver file from the Canon-Singapore sight. Double click on the scangearmp-mx870series-1.50-1-i386-deb.tar.gz file. This opens a new folder with the scangear file. Double-click that file, the folder contains folders for packages, resources and a install shell script. I don't know how to run the script, so I opened the resources folder, which contains the common and mx870 files. Going by what I read elsewhere, install the common first, by double clicking. Then install the scan specific file. This should install the drivers.

Now to the software. No Canon software for Unix architecture, use what the system has available. To open this, follow these instructions: 
 [/COLOR][QUOTE=thewump][COLOR=#000000]Now.. You've just installed drivers AND a scanner app.  To use the  scanner app you have to run it.  Hit ALT-F2 to pull up the run command  and type "scangearmp".  You should see a dialog box about scanners  (first time it might say "NOT FOUND" but if you follow your nose, it  will find the scanner and add it to the available list.  To make life  easier, make a launcher on your desktop for scangearmp for future use.
[/COLOR][/QUOTE][COLOR=#000000]

I can now scan in Ubuntu, but don't have the controls like Windows.
[/COLOR]

---

### Post by pdc on 2014-07-30
Hi Fred; my apologies for not being online to spot your new thread: well done; you did very well to get it all downloaded and installed; tell the family how well you did!!

so for a 32bit (386) system, the Canon driver should install easily and work well; 

___________________

if you set up a launcher, it makes launching [COLOR="#0000FF"]ScanGearMP[/COLOR] more easy for most


I wasn't clear if you had the Canon printer driver installed; if you don't; happy to supply the commands to make the install quicker for you;

don't know if either of these are good for you [http://www.youtube.com/watch?v=GSU9YuE_36w](http://www.youtube.com/watch?v=GSU9YuE_36w) and [https://apps.ubuntu.com/cat/applications/manage-launcher/](https://apps.ubuntu.com/cat/applications/manage-launcher/)

________

I will subscribe to the thread to better keep in touch

---

### Post by Fred T on 2014-07-30
I had the printer drivers installed, which was the cause of the error discussed in the older thread. Your comments there were helpful in finding the solution. Thanks

---

