---
title: "Problem installing other software after botched Ubuntu-studio install"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by AllTheGoodNamesAreGone on 2009-05-15
Hey all, I have Ubuntu Jaunty 9.04 installed and I was looking to try the Ubuntu-studio and when trying to install that, I got cold feet during the install and abandoned it.  Afterwards, when trying to install a couple of other programs, I get an error that shows the following:

"Please insert the disk labeled: Ubuntu-studio 9.04_jaunty jackalope_-Release i386 (20090421.4) in drive /cdrom/"


I had the iso disk for Ubuntu studio in the drive during this time.  I attempted to repair the issue with the uninstalled dependencies (kommander?) using Synaptic, but I still have the issue of the aforementioned error.  How can I tell Ubuntu to stop with this particular error and allow me to install applications again?  I can install small applications, but something like "Inkscape" fails due to seeking for the Ubuntu studio disk.


Im pretty new to Ubuntu so Im not real familiar with installing and uninstalling programs and even less on how to undo mistakes.  Any help would be appreciated!


Thank you in advance.


Steve

---

### Post by tagabukid on 2009-05-15
You have to disable the cd-rom as a software source.

System> Administration> Software Sources

On the "Third Party Software tab" uncheck cdrom:[Ubuntu-studio 9.04_jaunty jackalope_-Release i386 20090421.4]

that should be it..

---

### Post by AllTheGoodNamesAreGone on 2009-05-15
> **tagabukid said:**
> You have to disable the cd-rom as a software source.

System> Administration> Software Sources

On the "Third Party Software tab" uncheck cdrom:[Ubuntu-studio 9.04_jaunty jackalope_-Release i386 20090421.4]

that should be it..

Thanks for the quick reply.  When I check the System>Administration>Software Sources and checking the Third Party Software tab, I dont see the above source.  I do see two of them under the Ubuntu Software tab.

Under the Third Party Software tab, it was caconical jaunty?  I went ahead and deleted those but this has not resolved the problem.  I do not see a way to delete the cdrom selection of Ubuntu.

I know this is probably easy to fix but Im too new to Ubuntu.  I hate learning curves! :D

---

### Post by AllTheGoodNamesAreGone on 2009-05-16
FIXED.

Using the search term "disable cd rom as software source Ubuntu", I found the solution.  It was recommended to perform the following:

sudo nano /etc/apt/sources.list 

and then comment out the cd source.

This worked fine and I can now install my applications.  Thank you again for your help.

Steve

---

### Post by tagabukid on 2009-05-16
I'm glad you solved your problem. Congrats!

):P

---

