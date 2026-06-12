---
title: "[SOLVED] OpenOffice.org ppa failure?"
date: 2008-11-30
forum: General Help
---

### Post by brandoncolorado on 2008-11-30
I recently lost my openoffice.org 3.0 for some strange reason.  I reverted back to openoffice.org 2.4.1 by uninstalling/reinstalling via add/remove applications.  Now I am in trouble here.  It seems that my long school outlines don't render in 2.4.1 in outline format, so I need 3.0 back! 
I followed these instructions:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)


I added the PPA repository to the synaptic repositories:
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)


Then I ran this:
sudo aptitude update && sudo aptitude full-upgrade -y

and I tried the GUI updater too, but my computer is not updating to the latest version of openoffice.org.

How can I update to 3.0 without having to download the .deb files?

Thanks!

---

### Post by binbash on 2008-11-30
pkgs are removed from that repo around last week.As far as i know there is no repo except that.

---

### Post by brandoncolorado on 2008-11-30
> **binbash said:**
> pkgs are removed from that repo around last week.As far as i know there is no repo except that.

:(    Does that mean I need to install some other way?

Can I just download a .deb and install it like any other software?

---

### Post by binbash on 2008-11-30
[http://ubuntuforums.org/showthread.php?t=998319](http://ubuntuforums.org/showthread.php?t=998319)

---

### Post by ugm6hr on 2008-11-30
Instructions to install OO.org3 with .debs:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by brandoncolorado on 2008-11-30
Thanks for the help. 

I followed those instructions, including installing the last .deb, and now I get a crash every time I start any OpenOffice program.  I tried re-doing everything, it went through without errors, and now I still can't start them.

---

### Post by exploder on 2008-11-30
I have used the method ugm6hr posted a link to in Intrepid, Hardy and Mint 5 with no problems of any kind. I removed OO 2.4 before installing 3.0. The command listed in the How To can easily be changed to install OO 2.4 if things go wrong.

The Sun deb install has the advantage of having the auto update feature enabled, this sure beats waiting for updated versions to come into the repos.

---

### Post by ugm6hr on 2008-11-30
In Terminal:
```
opt/openoffice.org3/program/soffice
```

---

### Post by brandoncolorado on 2008-11-30
> **ugm6hr said:**
> In Terminal:
```
opt/openoffice.org3/program/soffice
```

Thanks for all of your help.  I had trouble with that command, but managed to fix the problem by deleting the openoffice folders in the home folder prior to a new installation.

Thanks!

---

### Post by Arup on 2008-11-30
The Sun deb works fine and the only thing missing is the quickstart which is available in the Ubuntu OO3.

---

