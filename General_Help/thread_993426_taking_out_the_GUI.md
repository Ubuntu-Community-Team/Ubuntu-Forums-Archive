---
title: "taking out the GUI"
date: 2008-11-25
forum: General Help
---

### Post by AnLGP on 2008-11-25
Hello,

I want to know how much of the GUI can I strip down from a fresh install of  ubuntu?

I remember you can take the bootsplash out but not how.  I also want to know if getting rid of GNOME is possible. I'll probably end up installing a WM (awesome).  How do I get it so I type "startx" and awesome loads?

Thanks
Steve

---

### Post by Locutus_of_Borg on 2008-11-25
why not just use the server edition of ubuntu?

apt-get remove ubuntu-desktop might work though

---

### Post by AnLGP on 2008-11-25
because it seems every time I install the mini distro I can't figure the sound out.  and it's largely important to me.

---

### Post by loomsen on 2008-11-25
Check out [www.instalinux.com](www.instalinux.com)

Configure it to your liking, you'll get a around 10MB sized iso file, with a very very minimal gnome desktop.

There was barely any application installed in my system. Perfect if you keep wasting time removing apps/pkges you don't want. 

You gotta be connected through LAN as it's a netinstallation. You'll have a basic installer too, so no mouse, 8bit visuals etc. As it should be imho :) Just to tell you.


2) If you don't want to chose this, and don't want to start gnome as your default Display Manager, you may edit
**/etc/X11/default-display-manager**
which should be set to /usr/sbin/gdm atm.

If you have xfce installed, for instance, change it to /usr/sbin/xdm
If you specify a display manager not available on your system, you'll get a shell login, so no need to worry.

You may as well set up your own session, but think about what it needs, such as xsetroot to set the background, a notification area, a panel, a menu aware appli and so on. So it's prlly easier to chose xdm and configure it.


I'd recommend instalinux.com tho.

---

### Post by AnLGP on 2008-11-25
Thanks.

I have ambitions of one day making my own linux distro but I simply don't think I know enough about it yet to achieve that goal.  I've been using Linux for roughly a year and a few months.  I think I've heard of instalinux.


I just tried to do an arch setup today and it was an epic FAIL.  The word "GRUB" kept going and going and going..

Thanks for the shell login.  I was lookin' for that :)

---

### Post by hictio on 2008-11-26
You can also get rid (that is, turning it off) of the graphical login, by issuing this on a terminal:
```

update-rc.d -f gdm remove

```

If you want to re-enable it later, type this:
```

update-rc.d -f gdm defaults

```

If you are going to have a CLI only system, you might find this interesting, [Ubuntu high resolution console](http://oesediez.blogspot.com/2008/09/ubuntu-high-resolution-console.html)

---

