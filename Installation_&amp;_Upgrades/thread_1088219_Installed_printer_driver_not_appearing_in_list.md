---
title: "Installed printer driver not appearing in list"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by fabricator4 on 2009-03-05
Hi all, I'm running Ubuntu (Intrepid) on a Celeron 1GHz box (with a minute amount of RAM).  I managed to get Ubuntu to give me the right resolutions for my screen through a KVM, but I'm still in the slow process of learning.  My main objective is to get everything going perfectly so that I can happily push the Celeron out the window, and install Ubuntu on my main box (currently XP), but since I'm a photographer there are a few things that really _must_ be working before I can do that.

One of these things is printing, but I found that my Canon iP3300 is not supported natively. The printer is plugged into the XP machine, and I can get to it and print under limited support through Samba (eg using a "similar" driver)

I downloaded the drivers from Canon Australia:
cnijfilter-common-2.70-1.i386.rpm
and
cnifilter-ip3300-2.70-2.i386.rpm

These drivers I put in a sub-directory in my home folder
I then ran alien to convert them:

sudo alien cnijfilter-common-2.70-1.i386.rpm
and
sudo alien -c cnijfilter-ip3300-2.70-2.i386.rpm

This made the .deb packages in the same directory:
I then rand dpkg to install them:

sudo dpkg -i cnijfilter-common-2.70-1.i386.deb
sudo dpkg -i cnijfilter-ip3300-2.70-2.i386.deb

The problem is that the printer driver still does not show up when I try to install the printer.  My understanding is that it should do.

Obviously I'm doing something wrong, but I can't for the life of me figure out what that is...

Chris

---

### Post by Partyboi2 on 2009-03-05
Did you complete the steps after installing the deb packages?
[http://www.pwnedwiki.nl/wordpress/?p=3](http://www.pwnedwiki.nl/wordpress/?p=3)

---

### Post by fabricator4 on 2009-03-06
> **Partyboi2 said:**
> Did you complete the steps after installing the deb packages?
[http://www.pwnedwiki.nl/wordpress/?p=3](http://www.pwnedwiki.nl/wordpress/?p=3)

Now that's not intuitive!  :-)   Thanks, I now have the printer driver showing up in the list and installed it.

The big dissapointment is that it's only 600x600 resolution, far short of the 4800x1200 that I need.  :-(

Also: the driver prints a ghost output - I can see the print job in the cups spooler, I can see it appear on the Windows print spooler for the correct printer, I can see it disappear into the printer memory which then proceeds to...  do absolutely nothing.

Back to the drawing board I guess, but thanks for your help.

Chris.

---

