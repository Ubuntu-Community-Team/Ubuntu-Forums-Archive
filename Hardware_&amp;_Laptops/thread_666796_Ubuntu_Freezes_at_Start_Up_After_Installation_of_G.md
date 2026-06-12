---
title: "Ubuntu Freezes at Start Up After Installation of Grapics Driver[Restricted DriverATI]"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by hxczach on 2008-01-13
Hi,
I recently installed ubuntu 7.10 everything went smoothly.
It started up and was fine, but the graphics driver hadnt been installed yet.
So i enabled the restricted ATI driver, and restarted, but now when its supposed to be loading the log in screen, it just sits and has a circle loading cursor.
I've had 7.10 installed and working fine before, with the restricted driver working, and even compiz fusion working fine.
I have a ATI Mobility Radeon x1800
Im completly stumped.

P.S.-I did a fresh install twice, and it did it both times.

Maybe it installed something different from the internet this time, as opposed to when i had it working a few month ago.

Any help would be much appreciated.

---

### Post by hxczach on 2008-01-13
bump

---

### Post by hxczach on 2008-01-14
bump again

---

### Post by Yellow Pasque on 2008-01-14
I'm guessing you used the Ubuntu Restricted drivers, not the ones downloaded from the ATI site? I would try the ATI version if Ubuntuy's version isn't working

When you get to the screen where it just hangs, press Ctrl+Alt+F1 to get back to the terminal. Then you can do:
```
sudo apt-get remove xorg-driver-fglrx
```
That should get you back to low-graphics mode, where you can fire up a browser and download the driver from ATI. I would recommend installing from a terminal (press Ctrl+Alt+F1 again).
```
sudo sh ati-driver-installer-8.443.1-x86.x86_64.run
sudo aticonfig --initial -f --overlay-type=Xv
```

---

### Post by hxczach on 2008-01-14
thanks, but now the problem seems a little worse.
after installing the ATI drivers from the ati site, the screen is black when i boot it up.
it has a few discolored lines running throughout the screen, but thats about it.
Do need to edit my xorg to use the new driver?

---

### Post by Yellow Pasque on 2008-01-14
Hmm. Sorry that didn't work. (BTW, aticonfig --initial -f edits your xorg for you)

You can uninstall the Catalyst drivers with:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

Reinstall the Ubuntu drivers and do an aticonfig on them:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```

Reboot. If that doesn't work, then post /var/log/Xorg.0.log and we'll see what's locking up X.

---

### Post by hxczach on 2008-01-14
No luck.
I thank you for your help though.
I plan on doing a fresh install tomorrow. 
How should i go about installing the ATI drivers, and what version should they be?

---

### Post by Yellow Pasque on 2008-01-14
There's no reason to do a fresh install. Please post /var/log/Xorg.0.log so we can determine the problem with the restricted drivers.

Or you can remove the restricted driver and go back to the open-source "radeon" driver.

---

### Post by hxczach on 2008-01-19
I decided to just do a fresh install, because i need to move my partitions around anyways.
So after it installs, and first boots, how should i install the ATI drivers?
Should i download then from the ati site, and run the .run file from the terminal?

Thank you for any help

---

### Post by Z_o-s-o on 2008-01-20
I don't  have a solution but I was having the same problem with an X1300 and an HD 2400 the other day.

Installing the drivers had various problems on several clean installs.

---

### Post by Yellow Pasque on 2008-01-20
I think this is the best install guide I can offer you:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by hxczach on 2008-01-20
Thank you.
That guide worked perfectly.
Thank you again for all your help. :)

---

