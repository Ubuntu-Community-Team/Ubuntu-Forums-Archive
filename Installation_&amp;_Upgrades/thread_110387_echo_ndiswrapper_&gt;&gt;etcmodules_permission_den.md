---
title: "echo ndiswrapper &gt;&gt;/etc/modules :permission denied. Need HELP!!!"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by nofx1510 on 2005-12-30
when i goto type in echo ndiswrapper >> /etc/modules i get the message of permission denined. Do i have to be in the root account if so how do i log into it because at the login screen it says root cannot login at that screen. I got the card to work great its just when i restart i need to retype sudo crap and that gets annoying. Any help would be greatly appreicaiated. I know im probably missing something cause im a complete noob but i will try and learn...

---

### Post by kaamos on 2005-12-30
in a terminal
```

sudo su

```
This logs you in as root.
```

echo "ndiswrapper" >> /etc/modules

```
This adds the line ndiswrapper to the text file modules.
```

exit

```
This logs out root.

Hope this helps. Also might be a good thing to read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nofx1510 on 2005-12-30
thanks man you helped out alot. i will read up on it its just my first day in linux so i kinda dove head first not knowing how to swim. This has been a fun day so far.

---

