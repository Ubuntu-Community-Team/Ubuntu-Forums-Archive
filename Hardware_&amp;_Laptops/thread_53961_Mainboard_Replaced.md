---
title: "Mainboard Replaced"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by n21roadie on 2005-08-02
I replaced my faulty mainboard and now i discover on boot up , after user name and password , it says i have new mail and stops "james@james.$~ " , 
Being new to this , what is the next step ??, to complete the boot up process.

---

### Post by mo_x on 2005-08-03
The boot process has completed but you probably want to start X Windows. Enter the command startx. You probably want to start X automatically. I am not sure but I think you can do that by installing the gdm package.

---

### Post by n21roadie on 2005-08-03
Tried startx command and received 
XIO : FATAL ERROR IO ERROR 104

---

### Post by mo_x on 2005-08-04
There seems to be a problem with the configuration of your X server. Check the /etc/X11/xorg.conf file. Maybe you can reconfigure with the following command:
sudo dpkg-reconfigure xserver-xorg

---

