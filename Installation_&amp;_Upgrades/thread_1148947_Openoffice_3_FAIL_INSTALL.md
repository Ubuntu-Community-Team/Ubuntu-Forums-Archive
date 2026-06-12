---
title: "Openoffice 3 FAIL INSTALL"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by HoCuS_PoKuS on 2009-05-04
I have been trying for about an hour now and can't get Openoffice 3 to install. I have done everything. Unintall 2.4, command line, looked on line.
WHAT AM I DOING WRONG???
this is becoming very annoying. =.= !!


sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

I have made several post with other problems that I couldn't get help on I hope i can with this one. =\

---

### Post by taurus on 2009-05-04
Which release are you running and what are the error messages when you ran those commands from a terminal?

---

### Post by HoCuS_PoKuS on 2009-05-04
Those were the commands I ran in terminal, in the directory on my desktop.

Running Ubuntu 8.04 

I get Errors on the amd archt. but im on intel so that not valid.

I get this on the desktop-intergration 

dpkg: regarding openoffice.org3.0-debian-menus_3.0-9376_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.0-9376) is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9376_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9376_all.deb
****

---

### Post by taurus on 2009-05-04
It's probably better to use the one from ppa.launchpad.net instead of installing it by hand.

---

### Post by Stupendoussteve on 2009-05-04
openoffice.org-debian-menues is trying to mess with files that were already messed with by openoffice.org-common.

Where did you get these .debs? It's best not to mix and match.

---

### Post by HoCuS_PoKuS on 2009-05-04
I downloaded them from OpenOffice site.

I haven't heard about using the ppa.launchpad, can you please explain ?

---

### Post by taurus on 2009-05-04
[http://ubuntuforums.org/showthread.php?t=1112178&highlight=install+openoffice+ppa.launchpad.net+hardy](http://ubuntuforums.org/showthread.php?t=1112178&highlight=install+openoffice+ppa.launchpad.net+hardy)

---

### Post by HoCuS_PoKuS on 2009-05-04
its shows office 3 but i cant access any of the apps. (writer/presentation)

damn i wish i remebered how i did it on my 7.10

---

### Post by HoCuS_PoKuS on 2009-05-04
I looked through synaptic and i go to add openoffice but it wont let me.

Bout to give up and just reinstall, since i can use 2.4 

since this was a new complete install again.

---

### Post by HoCuS_PoKuS on 2009-05-04
Ya, reinstall is looking nice. Been working on this for over 2hrs+ and nothing is working right. Everything is marked for install, done the cores, the works. Tried various install helps. =.=


It shows openoffice 3 in my /usr/bin but wont run it.

---

