---
title: "Frustrations trying to install WINE"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Martin7486 on 2009-10-17
I'm pretty new to Ubuntu and found out for me to run Steam or ITunes that I should install WINE. In my attempts to do so, when I run my Synaptics Packet Manager or Software Sources, I get the following errors...

E: Type 'IT' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

What do I do? Any detailed explanations would be greatly appreciated.

---

### Post by ajgreeny on 2009-10-17
It seems that your /etc/apt/sources.list file is not as it should be so in a terminal type ```
gksudo gedit /etc/apt/sources.list
```find line 42 and look for the "IT" that the error message mentions, and delete it.

If you are not too sure about this, show the output of ```
cat /etc/apt/sources.list
```here and we can tell you in more detail what appears to be wrong.

---

### Post by Martin7486 on 2009-10-17
This is the area where the problem is I think, but where is the delete option?

IT Web Tips
Highub &#8211; IT Web Tips

    * Home
    * About
    * Portfolio

« Validate URL Using PHP Regex
Install Flash CS on Ubuntu »
Install and Configure Wine on Ubuntu

Thanks to Wine, an open source Windows compatibility layer, Adobe&#8217;s Photoshop, Dreamweaver, and Flash all can be installed o$

Wine is not an emulator (hence the name, in true GNU recursive style), but it does provide an alternative, 100-percent-non-M$

Install Wine

The Wine software included with Ubuntu is frequently at least a step behind the current version, so to run the latest versio$

To add the line yourself, open Terminal and enter this command:

sudo nano /etc/apt/sources.list


After you furnish your password, the nano editor will open sources.list. Enter this line at the end of the file:

---

