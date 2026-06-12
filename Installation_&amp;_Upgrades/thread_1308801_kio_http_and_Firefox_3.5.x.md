---
title: "kio_http and Firefox 3.5.x"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2009-10-31
In the prior version of Ubuntu (Jaunty) when using Firefox 3.5+ there was a serious issue with how it leaked memory.  What happened was that as you right clicked on a photo and chose to save it to file there would be a program that Firefox launched that would remain open and never close.  The next time you did this same task another program would be opened.  In jaunty that program was called "python".  It would take around 3 mb of RAM for each save.  If you did this enough times your system would become unstable (keeping you from launching another program) until you rebooted or terminated those programs using the system monitor.

In Karmic we have the same issue, except the name of the program has changed.  In this latest release the name of the program is called kio_http.  For each file you right click and choose save (such as saving an image), you will get one of these programs launched (you can see the entry in system monitor).

These add up and create a very unstable environment for anyone using their system for any length of time.

My prior install was an upgrade to Jaunty from the prior release.  When KDE 4.2 was released I installed kubuntu-desktop, and later upgraded to the latest release.  My current system however is a clean install of Ubuntu and then with no additional repositories I did a "sudo apt-get install kubuntu-desktop".  I became curious as to the amount of free ram I had and checked system monitor and noticed this same behavior.

This seems like a very serious error and it should have been identified and corrected before (back just a couple months after jaunty was released when it was reported.)

---

