---
title: "Reinstall Open Office"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by accooper on 2009-08-29
If I remove Open Office 3.0 with the add/remove in the applications menu and then add with the same add/remove menu, will I get Open Office 3.1?

TIA
Andrew From Texas

---

### Post by mikewhatever on 2009-08-29
No, you will not.

---

### Post by scouser73 on 2009-08-29
Openoffice Installation 3.1.0

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the **Linux .deb** file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

### Post by accooper on 2009-08-29
Thanks your instructions worked great!  Thanks for the help!

Andrew From Texas

---

