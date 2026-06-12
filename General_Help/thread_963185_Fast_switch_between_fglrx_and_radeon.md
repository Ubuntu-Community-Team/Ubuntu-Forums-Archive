---
title: "Fast switch between fglrx and radeon"
date: 2008-10-30
forum: General Help
---

### Post by zeigfried on 2008-10-30
Hey, 

I currently play 3d games better with fglrx driver, still I need EXA acceleration with some tools, that`s only available with radeon driver for my video card... Besides 2d performance also seems better with radeon driver.

Every time I need to switch between fglrx and radeon I purge the fglrx driver (because radeon driver don`t load as long as fglrx is installed) and copy a xorg.conf file to the /etc/X11... (lame)
To switch back to fglrx I reinstall it from the deb package and copy another xorg.conf file to /etc/X11. (even lamer)

What I want is a fast way to switch between the two drivers... 
Is there any way to write a script able to switch between the drivers without using purge & dkpg -i (or even using it if there is no better solution)?
How about two entries in the grub menu (one for fglrx, other for radeon)?

Thanks in advance,

---

### Post by zeigfried on 2008-10-30
Anyone got a solution / suggestion?

---

### Post by neunon on 2009-01-16
Apologies for the gravedig, but I need this as well. Any suggestions?

---

### Post by jpeter55 on 2009-04-08
I could use this too...

---

### Post by craigster0 on 2009-04-14
well, i haven't tried this myself, but it's probably not that hard to write a script to rename the files.

i would try have to xorg.conf files, let's call them:

/etc/X11/xorg.conf.radeon
/etc/X11/xorg.conf.fglrx

with the obvious contents.  we'll use symlinks to switch between them.  a script that contained:

mv /usr/lib/xorg/modules/drivers//fglrx_drv.so \
          /usr/lib/xorg/modules/drivers//fglrx_drv.so-sav
rm /etc/X11/xorg.conf
ln -s xorg.conf.radeon /etc/X11/xorg.conf

would be enough to setup your radeon config.  to switch to fglrx you could have:

mv /usr/lib/xorg/modules/drivers//fglrx_drv.so-sav \
          /usr/lib/xorg/modules/drivers//fglrx_drv.so
rm /etc/X11/xorg.conf
ln -s xorg.conf.fglrx /etc/X11/xorg.conf

after running the appropriate script, you can logout to restart the X server (i think), or cause it to restart by pressing Ctrl+Alt+Backspace (at the same time).  note that any open windows will close when you do this.

---

