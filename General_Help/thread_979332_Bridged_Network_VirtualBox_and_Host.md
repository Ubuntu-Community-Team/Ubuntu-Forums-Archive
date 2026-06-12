---
title: "Bridged Network VirtualBox and Host"
date: 2008-11-11
forum: General Help
---

### Post by FLCL on 2008-11-11
So previously i had created a bridge between my virtual machine and my host, and in the process i created a back up of my configuration settings, but now i want to restore back to those original interfaces. Can anyone explain how to me please?
I followed the tutorial here: [HTML]https://help.ubuntu.com/community/VirtualBox#Networking[/HTML]

---

### Post by FLCL on 2008-11-11
Please help :(

---

### Post by Liv3dN8as on 2008-11-13
type in the terminal ```
gksu nautilus /etc/network
```It will ask you for your password and put you right in the directory you want to be in. Then just find the backup you made with the date and time and rename it to the old one.

---

### Post by akelsall on 2008-11-16
Are you saying you modified the /etc/network/interfaces file? If so, all you have to do is the following:

     cd /etc/network 
     sudo  cp  *backed_up_file_name*  **interfaces**

For example, if you backed up your **interfaces** file and named it *interfaces.bak*, you would enter
 
     sudo  cp  interfaces.bak  interfaces

You can use the same principle if you're talking about a different file. If you think you might want to go back to your modified file at some point, be sure to back it up as well before overwriting it. 

Andy

---

