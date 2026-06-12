---
title: "OpenOffice 3 cannot open after restarted."
date: 2008-10-24
forum: General Help
---

### Post by akpower on 2008-10-24
I just installed oo3 in Ubuntu 8.04 yesterday.
I cannot find those application icons under Application>Office , and can't open a doc by clicking it which pop-up an message "There is no application installed for this file"
However, I can open oo3 main menu by using /opt/openoffice.org3/program/soffice

anyone can solve this problem for me, please!!!
Thank you!

---

### Post by kpkeerthi on 2008-10-24
you could add /opt/openoffice.org3/program/ to your $PATH env variable.

Or right-click on the doc -> Properties -> Open with and choose /opt/openoffice.org3/program/soffice -writer

---

### Post by caleb12 on 2008-10-24
Open Office 3 installs itself quietly in regards to application icons and system integration. It's not meant to replace 2.4 as of yet, so I would gather that is why they install in this manner. 

There are basically two things you have to do... one, open nautilus and right click on the document you want to open and select "Open With" then enter the path to the soffice binary. Nautilus will remember the association in the future. 

Right click on your desktop and select "Add Launcher" and again... navigate to the soffice binary. To put it in the Main Menu - basically follow the same instructions above, jsut right click on the Main Menu icon and select Edit. Then start adding your launchers...

---

### Post by akpower on 2008-10-26
I installed the OO3 by following the instruction.
I removed the openoffice 2.4 before installation
cd  OOO300_m9_native_packed-1_en-US.9358/DEBS/
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

It's working after installed. However, it disappear after turn off the computer and open it again.

The "add launcher" is working! Can I open work & excel togethre?
When I use this method, I can only open either work or excel... it is wired....

Thank you

---

