---
title: "How can I revert system updates?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by mbaggia on 2009-10-21
Hello,

Update manager flagged up a couple of things yesterday, so I trustingly went ahead and OK'd the updates. Since then, my fonts are all messed up - in Firefox, OpenOffice spreadsheet, as well as OpenOffice document.

How can I:

A) find out exactly what yesterday's updates were, and 
B) roll back to the previous state?

I have looked in Update Manager (no option to revert), and Control Centre (likewise, no way of reverting).

Please help, this is driving me nuts! I have checked against my other machine, and the fonts/sizes are set the same, so it's not that different fonts have been applied, it's that the same fonts appear different.

Thanks,
Masood

---

### Post by Mark Phelps on 2009-10-21
This is one of my pet peeves in Ubuntu -- that instead of adding really useful features (like an equivalent of System Restore), the Ubuntu developers keep throwing in fluff like new eye candy.

Anyway ...

Sorry to report, but there's no built-in way to revert back to a former state in Ubuntu.

To do what you want do to, you would have to do the following:
1) Find out which packages were installed recently
2) Remove those packages
3) Find the older version of each package
4) Download the older version of each package
5) Install the older version of each package

If you open Synaptic Package Manager, you can find 1) by doing File --> History, and selecting the month and date of the recent changes.  In the right panel, you will see a list of all the recent package changes.  You can capture that information and paste it to a text file -- if you want a list in a separate file.

The rest gets a LOT harder because you would have to use the Debian package search site to locate those packages, look through the history to find the most recent version of each, and then manually download each.

The easier way to handle this in the future is to do backups of your system prior to any major package update and, if the update goes bad, restore from backup -- essentially, implementing System Restore in a manual fashion.

---

### Post by mbaggia on 2009-10-21
Thank you, Mark, Will follow your instructions and see what adventures I have! :)

Will be sure to make a backup first, though!

---

