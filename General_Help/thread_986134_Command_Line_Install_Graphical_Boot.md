---
title: "Command Line Install Graphical Boot"
date: 2008-11-18
forum: General Help
---

### Post by mashcaster on 2008-11-18
After completing a command line install, when I start the computer, I see lots of gobldy goop text on the screen before it asks me to login via command line.

How do I install the graphical progress bar which is shown on a standard ubuntu install when the OS is loading?

---

### Post by taurus on 2008-11-18
Which CD did you use to install Ubuntu on your machine?  What happens when you run this command from a prompt, after you have logged in with your username and password?

```
startx
```

---

### Post by mikewhatever on 2008-11-18
check out this link ->[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash). You may also need to edit the boot line in Grub's menu to include the splash option.

Example: kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=?????????????? ro quiet splash

Add the 'splash' option at the of the line if not there.

---

### Post by mashcaster on 2008-11-19
> **taurus said:**
> Which CD did you use to install Ubuntu on your machine?  What happens when you run this command from a prompt, after you have logged in with your username and password?

```
startx
```

I used the alternative 386 cd and chose to do a command line install.  if I type startx, I think it will start up the desktop environment have installed after finishing the command line install of ubuntu.

---

### Post by mashcaster on 2008-11-19
> **mikewhatever said:**
> check out this link ->[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash). You may also need to edit the boot line in Grub's menu to include the splash option.

Example: kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=?????????????? ro quiet splash

Add the 'splash' option at the of the line if not there.

Thanks, I will try this asap.

---

### Post by taurus on 2008-11-19
If you have already installed Gnome but the system only boots into a console, you can try to install gdm (if you have not already done so) and start it.

```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

### Post by mashcaster on 2008-11-19
> **taurus said:**
> If you have already installed Gnome but the system only boots into a console, you can try to install gdm (if you have not already done so) and start it.

```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

I don't have gnome or gdm installed, I have lxde installed.  When I boot up my computer, after all the text, it automatically loads the login manager (SLiM) which then goes into the desktop environment LXDE.  It's just that the boot process does not look nice yet.  I would prefer a progress bar.

---

