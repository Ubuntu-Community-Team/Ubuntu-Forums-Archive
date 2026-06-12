---
title: "Openoffice gives error in Terminal"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by PostChache on 2009-08-31
Whenever I open an .odt in the Terminal I get this error 

$ javaldx: Could not find a Java Runtime Environment! 
Please ensure that the package openoffice.org-java-common is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
** (soffice:3589): WARNING **: unable to get gail version number
error - missing word count in dictionary file
Hash Manager Error : 4


It will still open the .odt but should I worry about this error or try to fix it? I've tried removing /.openoffice.org/3/user/config/javasetting_Linux_*.xml

---

### Post by Partyboi2 on 2009-09-01
Have you got the openoffice.org-java-common package installed?
```
sudo apt-get install openoffice.org-java-common
```

---

### Post by PostChache on 2009-09-01
> **Partyboi2 said:**
> Have you got the openoffice.org-java-common package installed?
```
sudo apt-get install openoffice.org-java-common
```

After doing that I'm still getting this part of the error.

[B]** (soffice:5783): WARNING **: unable to get gail version number

~$ error - missing word count in dictionary file
Hash Manager Error : 4


[/B]

---

### Post by linfidel on 2009-09-01
> **PostChache said:**
> After doing that I'm still getting this part of the error.

[B]** (soffice:5783): WARNING **: unable to get gail version number

~$ error - missing word count in dictionary file
Hash Manager Error : 4

[/B]I also get that exact warning.  But, the app runs, so I don't know if it's meaningful or not.

---

### Post by Partyboi2 on 2009-09-02
Are you using other languages? Have a look at [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/367502"), they were having problems with the dutch language and fixed it installing the myspell-nl (dutch) package.

---

### Post by PostChache on 2009-09-02
> **Partyboi2 said:**
> Are you using other languages? Have a look at [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/367502"), they were having problems with the dutch language and fixed it installing the myspell-nl (dutch) package.
English is the only language I'm using.

I'm also getting this error while opening up a .pdf

$ 
(evince:29098): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

---

### Post by linfidel on 2009-09-02
I'm also not using any languages other than the standard English that is the default for me.

---

### Post by Partyboi2 on 2009-09-03
> **PostChache said:**
> English is the only language I'm using.

I'm also getting this error while opening up a .pdf

$ 
(evince:29098): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Have you got the gtk2-engines-ubuntulooks package installed?
```
dpkg -l gtk2-engines-ubuntulooks 
```
If not then install it
```
sudo apt-get install gtk2-engines-ubuntulooks
```

As for the > $ error - missing word count in dictionary file
Hash Manager Error : 4
Try reinstalling  myspell-en-us
```
sudo apt-get --reinstall install myspell-en-us
```

---

### Post by Hagar Delest on 2009-09-03
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile. Check that there is a JRE version _checked_ in Tools>Options>OOo>Java.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by PostChache on 2009-09-04
> **Partyboi2 said:**
> Have you got the gtk2-engines-ubuntulooks package installed?
```
dpkg -l gtk2-engines-ubuntulooks 
```If not then install it
```
sudo apt-get install gtk2-engines-ubuntulooks
```As for the 
Try reinstalling  myspell-en-us
```
sudo apt-get --reinstall install myspell-en-us
```

I did this and I'm still getting the same errors.

> Try to [reset your OOo user profile]("http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403") but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile. Check that there is a JRE version _checked_ in Tools>Options>OOo>Java.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")I made a new profile but I'm still getting the error. 
I'm afraid to install the Sun Version because it requires me to uninstall and I've had a problem where if I uninstall OpenOffice that I can't reinstall it and I have to reinstall Ubuntu to get it back on.

I checked Java and it says I have a JRE version called Sun Microsystems Inc.

---

### Post by Partyboi2 on 2009-09-04
Well, I am all out of ideas, maybe open a [[COLOR=Blue]bug report[/COLOR]]("https://bugs.launchpad.net/bugs/+filebug") I did read about the same bug that affects some Gentoo users.
[http://bugs.gentoo.org/242020](http://bugs.gentoo.org/242020)

---

### Post by PostChache on 2009-09-04
> **Partyboi2 said:**
> Well, I am all out of ideas, maybe open a [[COLOR=Blue]bug report[/COLOR]]("https://bugs.launchpad.net/bugs/+filebug") I did read about the same bug that affects some Gentoo users.
[http://bugs.gentoo.org/242020](http://bugs.gentoo.org/242020)


I'll be doing that then , thank you for all your help!

---

