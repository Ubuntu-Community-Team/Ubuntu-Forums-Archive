---
title: "Wireless no go."
date: 2009-09-13
forum: Hardware
---

### Post by Mardec on 2009-09-13
I have Ubuntu 9.04 currently installed on my Dell Inspiron 1200. I was having issues getting my computer to connect to the network wirelessly via a Dell Wireless 1350 PC Card. I found other pages pointing me towards b43-fwcutter or some such like that. Well I installed it and now I'm totally and utterly without any wireless options. Before he install I could enable wireless via the tray icon, and I had wireless options else where. But now the "Enable Wireless" check box that was once accessible from tray icon is gone, not just unselectible, totally vanished. As have all the rest of my wireless options. I would really appreaciate someone setting things straight for me.

---

### Post by community nerd on 2009-09-13
post the output of wireless yes go, lol :o
try going to system>administration>hardware drivers and click activate

---

### Post by Ayuthia on 2009-09-13
If you had wireless sites prior to installing b43-fwcutter, it sounds like you might have two wireless modules running at the same time.  You can check by going into the Terminal and checking:
```
lsmod|grep -e b43 -e ssb -e wl
```
If the wl module shows up with b43 or ssb, then that is the problem.  You can try the following to see if any wireless sites show up:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo iwlist scan
```
If wireless sites show up, you can first try and go to System->Administration->Hardware Drivers and disable the Broadcom STA option.  If that does not work you can disable the wl module by doing the following from the Terminal:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Hope that helps.  If it does not, can you post the results of:
```
lshw -C network
```

---

### Post by Mardec on 2009-09-13
Thank you so much [Ayuthia]("http://ubuntuforums.org/member.php?u=286983"). That worked perfectly and I have wireless internet again. I was getting ready to give up on the ubuntu community.

---

