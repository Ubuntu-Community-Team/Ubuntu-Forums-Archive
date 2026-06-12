---
title: "No Hardware Drivers Applet ?"
date: 2008-07-18
forum: General Help
---

### Post by danny138 on 2008-07-18
I have a question, when I open Hardware drivers Applet it won't open, there is just a small box saying "No proprietary software installed on this system. What can or should I do about this as I realize the list of hardware is supposed to be displayed here. I'm brand new and trying to feel my way around. Any help is greatly appreciated, Thank You.

---

### Post by Viper666 on 2008-07-18
the hardware list won't appear there... that is only a list containing the "non-opensource" drivers (like videocard drivers)

---

### Post by danny138 on 2008-07-18
OK, Can you tell me how to view the hardware that is installed on system, hope this isn't totally out of line but I'm just getting this for 2 days after 13 years with those other guys. Wondering what took so long? Thank You for any help.

---

### Post by fragos on 2008-07-19
In a terminal run "lspci". "sudo lshw" will give more detailed information. The hardware drivers applet is only used to load proprietary drivers. It's telling you that all of your harware already has the necessary drivers to work -- no proprietary drivers required. Example would be the proprietary Nvidia 3D driver.

---

