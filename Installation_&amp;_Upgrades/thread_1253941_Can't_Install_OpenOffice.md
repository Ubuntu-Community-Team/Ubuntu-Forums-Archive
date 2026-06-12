---
title: "Can't Install OpenOffice"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by PostChache on 2009-08-30
I removed OpenOffice due to errors I was getting before. I read somewhere to remove it to type sudo apt-get remove openoffice* now I want to reinstall it, I was following these instructions [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) But whenever I go to Update Manager no updates appear. How do I reinstall Open Office D:

---

### Post by Partyboi2 on 2009-08-30
Hi, make sure you reload the package list first.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by running_rabbit07 on 2009-08-30
Another way to install OpenOffice.org is via their website.

---

### Post by PostChache on 2009-08-30
> **Partyboi2 said:**
> Hi, make sure you reload the package list first.
```
sudo apt-get update
sudo apt-get upgrade
```
Then what do I do D:

---

### Post by Partyboi2 on 2009-08-30
> **PostChache said:**
> Then what do I do D:
Sorry my mistake I forgot that you have already removed OO,
After reloading the package list open up Add/Remove (Applications>Add/Remove) and searching for 'OpenOffice.org' and install the packages.

---

### Post by PostChache on 2009-08-30
> **Partyboi2 said:**
> Sorry my mistake I forgot that you have already removed OO,
After reloading the package list open up Add/Remove (Applications>Add/Remove) and searching for 'OpenOffice.org' and install the packages.
It says it can't install due to conflicts and to go to Synaptic but I don't know what to do when I get there.

---

### Post by running_rabbit07 on 2009-08-30
> **PostChache said:**
> It says it can't install due to conflicts and to go to Synaptic but I don't know what to do when I get there.

After you open Synaptic. Search openoffice.org, then click the box beside openoffice.org or you can choose whichever part of openoffice you wanted, then click the green arrow at the top.

---

### Post by PostChache on 2009-08-30
> **running_rabbit07 said:**
> After you open Synaptic. Search openoffice.org, then click the box beside openoffice.org or you can choose whichever part of openoffice you wanted, then click the green arrow at the top.
[IMG]file:///home/cha-che/Desktop/Screenshot-Untitled%2520Window.png[/IMG][IMG]http://img42.imageshack.us/img42/7058/41906990.png[/IMG]

What do I do now?

---

### Post by running_rabbit07 on 2009-08-30
The only other thong I can think of that may get it to install is, ```
sudo apt-get install openoffice.org
```I am sure there are other fixes but they are beyond my skill level. If the above doesn't work let us know and someone will throw in some other advice.

If you are in school like. like me, and need a word processor, install Abiword. Abiword even has the capability to save to .docx if you need it to.

---

### Post by PostChache on 2009-08-30
> **running_rabbit07 said:**
> The only other thong I can think of that may get it to install is, ```
sudo apt-get install openoffice.org
```

Doing that gave me this 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm following this guide now xD [http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F]("http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F") but I'm stuck when it says

3. Grant permission to open a graphical display for root, using the authority from your user account. This step is necessary for security reasons on some systems, while on other systems adequate security is provided without this. 
   XAUTHORITY=/home/{username}/.Xauthority; export XAUTHORITY
  DISPLAY=:0.0; export DISPLAY
4. Change to the directory that contains the OOo 3 installation program. 

When I type su - "It tells me Authentication failure"

And ontop of that on Step 4 I don't know which directory contains the OOo3! 
This is really confusing now T.T

---

### Post by running_rabbit07 on 2009-08-30
To install Abiword if you need it, just search in Synaptic and install it.

---

### Post by running_rabbit07 on 2009-08-30
> **PostChache said:**
> I'm following this guide now xD [http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F]("http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F") but I'm stuck when it says

3. Grant permission to open a graphical display for root, using the authority from your user account. This step is necessary for security reasons on some systems, while on other systems adequate security is provided without this. 
   XAUTHORITY=/home/{username}/.Xauthority; export XAUTHORITY
  DISPLAY=:0.0; export DISPLAY
4. Change to the directory that contains the OOo 3 installation program. 

When I type su - "It tells me Authentication failure"

And ontop of that on Step 4 I don't know which directory contains the OOo3! 
This is really confusing now T.T

Down load it from Openoffice.org and put it in your home folder.

Before the command you are trying to do, type ```
sudo
``` on front of it.

When it asks for a password, type it in. It will not show any dots for letters entered.

---

### Post by PostChache on 2009-08-30
> **running_rabbit07 said:**
> Down load it from Openoffice.org and put it in your home folder.

Before the command you are trying to do, type ```
sudo
``` on front of it.

When it asks for a password, type it in. It will not show any dots for letters entered.
Okay I've done that, do I change the directory to the extracted folder on my Desktop? If so whenever I do ./setup I get bash: ./setup: No such file or directory

---

### Post by running_rabbit07 on 2009-08-30
Did you download the .deb?

The last time I did the manual install I used this sites[ instructions]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04").

---

### Post by Partyboi2 on 2009-08-30
> **PostChache said:**
> Okay I've done that, do I change the directory to the extracted folder on my Desktop? If so whenever I do ./setup I get bash: ./setup: No such file or directory
What version of Ubuntu are you running?

---

### Post by PostChache on 2009-08-30
> **Partyboi2 said:**
> What version of Ubuntu are you running?
9.04 64bit

---

### Post by Partyboi2 on 2009-08-30
Lets try back tracking, open Software Sources (System>Admin>Software Sources) and go to the "Third Party Software" tab and remove
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```Then reload the package list and  open Add/remove and try installing Open office.org.

---

### Post by running_rabbit07 on 2009-08-30
> **Partyboi2 said:**
> Lets try back tracking, open Software Sources (System>Admin>Software Sources) and go to the "Third Party Software" tab and remove
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```Then reload the package list and  open Add/remove and try installing Open office.org.
The version in the jaunty repos is 3.01 so you do not need to use that 3rd party repo.

I was looking for that one, but couldn't find it. Thanks for stepping in.

---

### Post by PostChache on 2009-08-30
> **running_rabbit07 said:**
> Did you download the .deb?

The last time I did the manual install I used this sites[ instructions]("http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04").
When I follow those instructions I get this 

dpkg: error processing ooobasis3.1-base_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-binfilter_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-calc_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core01_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core02_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core03_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core04_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core05_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core06_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-core07_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-draw_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-base_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-binfilter_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-calc_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-draw_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-help_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-impress_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-math_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-res_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-en-us-writer_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-gnome-integration_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-graphicfilter_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-images_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-impress_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-javafilter_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-kde-integration_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-math_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-onlineupdate_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-ooofonts_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-oooimprovement_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-ooolinguistic_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-pyuno_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-testtool_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-writer_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing ooobasis3.1-xsltfilter_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-base_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-calc_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-en_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-es_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-dict-fr_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-draw_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-en-us_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-impress_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-math_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org3-writer_3.1.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing openoffice.org-ure_1.5.0-11_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ooobasis3.1-base_3.1.0-11_i386.deb
 ooobasis3.1-binfilter_3.1.0-11_i386.deb
 ooobasis3.1-calc_3.1.0-11_i386.deb
 ooobasis3.1-core01_3.1.0-11_i386.deb
 ooobasis3.1-core02_3.1.0-11_i386.deb
 ooobasis3.1-core03_3.1.0-11_i386.deb
 ooobasis3.1-core04_3.1.0-11_i386.deb
 ooobasis3.1-core05_3.1.0-11_i386.deb
 ooobasis3.1-core06_3.1.0-11_i386.deb
 ooobasis3.1-core07_3.1.0-11_i386.deb
 ooobasis3.1-draw_3.1.0-11_i386.deb
 ooobasis3.1-en-us_3.1.0-11_i386.deb
 ooobasis3.1-en-us-base_3.1.0-11_i386.deb
 ooobasis3.1-en-us-binfilter_3.1.0-11_i386.deb
 ooobasis3.1-en-us-calc_3.1.0-11_i386.deb
 ooobasis3.1-en-us-draw_3.1.0-11_i386.deb
 ooobasis3.1-en-us-help_3.1.0-11_i386.deb
 ooobasis3.1-en-us-impress_3.1.0-11_i386.deb
 ooobasis3.1-en-us-math_3.1.0-11_i386.deb
 ooobasis3.1-en-us-res_3.1.0-11_i386.deb
 ooobasis3.1-en-us-writer_3.1.0-11_i386.deb
 ooobasis3.1-gnome-integration_3.1.0-11_i386.deb
 ooobasis3.1-graphicfilter_3.1.0-11_i386.deb
 ooobasis3.1-images_3.1.0-11_i386.deb
 ooobasis3.1-impress_3.1.0-11_i386.deb
 ooobasis3.1-javafilter_3.1.0-11_i386.deb
 ooobasis3.1-kde-integration_3.1.0-11_i386.deb
 ooobasis3.1-math_3.1.0-11_i386.deb
 ooobasis3.1-onlineupdate_3.1.0-11_i386.deb
 ooobasis3.1-ooofonts_3.1.0-11_i386.deb
 ooobasis3.1-oooimprovement_3.1.0-11_i386.deb
 ooobasis3.1-ooolinguistic_3.1.0-11_i386.deb
 ooobasis3.1-pyuno_3.1.0-11_i386.deb
 ooobasis3.1-testtool_3.1.0-11_i386.deb
 ooobasis3.1-writer_3.1.0-11_i386.deb
 ooobasis3.1-xsltfilter_3.1.0-11_i386.deb
 openoffice.org3_3.1.0-11_i386.deb
 openoffice.org3-base_3.1.0-11_i386.deb
 openoffice.org3-calc_3.1.0-11_i386.deb
 openoffice.org3-dict-en_3.1.0-11_i386.deb
 openoffice.org3-dict-es_3.1.0-11_i386.deb
 openoffice.org3-dict-fr_3.1.0-11_i386.deb
 openoffice.org3-draw_3.1.0-11_i386.deb
 openoffice.org3-en-us_3.1.0-11_i386.deb
 openoffice.org3-impress_3.1.0-11_i386.deb
 openoffice.org3-math_3.1.0-11_i386.deb
 openoffice.org3-writer_3.1.0-11_i386.deb
 openoffice.org-ure_1.5.0-11_i386.deb

---

### Post by Partyboi2 on 2009-08-30
Open a terminal and try clearing the cache before installing open office
```
sudo apt-get clean
```

---

### Post by PostChache on 2009-08-30
> **Partyboi2 said:**
> Lets try back tracking, open Software Sources (System>Admin>Software Sources) and go to the "Third Party Software" tab and remove
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```Then reload the package list and  open Add/remove and try installing Open office.org.

Doing that gave me this 

OpenOffice.org cannot be installed on your computer type (amd64)

Either the application requires special hardware features or the vendor decided to not support your computer type.

I did the sudo apt-get clean as well and got the same error




I think I'm just going to backup my files and reinstall Ubuntu ._. this is frustrating me

---

