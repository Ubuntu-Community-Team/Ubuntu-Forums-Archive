---
title: "network configuration"
date: 2008-11-23
forum: Hardware
---

### Post by svonk on 2008-11-23
I'm having some problem with setting up my wireless on a dell laptop with ubuntu 8.10. Almost all the tutorials contains a part with the menu entry system/administration/networking but I do not have it only network tools but it doesn't have the described stuff, like enable roaming etc.. Any suggestion? I'm desperate I`ve been struggling with this for more than a week. Thanks!

---

### Post by doas777 on 2008-11-23
well, I can't really help with wireless issues, but anyone who could would need to know what type of wifi card you have. if you open a terminal and type:
```
sudo lshw -c network
```

what comes up? it would help those who can help, and perhaps I would google "Intrepid <insert card model here>" and see what tutorials and threads come up.

good luck,
franklin

---

### Post by svonk on 2008-11-23
I have broadcom 4328/ dell 1500 draft. I found a lots of tutorials. I installed the driver with ndiswrapper. It says driver installed, hardware is there, but I always stuck at the above mentioned point. I couldn't find any sign of the wireless nowhere. Sometimes the led on the laptop lights up though after restart. I dual boot and it works fine with windows I just wanna give a chance to ubuntu. Thanks!

---

### Post by Zteam on 2008-11-24
Just install gnome-network-admin from synaptic (or run sudo apt-get install gnome-network-admin from the terminal) that should fix the missing menu item :)

---

### Post by Wolfhere on 2008-11-27
solved the same problem for me. Thank you. Intrepid does not install this by default. I needed a static assignement for likewise to work correctly. I used the networking launcher on the panel to no avail. I would configure the network there and lose the static on next boot. /etc/network/interfaces showed only auto eth0...no static config. I followed your advice, rebooted and network-admin works. Awesome!:guitar:

---

