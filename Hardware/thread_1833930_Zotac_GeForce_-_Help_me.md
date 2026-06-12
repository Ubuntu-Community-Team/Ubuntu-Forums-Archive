---
title: "Zotac GeForce - Help me?"
date: 2011-08-26
forum: Hardware
---

### Post by TheCadaver on 2011-08-26
I recently purchased a Zotac GeForce GTX 550 Ti ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814500194](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500194)) off of newegg. I'm sure I installed it properly, it fit in the slot and whatnot, but, with problems. At first boot, with the DVI plugged into the graphics card, the computer would boot, but with a black screen, however i heard the ubuntu boot sounds and everything, so it seems my graphics card wasn't working when plugged into the card itself. Then, after some time of research and rebooting, now the opposite has happened, but with side effects. Now, the monitor only turns on when plugged into the graphics card, but ubuntu has a very small and fuzzy resolution (800x600) and only one other option beside it, 640x480, while the card it capable of going to 2560x1600. Also, being a brand-new card, i haven't installed the driver, and when i click "additional drivers" under system>administration, there are no options.

So... what might be the problem? The card's fan is spinning, and I'm using the monitor through it. Also, this is a fresh install of ubuntu 10.10, and i really haven't done anything. it was just like this on the card's first boot. Is it broken?

---

### Post by TheCadaver on 2011-08-26
bump

---

### Post by Frogs Hair on 2011-08-26
I'm surprised there is no driver offered in additional drivers . Run the update manager and check additional drivers again .

The next option is try and install the current stable driver from the terminal  . This will require reboot post installation .
```
sudo apt-get install nvidia-current
```The last option is a PPA that will provide the latest Nvidia drivers available for Ubuntu . 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
``````
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

---

### Post by TheCadaver on 2011-08-26
> **Frogs Hair said:**
> I'm surprised there is no driver offered in additional drivers . Run the update manager and check additional drivers again .

The next option is try and install the current stable driver from the terminal  . This will require reboot post installation .
```
sudo apt-get install nvidia-current
```The last option is a PPA that will provide the latest Nvidia drivers available for Ubuntu . 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
``````
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

I tried
 ```
sudo apt-get install nvidia-current
```
I did get a driver in my additional drivers, and it says it's in use, but when i proceeded to change my resolution to normal, I'm asked, "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?". When I clicked okay, I get, "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." running sudo nvidia-xconfig did nothing. Are you sure what you gave me would give me the correct driver directly for my card? Install nvidia-settings seems a bit generic, isn't there a specific one for "GeForce GTX 550 Ti"?

Haven't tried the other two options yet.

---

### Post by Frogs Hair on 2011-08-26
The Nvidia current driver is the one that would be offered by additional drivers .   The last option is actually  three commands the first to connect to the source and the last box is two commands that install Nvidia settings and the driver .

---

### Post by TheCadaver on 2011-08-26
Hm.. is there any way to check whether my graphics card is properly functioning? I haven't got any games installed yet, but most i can think of won't work on ubuntu without tedious wine working and whatnot anyways, so I can't check frame rates.

---

### Post by Frogs Hair on 2011-08-27
There are games in the software center that require 3D drivers . select a games category an type 3d into the search box .

---

### Post by TheCadaver on 2011-08-27
Well, I just revolted my computer to do that, and now I'm stuck on the same problem that made me rebuild the computer and reinstall ubuntu. Every time I boot, rather than the ubuntu login screen, I get a tty1 login screen, a black screen where all it says is, "ubuntu 10.10 Neptune tty1" and "Neptune login", where Neptune is the name of my computer. The previous time, after 3 pages of help on my forum thread, nobody could solve this problem. Ugh.

Edit: Well, I've reinstalled ubuntu (again) and now I'm back to the beggining, with the screen resolution being tiny and whatnot.

Edit 2: I tried your last option and got the driver once again, Then went to go test one of ubuntu's 3D games, and those were definetely not the framerates of a 1000Mhz Core Clock graphics card, so it probably isn't working.

---

### Post by TheCadaver on 2011-08-28
bump.

Also, I removed my graphics card to see what would happen, and my screen resolution is back to normal.

---

### Post by TheCadaver on 2011-08-29
bump.

---

### Post by realzippy on 2011-08-29
So what is status quo now?
Nvidia driver installed,bad resolution?

---

### Post by TheCadaver on 2011-08-30
No driver installed currently, bad resolution, and frame rates equal to that of integrated graphics.

---

### Post by TheCadaver on 2011-08-30
Bump.

Also, In the Zotac Troubleshoot thing, it says that a bad screen resolution without the ability to change it is likely either corrupt driver, wrong driver or no driver.

What if I tried downloading the driver off of Nvidia's website?

---

### Post by realzippy on 2011-08-31
Nvidia download center offers 280.13 for your card.
You can get the same driver also when adding xswat ppa to your system,
so you had not to install manually and repeat install every time a kernel
update comes.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```

Also update your system before installing nvidia-driver
```
sudo apt-get upgrade
```
Then install nvidia-current
(which now is from xswat ppa)
 using addditional drivers tool (jockey)

```
jockey-gtk
```

reboot.

---

### Post by TheCadaver on 2011-09-05
I... I love you. you saved me thousands of dollars. I'm not sure what to say. You're awesome.

---

### Post by ademus4 on 2012-03-11
Fantastic, worked with my system too.

Ubuntu 10.04 LTS with Zotac GTS450.

Cheers!

---

