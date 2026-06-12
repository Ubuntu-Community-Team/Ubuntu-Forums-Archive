---
title: "Problem with VirtualBox after installing updates"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by Ibrahim Mohammed Abdu on 2009-07-13
Hi,
Pls. Somebody should help me. My virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386 has freezy. Program crash showed on the notification bar. There4 i run sudo apt-get install -f @ the terminal in order to fix the problem. it shows that some programs would be removed others would be upgrade and i press yes to continue. after the installation the virtualbox was removed and i try reinstalling it but all in vain. it keep showing libqt4-network dependencies.
I tried install libqt4-network using synaptic manager bt came up with the following message:

Could not mark all packages for installation or upgrade
the following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

Libqt4-network:
Depends: libqtcore4 (=4.4.3-Obuntu1.2) but 4.5.0-Obuntu4.1 is to be installed.
Pls. help

---

### Post by Jose Catre-Vandis on 2009-07-13
Try downloading the latest virtualbox version (3.0) from their website and see how you get on. If it is a deb file it should handle your dependencies OK.

---

### Post by Ibrahim Mohammed Abdu on 2009-07-13
I've downlod virtualbox 3.0 and is still showing the same message.

---

### Post by Jose Catre-Vandis on 2009-07-14
Hmmm, are you running Intrepid (8.10) or Jaunty (9.04), as Intrepid has the 4.4 version of libqtcore whilst Jaunty has 4.5. If you are on Jaunty then you will need the Jaunty deb file for VBox.

You could try uninstalling everything to do with libqtcore and then force the 4.4 version if it is available?

---

### Post by Jose Catre-Vandis on 2009-07-14
:)

---

