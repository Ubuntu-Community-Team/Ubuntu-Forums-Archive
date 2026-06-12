---
title: "Ubuntu and gfx drivers..."
date: 2008-09-08
forum: General Help
---

### Post by l33t p1mp on 2008-09-08
I have an 8800 gts 512 with ubuntu 8.04 installed. Ubuntu tries to install the drivers, it connects, then gives a 404. Heres a screenshot.

---

### Post by overdrank on 2008-09-08
> **l33t p1mp said:**
> I have an 8800 gts 512 with ubuntu 8.04 installed. Ubuntu tries to install the drivers, it connects, then gives a 404. Heres a screenshot.

Hi and you may change your server location in software sources located under system, administration.

---

### Post by ryanhaigh on 2008-09-09
Just to make it a little clearer go to system>administration>software sources and change the server to another (preferably local) one.

EDIT: Actually it looks like the package isn't found on the main ubuntu server which is a little strange. Perhaps try updating your list of packages by opening synaptic (system>admin>synaptic package manager) and pressing the reload button. You could also install nvidia-glx-new directly from within synaptic, just search for it and mark for installation then click apply.

---

### Post by l33t p1mp on 2008-09-09
Perfect, thanks overdrank and ryanhaigh, I did what you said with the synaptic package manager, then went back to the hardware drivers, it installed, and will reboot. All work fine now. Since I was downloading updates, tossed in a few compiz fusion goodies. :P

---

### Post by l33t p1mp on 2008-09-09
Ok, I am back, and after 2 restarts, it still isnt working. I restarted, just like it asked. Upon boot, it gives me a list saying it is running in low-quality mode because it can not find my video card. I go to the drop down menus that it had, chose my lcd monitor, and my video card. It boots, and then the MAX resolution it gives me is 800x600. Before I downloaded and installed the drivers, I ran 1680x1050 like my lcd supports. It says that it needs to reboot again, so I click the reboot button, and same thing again...I am back on ubuntu, and it is the same thing, except it does not ask me to reboot anymore...max resolution of 800x600 again...any ideas?
Thanks in advance.

---

### Post by l33t p1mp on 2008-09-09
I have officially tried all I know, and it still does not work. Please help. :(

---

### Post by ryanhaigh on 2008-09-09
The nvidia drivers come with their own configuration tool. Boot into your install and log in then press alt-f2 and enter
```
gksudo nvidia-settings
```
You can then configure your monitors as you want and once you are happy with the settings press the Save X Configuration button. This will make some changes to your /etc/X11/xorg.conf so as always back it up first!
```

cp /etc/X11/xorg.conf ~/

```

---

### Post by l33t p1mp on 2008-09-09
And...How do I boot into install exactly? Thanks.

---

### Post by ryanhaigh on 2008-09-09
I just meant boot into your currently installed system (aka normal boot).

---

### Post by l33t p1mp on 2008-09-09
Ok, so boot into ubuntu, use alt+f2, and do what you said in the previous post?

---

