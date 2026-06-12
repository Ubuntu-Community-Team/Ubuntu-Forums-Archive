---
title: "update manager not working. Unable to connect to ubuntu.org.ua http:"
date: 2008-09-20
forum: General Help
---

### Post by cic.11 on 2008-09-20
I have been running xubuntu on my travelmate 220 for a couple of weeks now, and everything has been great, i didnt even need a driver for my 2wire card. But yesterday and today i saw that there were 9 updates available, so i opened the update manager, clicked to install updates, the after some minutes i get this message:

> 
W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/br/brasero_0.8.1-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/br/brasero_0.8.1-1~getdeb1_i386.deb)
  Could not connect to ubuntu.org.ua:80 (91.193.124.193), connection timed out


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/gi/gimp_2.4.7-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/gi/gimp_2.4.7-1~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/gi/gimp-data_2.4.7-1~getdeb1_all.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/gi/gimp-data_2.4.7-1~getdeb1_all.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/li/libgimp2.0_2.4.7-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/li/libgimp2.0_2.4.7-1~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/pi/pidgin_2.5.1-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/pi/pidgin_2.5.1-1~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/li/libpurple0_2.5.1-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/li/libpurple0_2.5.1-1~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/pi/pidgin-data_2.5.1-1~getdeb1_all.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/pi/pidgin-data_2.5.1-1~getdeb1_all.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/tr/transmission-gtk_1.33-1~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/tr/transmission-gtk_1.33-1~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/tr/transmission-common_1.33-1~getdeb1_all.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/tr/transmission-common_1.33-1~getdeb1_all.deb)
  Unable to connect to ubuntu.org.ua http:

can some one help me, please.:confused:

---

### Post by sayakb on 2008-09-20
Goto System->Administration->Software Sources
Change the **Download from** drop menu entry to Main Server or something else. Then press Close button and press Reload button when prompted to. Now try again.

---

### Post by cic.11 on 2008-09-21
> **LinuxIsInnovation said:**
> Goto System->Administration->Software Sources
Change the **Download from** drop menu entry to Main Server or something else. Then press Close button and press Reload button when prompted to. Now try again.

ok i did that, then when i open the update manager i get the same message, also when i try to install linux multimedia studio from the synpatic package manager i get this message:

> W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/wi/wine_1.1.4+3dmarkPatch-0~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/wi/wine_1.1.4+3dmarkPatch-0~getdeb1_i386.deb)
  Could not connect to ubuntu.org.ua:80 (91.193.124.193), connection timed out


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/lm/lmms-common_0.3.2-0~getdeb1_all.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/lm/lmms-common_0.3.2-0~getdeb1_all.deb)
  Unable to connect to ubuntu.org.ua http:


W: Failed to fetch [http://ubuntu.org.ua/getdeb/ubuntu/hardy/lm/lmms_0.3.2-0~getdeb1_i386.deb](http://ubuntu.org.ua/getdeb/ubuntu/hardy/lm/lmms_0.3.2-0~getdeb1_i386.deb)
  Unable to connect to ubuntu.org.ua http:




for some reason im not being able to download anything from ubuntu
website, because i was able to download and install programs that were not from ubuntu. :confused:

---

### Post by cic.11 on 2008-09-23
i tried the same thing again today, but this time i restarted the laptop and it worked. thanks, i finally updated my laptop and got LMMS :)

---

