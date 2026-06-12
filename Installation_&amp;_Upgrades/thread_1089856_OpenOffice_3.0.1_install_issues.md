---
title: "OpenOffice 3.0.1 install issues"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Fazesilver on 2009-03-07
Hey guys,

I tried following this guide to install the new version of open office: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

I followed the process exactly and on the "Update Manager" step my update manager removed the old version of Open Office but it did not load the new one in.

I then tried following this guide to install it more "manually": [http://ubuntuforums.org/showthread.php?p=6639054#post6639054](http://ubuntuforums.org/showthread.php?p=6639054#post6639054)

Open Office does not appear in the office sub-category of the Applications menu. When I go into the Add/Remove to try to remove or add Open Office it is unchecked and when I try to install it it says "This application conflicts with other installed software. To install 'openoffice.org-writer' the conflicting software must be removed first. Switch to 'synaptic' package manager to resolve this conflict."

 So then I did this and all of the open office packages are not selected or the boxes do not have anything filled in as if the program is not installed. When I try to mark it for re-installation I get this error:

"Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

openoffice.org-base-core:
 Depends: openoffice.org-core but it is not going to be installed
  Depends: libgcc1 (>=1:4.3) but 1:4.2.3-2ubuntu7 is to be installed
  Depends: libstdc++6 (>=4.3) but 4.2.3-2ubuntu7 is to be installed
 Depends: ure but it is not going to be installed"

So now I absolutely do not know what to do if it is uninstalled? Or what is a way to get all of the required packages too??

Thanks for the help.

---

### Post by snowpine on 2009-03-07
Hi Fazesilver, which version of Ubuntu do you have installed? OpenOffice 2.4 is recommended for all versions of Ubuntu prior to 9.04 Jaunty, which will include OO3 in its repositories.

---

### Post by Fazesilver on 2009-03-08
I am running the 8.04 Hardy.

So since I have to wait for open office 3 is there a way to reinstall open office 2.4? As I mentioned in the first post it does not let me install openoffice from the Add/Remove list because there is a conflict with already installed software...

---

### Post by chubble10 on 2009-03-08
> **Fazesilver said:**
> I am running the 8.04 Hardy.

So since I have to wait for open office 3 is there a way to reinstall open office 2.4? As I mentioned in the first post it does not let me install openoffice from the Add/Remove list because there is a conflict with already installed software...
Try looking for OO stuff in package manager

---

### Post by Fazesilver on 2009-03-08
Ok I got it working. I just had to disable the repository that I added for the upgrade and I was able to re-install openoffice 2.4 without any software conflicts.

---

### Post by snowpine on 2009-03-08
> **Fazesilver said:**
> I am running the 8.04 Hardy.


Ah, that explains it... the tutorial you linked to is for 8.10 intrepid. I'm pretty sure OO3 can also be installed in 8.04, but you need to look for a tutorial specific to 8.04 Hardy Heron.

---

### Post by LindaLou on 2009-03-10
Faxesilver, this link might help you.  It's a Tutorital for Oo 3.0 install on Ubuntu 8.04.  Read thru the instructions prior to installing the Oo upgrade and note that the instructions work for previously uninstalled Oo. a 

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

