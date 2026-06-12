---
title: "Problem running commands at startup"
date: 2008-07-22
forum: General Help
---

### Post by Diego Garcia Mendoza on 2008-07-22
Hi,

i installed the madwifi modules and when i run the commands

```
modprobe ath_pci
modprobe wlan_scan_sta

```
Everything works perfect! So i want them to run automatically and i was reading about add them to */etc/modules* so i did it but nothing. Just don't work, i tried add them with and without the modprobe command.

I tried write a script in */etc/init.d/* and the ```
update-rc.d WIFI defaults 
``` without results of course.

I hope anyone can help me with this.

---

### Post by Separ on 2008-07-22
Try adding the commands under System > Preferences > Sessions

---

### Post by Tim Sharitt on 2008-07-22
Add them to /etc/modules
```
echo "ath_pci" | sudo tee -a /etc/modules
echo "wlan_scan_sta" | sudo tee -a /etc/modules
```

---

### Post by Diego Garcia Mendoza on 2008-07-25
Ok it's solved

I added the *modprobe *commands to the file */etc/rc.local*

Thanks for th suggestions ^^

---

