---
title: "Eclipse can't install Java development plugin/ ADT plugin"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by flair-kun on 2009-11-09
I just installed Eclipse from software center on Ubuntu 9.10 and cannot seem to install the Java Development tools plugin from Galileo - [http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo)

Similarly i couldn't install the C/C++ development plugin or the ADT plugin.

Can Someone tell me how to solve this? Thanks a lot.

The Error i get with Java Development plugin is:

Cannot complete the install because of a conflicting dependency.
  Software being installed: Eclipse Java Development Tools 3.5.1.r351_v20090810-0600-7r88FEoFI0WTo6Az-1qFRHm37ChJ (org.eclipse.jdt.feature.group 3.5.1.r351_v20090810-0600-7r88FEoFI0WTo6Az-1qFRHm37ChJ)
  Software currently installed: Eclipse Platform 3.5.1 (Eclipse Platform 3.5.1)
  Only one of the following can be installed at once: 
    Eclipse Java Development Tools 3.5.1.r351_v20090810-0600 (org.eclipse.jdt 3.5.1.r351_v20090810-0600)
    Eclipse Java Development Tools 3.5.1.v200909170800 (org.eclipse.jdt 3.5.1.v200909170800)
  Cannot satisfy dependency:
    From: Eclipse Platform 3.5.1 (Eclipse Platform 3.5.1)
    To: org.eclipse.jdt [3.5.1.r351_v20090810-0600]
  Cannot satisfy dependency:
    From: Eclipse Java Development Tools 3.5.1.r351_v20090810-0600-7r88FEoFI0WTo6Az-1qFRHm37ChJ (org.eclipse.jdt.feature.group 3.5.1.r351_v20090810-0600-7r88FEoFI0WTo6Az-1qFRHm37ChJ)
    To: org.eclipse.jdt [3.5.1.v200909170800]

---

### Post by flair-kun on 2009-11-10
SOLVED

The Eclipse installed from software center does not come with eclipse-jdt, eclipse-plugin-cvs and eclipse-pde.

I uninstalled and installed from command line using apt-get install eclipse and it worked.

---

### Post by btnelson on 2010-01-11
Thanks flair-kun.  Did the trick.

I had also installed Eclipse from the Ubuntu Software Centre.  I didn't uninstall though and just ran:

sudo apt-get install eclipse-jdt eclipse-plugin-cvs eclipse-pde.

Then installed ADT Plugin again in Eclipse and fixed the issue.

---

