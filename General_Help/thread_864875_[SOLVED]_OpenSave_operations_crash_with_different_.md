---
title: "[SOLVED] Open/Save operations crash with different apps"
date: 2008-07-20
forum: General Help
---

### Post by zozio32 on 2008-07-20
Hi,

I have some problems with 8.04. since a few weeks (2-3), I have open/save problems with some applications: when trying to open or save a file from the application (File -> Open or Save), the application just close...
I have identified a couple of application suffering from that: OpenOffice.org, Gimp, Inkscape, revelation (Password manager), and probably other but I still son't know.
some application are fine: firefox, Xara Xtreme, QtOctave.

I've amanged to solve the problem for Gimp and OOo by doing a *Complete removal* with the package manager and reinstalling :), but the same method applied to Inkscape and Revelation didn't work :(.

any idea?

---

### Post by JagDragon on 2008-07-20
Hmm.

This may be a bit brutal, but a full reinstall of Ubuntu may fix it.

---

### Post by pooyaplus on 2008-07-20
Hi,
you can open the applications in a terminal and keeping the terminal open and observe the behaviour of the application. And in case of any errors or crashes you can post it here to get help from the folks.

Go to Applications > Accessories > Terminal and just type in the application e.g. gimp.

Good luck.

---

### Post by zozio32 on 2008-07-20
ok,
that's what I got from Inkscape, just opening the application and doing File -> Open.
```
Emergency save activated!
Emergency save completed. inkscape will close now.
if you can reproduce this crash, please file a bug at www.inkscape.org with a detailed description of the steps leading to the crash, so we can fix it.
Segmentation fault
```

what I got from revelation, with the same operation (File -> Open):
```
Segmentation fault
```

Gimp is ok, it didn't print anything in the terminal while running, but as I said before, it seems to behave well since I completely removed it and re-install it.

OpenOffice gave me this, just starting the application:
```
javaldx failed!
```
It looked funny at the start, with nearly nothing in the window, but then worked correctly for opening files. It also seems to work better since a complete removal and re-installation.

If I remembre well, those problems started after I've messed around with the java trying to keep only the sun-java6 and deleting OpenJDK, but I re-install it since...

---

### Post by pooyaplus on 2008-07-20
Well, that's another story. Have you searched those error messages in their own forums or google? If you could not manage to find some hints in their bug polls or anywhere else in the Internet, you may need to reinstall those apps again with that openjdk package installed. 
Let me know if you find something new.

---

### Post by zozio32 on 2008-07-20
I'll try that, but as it was the same error for different applications, I thought it was a Ubuntu related program.
And well, i have OpenJDK installed now, and the solution *complete removal* and *re-install* doesn't work for Inkscape and Revelation. They were both working fine before.

Do you know what's ```
javaldx failed
``` mean?

I'll post whatever I find about this.
Thanks for the hepl

---

### Post by pooyaplus on 2008-07-21
Hi, would you please check the dependencies of the open jdk package in the synaptic. That may help. Anyway, I have found some similar posts in the launchpad bugs here: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139") and in ubuntuforums archive here: [http://ubuntuforums.org/archive/index.php/t-585968.html]("http://ubuntuforums.org/archive/index.php/t-585968.html")

As I said and as these threads say try removing the packages completely (complete removal) and do a fresh install. Hope this solves your problem.

---

### Post by zozio32 on 2008-07-21
openjdk-6-jre dependencies:
*Depends:*
libasound2 (>1.0.14)
libc6 (>=2.3)
libgif4 (>=4.1.6)
libjpeg62
libpng12-0 (>1.2.13-4)
libx11-6
lbxext6
libxtsx6
open-6-jre-headless (=6bO9-Oubuntu2)
zliblg (>=1:1.2.3.3.dfsg-1)

*PreDepends* dpkg (>=1.14.12ubuntu3)

*Suggests* icedtea-gcjwebplugin

*Recommends* lesstif2

Dependent Packages:
*Dependency of*
openoffice.org-writer (or dependency)
openoffice.org-officebean (or dependency)
openoffice.org-base (or dependency)
openoffice.org (or dependency)
sun-javadb-demo (or dependency)
sun-javadb-core (or dependency)
sun-javadb-client (or dependency)
jabref
freemind (or dependency)
solr-common
project-x (or dependency)
openjdk-6-source
openjdk-6-jdk
openjdk-6-demo
lib-woodstox-java (or dependency)
libswingworker-java
libqtjambi-java
libnb-svnclientadapter-java
libnb-platform7-java (or dependency)
libnb-platform7-devel-java (or dependency)
libnb-javaparser-java
liblucene2-java (or dependency)
libini4j-java
libhiglayout-java (or dependency)
libbeansbiding-java
libappframework-java
libaccess-bridge-java (or dependency)
jedit (or dependency)
imqv2 (or dependency)
icedtea-java7-jre
icedtea-gcjwebplugin
freecol (or dependency)
azureus (or dependency)
openoffice.org-writer (or dependency)
openoffice.org-officebean (or dependency)
openoffice.org-base (or dependency)
openoffice.org (or dependency)

I think I got them all. I had to type them all from the dialog box open by the package manager. do you kno a way to do a copy->paste from there?

DO you also need the dependencies of: openjdk-6-jre-headless and openjdk-6-jre-lib?

---

### Post by zozio32 on 2008-07-21
I've tried again to remove completely Inkscape, and put it back, but still the same problem.
I don't know if its related to inkscape or not, as it was working some time ago without any problem on hardy...

---

### Post by pooyaplus on 2008-07-21
Interesting, as you can see the openjdk-6-jre has multiple dependencies with the open office suite. That justifies the problem with the open office. But regarding the inkscape just check out its own dependencies and see if there had been a package that you might be removed accidentally.

But a complete removal of the packages and a fresh install must do the trick for both openoffice and inkscape. Wondering if you have enough bandwidth to get them again or not. 

Did you go through the launchpad bud poll? Found anything?

---

### Post by zozio32 on 2008-07-30
new problem with OOo.
after a full re-install of OOo, I thought it was sorted as I now can open a file from the application itself. BUT..., if I do insert -> picture -> from file, I get the same type of crash than before.

:( I am definitely lost with that.
I don't get an error report in the terminal if I lunch it from the terminal.

and btw, I've reported the "revelation" and "Inkscape" problem, but I haven't got any answer yet.

suggestion: formating Ubuntu and full reinstall? what kind of config file should I save if this is the case?

---

### Post by pooyaplus on 2008-08-02
> **zozio32 said:**
> 
I've reported the "revelation" and "Inkscape" problem, but I haven't got any answer yet.

suggestion: formating Ubuntu and full reinstall? what kind of config file should I save if this is the case?

Hi, at least it's a step forward. :) You may need to report the OOo bug too. I do not believe that a fresh install of the OS would be required, since issues like yours have been around for some time, and there are workarounds. 

In such situations as yours, the only reference would be the bug polls of the apps and the launchpad. 

Hope you find the fix asap and let us know of the fixes.

Suggestion: If you need the OOo for the time being and the error are making trouble, just download the portable version from the [http://portableapps.com/](http://portableapps.com/) and have your works done till you find the fix.

Good luck.

---

### Post by zozio32 on 2008-08-02
well,

I've gone trough a full re-install 2 days ago.
everythings seems fine now for OOo, Inkscape, Gimp, revelation, etc...

---

### Post by pooyaplus on 2008-08-03
Well, it seems your problem has been solved, so tag the thread as such please. 

Good luck.:popcorn:

---

