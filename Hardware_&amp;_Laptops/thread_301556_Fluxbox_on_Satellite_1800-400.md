---
title: "Fluxbox on Satellite 1800-400"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by HydroDiOxide on 2006-11-17
Hi,

Trying to revive my Toshiba Satellite using Ubuntu. Ubuntu 6.10 with Gnome was running really slow, so I did a command line install and tried to get the thing running using fluxbox. I used the Howto located [here](https://help.ubuntu.com/community/Installation/LowMemorySystems).
However, when I type startx at the commandline my screen blanks out and I can't see anything anymore. Also, when rebooting, the screen turns black and I can't see nothing. Anyone any ideas on how to get fluxbox running on this thing?

---

### Post by christhemonkey on 2006-11-17
After typing "startx", press, <Ctrl>+<Alt>+<F1> to go back to the command line, and note any errors, then post them up on here.

---

### Post by HydroDiOxide on 2006-11-17
I'm doing a reinstall right now; 6.10 'command line'. Afterwards I want to install the ubuntu-lite-desktop using [this](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=laptop) HOWTO and then, when I get into a working desktop environment (hopefully), install fluxbox to speed things up even more. Does that sound like a good idea?

---

### Post by HydroDiOxide on 2006-11-17
Can't get things to run. Did a reinstall again and tried to install fluxbox according to the above mentioned HOWTO. startx turns the screen blank again and ctrl+alt+f1 won't get me anything. Any ideas?

by the way: is the 'command line'install from the alternate cd's the same thing as the server install from the desktop installation cd's?

---

### Post by kerry_s on 2006-11-17
What's the specs on your machine? When you say you tried gnome, did that get to the desktop? Did you follow all the instructions?

#1. server install

#2. login & sudo su  <-makes you root

#3. nano /etc/apt/sources.list   <& (#)comment out the cdrom and uncomment all the repos(they start with deb) & ctrl + x & y & enter to save.

#4. apt-get update

#5. apt-get install x-window-system-core gdm xterm fluxbox synaptic emelfm leafpad dillo firefox gaim

#6. type> reboot

That's it that will give you a fully working desktop.
gdm = login manager
xterm = terminal
fluxbox = the Wm or desktop gui
synaptic = the package manager, to install or remove packages
emelfm = filemanager, very light & simple 
leafpad = text editor
dillo = small fast web browser
firefox = bigger slower full feature web browser
gaim = IM & mail notifcation

---

### Post by HydroDiOxide on 2006-11-20
I'm booting from the alternate install cd here. I'm presented with a graphical selection menu:

#install in text mode

#install in OEM mode

#install a command-line system

#etc

So, where do I type server install? From the F6 menu maybe?

---

### Post by kerry_s on 2006-11-20
It's the command-line one. They have changed the wording but were use to calling it a server or base install. So start with the command-line system install and go from there. Good luck.

---

### Post by HydroDiOxide on 2006-11-20
6.10 Edgy Eft will boot/install normally and give me a working desktop.

shouldn't I configure the xserver with something like this:

sudo dpkg-reconfigure xserver-xorg (as mentioned [here](http://www.ubuntuforums.org/showthread.php?t=98233))?

By the way, can I replace fluxbox with xfce to get an xfce desktop?

Specs on the machine:
Toshiba Satellite 1800-400 
Celeron mobile 800mgh
256 mb RAM
15 gig hdd
8mb video ram on an Trident Cyberblade

---

### Post by tturrisi on 2006-11-20
[http://fluxbuntu.org/](http://fluxbuntu.org/)
[http://wiki.fluxbuntu.org/index.php?title=Main_Page](http://wiki.fluxbuntu.org/index.php?title=Main_Page)

---

### Post by kerry_s on 2006-11-20
> **HydroDiOxide said:**
> 6.10 Edgy Eft will boot/install normally and give me a working desktop.

shouldn't I configure the xserver with something like this:

sudo dpkg-reconfigure xserver-xorg (as mentioned [here](http://www.ubuntuforums.org/showthread.php?t=98233))?

By the way, can I replace fluxbox with xfce to get an xfce desktop?

Specs on the machine:
Toshiba Satellite 1800-400 
Celeron mobile 800mgh
256 mb RAM
15 gig hdd
8mb video ram on an Trident Cyberblade

No it will ask what display size you want, just use the up/down arrows and space bar to select your screen size's and press tab to get to ok when done.

Yes you can select xfce4 instead of fluxbox, it will be a little different than the fluxbox instructions i gave. on the install part change to this->

#5. apt-get install x-window-system-core gdm xfce4 leafpad xfce4-terminal synaptic dillo firefox gaim xfce4-appfinder

That will give you a bare bones xfce4 setup, it will just have->
thunar = file manager
leafpad = editor
xfce4-terminal = terminal
dillo = small fast web browser
firefox = bigger slower full feature web browser
gaim = IM & mail notifcation

Now for a minimal xfce4 you have to build the panel yourself, you will just get a empty panel with a empty launcher in the top left hand corner, but you will have a complete menu on the mouse right click. Just right click & look for xfce4-appfinder, will use that to start your panel, now right click the panel & select properties. Now just drag a application to the launcher window & you have your first launcher. Xfce4 can do several launchers on a single icon or just 1, it's up to you to build it. Choose add item to put a tasklist(shows what apps using) & so on.

---

### Post by HydroDiOxide on 2006-11-21
@kerry_s

Thanks for all the good replies. I've found out that a basic xfce install on an ubuntu commandline install is much faster than a xubuntu installation (full). I was wondering if you had any clue how this could be: what is slowing xubuntu down?

---

### Post by kerry_s on 2006-11-21
I don't know, it's just alot bigger. I only have the full xubuntu(my pure setup) & fluxbox + thunar(my everyday use). On my fluxbox+thunar setup you can really feel a difference in speed. Here's a pic of my fluxbox & thunar install.

---

### Post by Nimo on 2006-11-23
> **kerry_s said:**
> I don't know, it's just alot bigger. I only have the full xubuntu(my pure setup) & fluxbox + thunar(my everyday use). On my fluxbox+thunar setup you can really feel a difference in speed. Here's a pic of my fluxbox & thunar install.

Ohh..looks nice!

Could you please post your .conkrc-settings?

What panel are you using at the bottom?

---

### Post by kerry_s on 2006-11-23
> **Nimo said:**
> Ohh..looks nice!

Could you please post your .conkrc-settings?

What panel are you using at the bottom?

Sure conkyrc attached.

I'm using the xfce4-panel, it get's installed with thunar so i put it to use.

---

