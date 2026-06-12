---
title: "[SOLVED] OpenOffice.org disappeared"
date: 2008-11-30
forum: General Help
---

### Post by brandoncolorado on 2008-11-30
Hello,

I installed OpenOffice.org 3.0 from a ppa.  I have been using it for about 3 weeks without any problems.  After a restart today, OpenOffice.org word processor and spreadsheet seem to be missing!  i can't start them from the menu, all file type associations are gone, and i can't start them from Alt+F2.  The PPA repositories are still listed in the sources.list file.  I tried to add openoffice in the add/remove dialog, and it said it conflicted with something else on my computer.  I went to synaptic, and nothing with openoffice in the name is installed.  I am confused.

1)  Why would this happen?
2)  How can I repair this problem without messing up my computer?
3)  Thanks!

---

### Post by TeXtonyx on 2008-11-30
> **brandoncolorado said:**
> Hello,

I installed OpenOffice.org 3.0 from a ppa.  I have been using it for about 3 weeks without any problems.  After a restart today, OpenOffice.org word processor and spreadsheet seem to be missing!  i can't start them from the menu, all file type associations are gone, and i can't start them from Alt+F2.  The PPA repositories are still listed in the sources.list file.  I tried to add openoffice in the add/remove dialog, and it said it conflicted with something else on my computer.  I went to synaptic, and nothing with openoffice in the name is installed.  I am confused.

1)  Why would this happen?
2)  How can I repair this problem without messing up my computer?
3)  Thanks!

-----------------------------------------

This method worked for me and a few others. I would backup any
important docs first as a precaution. Is the conflict with
openoffice.org-core ? This method removes OpenOffice and reinstalls.

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*
steps ...

With that done you should have just one thing left to do: Install the
desktop integration package. That should be in the DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I've read that sudo dpkg -i -R may be a better syntax.

Her is another website that makes a similar recommendation,

-------------------------------

[http://www.rebelzero.com/ubuntu/inst...hardy-heron/27](http://www.rebelzero.com/ubuntu/inst...hardy-heron/27)

[http://www.rebelzero.com/ubuntu/](http://www.rebelzero.com/ubuntu/) [copy and paste into one line]
installing-ooo-300-onto-hardy-heron/27

"If you already have OpenOffice.org 2.4.1 installed through Ubuntu’s
repos, you will need to remove it. One of the 3.0.0 packages (debian
menus) has a conflict with one of the 2.4.1 packages,
openoffice.org-core. Removing openoffice.org-core will also remove OO.o
2.4.1 from your computer. Remove OO.o 2.4.1 by using apt-get at the
command line:

sudo apt-get remove openoffice.org-core

You’ll see apt-get prompt you for removing the other 2.4.1 packages as well.
Just hit enter and apt-get will do the rest. Proceed to Step 3b.

-------------------------------------------------

---

### Post by brandoncolorado on 2008-11-30
Thanks!  :mrgreen:

---

