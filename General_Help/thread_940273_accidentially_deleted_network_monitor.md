---
title: "accidentially deleted network monitor"
date: 2008-10-06
forum: General Help
---

### Post by tmapj on 2008-10-06
I accidentally deleted network manager and replaced it with klem, now i have no idea how to operate klem and thus cannot connect to the internet to download network manager. What can I do?

I do have a dual boot system, however, with windows vista, that has a network connection, if that is of any importance.

---

### Post by ryanhaigh on 2008-10-06
I assume you are talking about network manager? How did you delete it from the system?

---

### Post by Soupcan on 2008-10-06
Do you mean the icon in the notification area that shows what type of connection you have, and how strong your wireless signal is?

---

### Post by tmapj on 2008-10-06
Yes, I meant network manager and yes, soupcan.

---

### Post by Soupcan on 2008-10-06
> **tmapj said:**
> Yes, I meant network manager and yes, soupcan.

Deleted how? Did you remove it from your panel, or from your system?

---

### Post by tmapj on 2008-10-06
my system

---

### Post by lswb on 2008-10-06
I have no idea what klem is, is that a KDE program perhaps? Anyway some more information would be helpful. "network monitor" is a panel applet for gmome, but I,m guessing what your really want is the network manager panel applet. Did you actually uninstall it or just delete it from the panel? If just deleted from the panel, in gnome use 
Main Menu/System/Preferences/Sessions/Startup Programs and check the Network Manager box. If it doesn't appear right away log out of the desktop and back in again.
If you ARE really talking about the "network monitor" applet, just right-click on the panel, select Add to Panel, select Network Monitor & Add.

If you really did uninstall it, you can use command line tools to connect but need a better description of your connection, i.e. wired, wireless, dhcp or static, etc. If you have a live CD you can add it to the repositories with synaptic, then get NM from the CD.

---

