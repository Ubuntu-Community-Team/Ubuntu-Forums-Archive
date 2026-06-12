---
title: "you tube help"
date: 2008-07-26
forum: General Help
---

### Post by mikedemario17 on 2008-07-26
i installed the flash plug in ...both of them and when i go to you tube the pc freezes and i have to hard shut down.... how do i install them again with out going to the site ...or a code to install flash?

---

### Post by AnonCat on 2008-07-26
The following might help:

1. Type the following commands into the terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get remove -y --purge flashplugin-nonfree
sudo apt-get remove -y --purge libflashsupport

2. Unzip the file you downloaded from the Adobe/Flash site and right click the file that ends in .so and choose "copy"

3. in the terminal type:

sudo nautilus

4. now navigate to the following directories and paste the .so file into them:

/usr/lib/firefox
/usr/lib/firefox-3.0
/usr/lib/firefox-3.0/plugins

or if you installed Opera into one or both of these directories:

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins

That should be all you need to do

---

### Post by mikedemario17 on 2008-07-26
i didnt download the program on the pc... i just installed the plug in on fire fox... i didnt need to install flash on to mty desktop... i have done this b4 ...and just installing the plug-in in fire fox worked last time

---

### Post by oneporter on 2008-07-26
Why don't you try the new Flash v10 beta?  Either way, you probably need to get rid of the old plugins to try to fix it.

BTW: Installing a plugin downloads the file to your PC -- it just automates the process so you don't have to mess with it.

---

### Post by mikedemario17 on 2008-07-27
ooo i didnt know that..

---

### Post by mikedemario17 on 2008-07-28
> **AnonCat said:**
> The following might help:

1. Type the following commands into the terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get remove -y --purge flashplugin-nonfree
sudo apt-get remove -y --purge libflashsupport

2. Unzip the file you downloaded from the Adobe/Flash site and right click the file that ends in .so and choose "copy"

3. in the terminal type:

sudo nautilus

4. now navigate to the following directories and paste the .so file into them:

/usr/lib/firefox
/usr/lib/firefox-3.0
/usr/lib/firefox-3.0/plugins

or if you installed Opera into one or both of these directories:

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins

That should be all you need to do
how am i supost to find thos files? i cant find em

---

