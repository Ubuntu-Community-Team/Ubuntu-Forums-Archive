---
title: "Installing NVIDIA Driver on Ubuntu 8.04"
date: 2008-10-20
forum: General Help
---

### Post by weirddan455 on 2008-10-20
I want the latest driver so I'm downloading it off the nvidia website rather than using the one that comes with Ubuntu.  I hit Ctrl+Alt+F2 to get to the console, then /etc/init.d/gdm stop to close down GNOME then installed the driver and ran startx to load GNOME up again.  The NVIDIA driver is up by the looks of it.

The trouble starts when I reboot the screen flashes and Ubuntu wants me to reconfigure my driver.  It won't let me do anything until I boot into recovery and click fix x.

It just doesn't make any sense when I run startx it works fine... maybe something weird in the boot up scripts?

---

### Post by weirddan455 on 2008-10-21
I found a workaround... I did sudo update-rc.d -f gdm remove to keep x from starting up and then I just startx manually every time.  It's kind of annoying to do that though.

Has anyone else had success with these drivers?

---

### Post by weirddan455 on 2008-10-21
Nope it's something about rebooting that's messing me up.  Everytime I reboot x can't start up.  It gives an error message about a mismatching kernel and the driver.  I'm not sure where the log file is or I'd post that.

---

### Post by shawnrgr on 2008-10-21
Im the only user on this box. so i don't even have GDM installed, or anyother display manger for that matter.

My system auto logs in from tty1 and launches x

here is a quick howto:

```
sudo apt-get install rungetty
sudo nano /etc/event.d/tty1
```

comment out the last line and replace it with the one below (replace 'shawn' with your username):
**exec /sbin/rungetty --autologin [COLOR="Red"]shawn[/COLOR] tty1**

make sure to only comment that out, don't delete it, that way you can change it from a terminal if something goes wrong.

watch your double quotes here if you copy and paste...
```
echo "pgrep X &>/dev/null; [ $? = 1 ] && startx" >> ~/.bashrc
```

EDIT: you added that last dohicky before i posted this lol, not sure if i can help you with that

---

### Post by TeXtonyx on 2008-10-21
There's a common complaint that after downloading the Nvidia driver
stopping X and building the driver (build-essentials)that installing
the driver doesn't stick, you get that low-res message next time 
you boot in Ubuntu. I found that the xorg.conf is useful which is
created from running nvidia-settings. But I found only the driver
when installed by envyng persisted (and used the good xorg.conf).


" Code: sudo apt-get install envyng-gtk

after it installs, find it in applications > system tools > envyng. 
open it and follow the prompts to install the nvidia driver. "

If you type , nvidia howto , in the search box at the top of the
forum webpage you will gets lots of hits from people who have
written howtos on installing different Nvidia drivers/cards.
In some cases they purge the old drivers.

---

### Post by weirddan455 on 2008-10-21
I figured out what's causing the bug.  Somewhere in the start-up scripts it's trying to load the kernel modules "nvidia".  This is my best workaround so far until I figure out where to edit the start-up scripts.

Run this one time.  It changes the scripts to not start the GUI up at start-up.
```
sudo update-rc.d -f gdm remove
```

If you need to go back to the way it was run this
```
sudo update-rc.d gdm defaults
```

Then when you get your console login run this to startx

```
sudo rmmod nvidia
startx
```

That "rmmod nvidia" removes the somehow messed up version of the module the start-up scripts try to load.  When you "startx" it reloads the module and works fine for me.

---

