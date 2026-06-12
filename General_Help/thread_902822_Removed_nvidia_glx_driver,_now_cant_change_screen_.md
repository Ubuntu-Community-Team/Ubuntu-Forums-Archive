---
title: "Removed nvidia glx driver, now cant change screen resolution, please help"
date: 2008-08-27
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-27
I first installed a package that I was prompted to when I chose visual effect - extra.  Then my screen was all messed up and I couldn't get it back to normal.  So I figured I should uninstall nvidia glx drivers, and not I cant get a resolution more than 800x600.  Anyone know what I can do to get it back to the way it was at intial Ubuntu install?

---

### Post by fooman on 2008-08-27
i would give envyng a shot.  it is available in synaptic or you can install it from a terminal:

```
sudo apt-get install envyng-gtk
```

after it installs,  find it in applications > system tools

it will detect your card, install the nvidia drivers and configure x for you.

---

### Post by WRDN on 2008-08-27
First try fixing X Server, by typing in the Terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

You may also want to reinstall the Nvidia drivers you removed. I use a nvidia card (GeForce FX 5500), and in my experience, I haven't had much luck with the drivers in the repo's, so instead, I much prefer to download the drivers from Nvidia's website. This allows me to use the resolution I want (1280x1024), rather than 800x600 which I am limited to by other drivers.

---

### Post by TampaDeathSuperStar on 2008-08-27
couldnt figure out how how to post...so this is of the topic...i tried to down load java through a command in the terminal it looked like it was working..so i thought...and know i cant open synaptic package manager wont open it says............E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report....what do i do

---

### Post by fooman on 2008-08-27
tampa,  you need to start your own thread...back on the first page of general help,  look just under the bottom thread and on the left you will see a button : "new thread"

click it.

in the mean time...open a terminal and try running this:

```
sudo dpkg --configure -a
```

see if that helps.  if not, start the new thread and someone will get you fixed up.

---

### Post by Timberwolf5578 on 2008-08-27
I actually used ```
sudo dpkg-reconfigure -p high xserver-xorg
``` and it worked great.  But thanks for the responses everyone.

---

