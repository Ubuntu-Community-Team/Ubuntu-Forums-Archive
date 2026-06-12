---
title: "No GUI boot login after manual nVidia driver install"
date: 2008-10-11
forum: General Help
---

### Post by Killer Cop on 2008-10-11
Hi.

I'm beginning to be quite good with Ubuntu, but I can't fix this. And I can't find anything on Google or this forum which can solve the problem.

I was thinking about updating my nVidia driver for my 8600GTS graphics card, because I wanted the graphics to become more smoother and get more performance.

I went to nVidia's driver download site and downloaded the latest nVidia driver tar.gz I could get. I ran the code and it said that I had to shut down xserver to continue the installation, and terminated installation if I didn't. I found some code that did that, and I installed the package from the command line interface. The installation did perfectly and it installed nVidia xserver too I think.

But then the problem arise, GUI won't start up again! I tried several codes I found, "startx", "exec gnome-session", "exec gdm" and running fail-safe restore thingy from GRUB menu and many other things, but no worky.

What do I do?

---

### Post by Ryadt on 2008-10-11
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Killer Cop on 2008-10-12
> **Ryadt said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```

Doesn't help. I've tried running it everal times and no help. :)

---

### Post by engineer on 2008-10-12
let me guess:

are you running the intrepid ibex beta?

i'm having the same problem, but also don't know, how to fix it.
gdm uses 100% cpu time

---

### Post by TeXtonyx on 2008-10-12
I read a tutorial on this and I've seen a few floating around. The recommended way
to stop Xserver was,  sudo /etc/init.d/gdm stop , and to start,  sudo /etc/init.d/gdm start
I've also seen,  sudo mv /etc/rc2.d/S30gdm  /etc/rc2.d/D30gdm
Then reboot and this usually takes you to the non-gui login. When done with the
Nvidia driver and writing xorg.conf,  sudo mv /etc/rc2.d/D30gdm  /etc/rc2.d/S30gdm
and reboot. They said ctrl-alt-backspace will restart the Xserver but it didn't work
for me. Finally I've seen,  sudo init 1 , to go to non-gui login and sudo telinit 1 and
sudo init 3 to restart the Xserver which worked for me. 

[http://www.yaroman.com/2007/08/14/howto-install-nvidia-8600gt/](http://www.yaroman.com/2007/08/14/howto-install-nvidia-8600gt/)  who says

4. Run the installation script/driver

Press CTRL+ALT+F6 and log into your ubuntu account

and paste the following:
sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NV (PRESS TAB TO GET THE REST)

and go through the installation. Once complete:

sudo /etc/init.d/gdm start
CTR+ALT+F7 to get back to GUI

---

