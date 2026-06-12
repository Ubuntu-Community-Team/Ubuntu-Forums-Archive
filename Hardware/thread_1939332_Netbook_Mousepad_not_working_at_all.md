---
title: "Netbook Mousepad not working at all"
date: 2012-03-11
forum: Hardware
---

### Post by Jok3r098 on 2012-03-11
My netbook mousepad is not working, it seems to be not detecting it.
It was working when i was runnning Ubuntu 11.10, and during the installation process of xubuntu 11.10 but no longer. ive tried various packages in the software center and looked in as many forum threads regarding the same issue as i could find on google.

'dmesg | grep input' comes up with nothing but the laptop buttons and the usb mouse i had plugged in temporarily.

i dont know whether its ALPS or Synaptic, but it was working in ubuntu with no configuration necessary.

if there are no solutions I'd also appreciate suggestions on other distros which have native mousepad support (no unity, and preferably the ubuntu software center)

Feel free to ask for more info if it helps but after a while i might just start switching between different ubuntu variants until i find one that works nicley.

PS:
my netbook is a Compaq mini 110-c

---

### Post by ajgreeny on 2012-03-11
See what output you get  when you run the command ```
synclient -l
```

---

### Post by Jok3r098 on 2012-03-11
"Couldn't find synaptics properties. No synaptics driver loaded?"

---

### Post by ajgreeny on 2012-03-11
> **Jok3r098 said:**
> "Couldn't find synaptics properties. No synaptics driver loaded?"
So it is obviously not a synaptics touchpad.  Sorry but I have no idea where to go from here.

---

### Post by Jok3r098 on 2012-03-11
Thanks for trying

---

### Post by ajgreeny on 2012-03-12
I have done a quick search which may help; there seems to be some hope with a new .deb package mentioned in [http://ubuntuforums.org/showthread.php?t=1753920](http://ubuntuforums.org/showthread.php?t=1753920) 
and also information in [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) and in this googlubuntu search.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=alps+touchpad&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=alps+touchpad&as_qdr=all&sa=Google+Search&lang=en)

Good luck.

---

### Post by varunendra on 2012-03-12
I feel a bit stupid while posting this, but since I've experienced it myself, I thought it might be worth sharing.

I was installing 10.04.4 LTS on an Asus laptop (don't remember the model now, but is one of the latest, 15" with i5-2430M, 1GB Nvidia, & DOS OS). While playing with some settings the mouse got stuck. I tried the only driver I could remember then and it worked!-
```
sudo modprobe psmouse
```

Obviously it is a PS/2 mouse driver. I don't know how it worked, maybe some silly coincidence. After a reboot, it worked as usual, without requiring to 'modprobe' anything and I didn't bother to see the driver in use.

---

### Post by Jok3r098 on 2012-03-12
Thanks for all your help everyone but i was also having problems with the wirless card and proprieatry drivers for it so i reinstalled ubuntu 11.04.

then i found this: [http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

and now im updating, hopefully i will have a system just the way i like it again :)

i don't know whether to mark this as solved or not because the solution ive used doesn't fit the problem

---

