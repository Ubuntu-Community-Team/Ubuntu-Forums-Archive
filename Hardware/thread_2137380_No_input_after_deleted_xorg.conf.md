---
title: "No input after deleted xorg.conf"
date: 2013-04-20
forum: Hardware
---

### Post by editheraven on 2013-04-20
After an upgrade, I could not start my ubuntu 12.04. Lightdm wouldn't start and reinstalling video card driver did not worked. So I deleted xorg.conf. Now, Lightdm starts but I cannot use my mouse nor my keyboard. What should I do?



update : I managed to get a new xorg.conf.new file, cp-it but input still doesn't work. What could be the problem?

update 2 : this is my apt-get log that caused xserver failure : [http://textuploader.com/?p=6&id=IZiHb](http://textuploader.com/?p=6&id=IZiHb)

---

### Post by ibjsb4 on 2013-04-20
Were you offered a [partial upgrade?]("http://ubuntuforums.org/showthread.php?t=1859240")

In terminal, try this:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get dist-upgrade
```

---

### Post by editheraven on 2013-04-20
I managed to solve it : I reinstalled
 xserver-xorg 
xserver-xorg-core
xserver-xorg-input-all

---

