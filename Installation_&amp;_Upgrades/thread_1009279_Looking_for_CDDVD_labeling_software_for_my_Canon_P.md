---
title: "Looking for CD/DVD labeling software for my Canon Pixma Printer"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2008-12-12
Hello :-)

I am trying to move completely away from windows.  Right now there are very few things that keep me from doing that.

One of the things is that I can't print on CD/DVD.  On my windows system I have a program that came with my printer a Canon Pixma-ip5000 called CD label print.

I tried to install it on my linux machine through wine, but I got an error that the spooler isn't started...

Anyway, I am not in love with the specific program, I just want a way to be able to print on CD/DVD's.

I tried to search with "cd label" on add-remove programs but nothing came out.

Is there anyone who had the same problem, and solved it?
Please share..

Thank you all in advance :-)

---

### Post by Ifaistos on 2008-12-13
bump :)

---

### Post by Ifaistos on 2008-12-15
bump

---

### Post by ibutho on 2008-12-15
You can use glabel, kover or use openoffice.org templates to create cd/dvd labels and print them.

---

### Post by Ifaistos on 2008-12-15
I can create them but I can't print them...
My printer prints directly on the CD/DVD

btw I couldn't find in add/remove programs these programs you mentioned...
glabel and kover I mean... I use gnome..

Thanks for the suggestion though.

---

### Post by ibutho on 2008-12-15
The program is called glables and not glabel. I made a typo in my first post. Kover has been around for a while, but its a qt/kde application. I don't have much knowledge about printing directly to discs using Linux, so sorry I can't help you there.

---

### Post by Ifaistos on 2008-12-18
np at all.
Thank you for your time and help :-)

bump

---

### Post by Mark Phelps on 2008-12-19
I print directly to an Epson CD/DVD printer, so I don't know if this will work with your Canon -- but it's worth a shot.

Install gimp-gutenprint. This will allow you to print directly to the CD/DVD media.

Use GIMP to open the graphic you want to print.

Select Print using Gutenprint from the menu (not Print).

That will open a screen with lots of options.  Somewhere in there (sorry, don't have it installed on this box), you'll see an option that allows selecting "print to CD".  You will also have options for selecting the CD size.

You can also set resolution and print quality.

At the bottom, click the save Settings and Print button.  That will open another window that will require you to Export the image. Allow it to do that.  You will see the progress bar at the bottom of the panel move to the right. Shortly thereafter, your printer should start.

If it doesn't, you might have to install the Gutenprint printer drivers.

To do that, you will need to install cups-driver-gutenprint, and then reconfigure your printer through CUPS, using localhost:631 in your browser, to open the printer, and reinstall it selecting a Gutenprint driver from the list of drivers for your printer.

---

### Post by Ifaistos on 2009-01-06
Thank you for your answer... I will definitely try it and let everyone know if it worked...

---

