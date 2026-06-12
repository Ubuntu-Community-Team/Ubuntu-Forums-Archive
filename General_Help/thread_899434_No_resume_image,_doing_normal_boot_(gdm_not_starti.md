---
title: "No resume image, doing normal boot (gdm not starting)"
date: 2008-08-24
forum: General Help
---

### Post by Werm on 2008-08-24
I recently needed to stop down X to install a driver... I shutdown GDM from a terminal.

NOW everytime I boot my computer I get the error:

kinit: name_to_dev_t (/dev/disk/by-uuid/ a bunch of letters and numbers) = s db6 (8,22)

Trying to resume blah blah blah

No resume image, doing normal boot

SOO I've been starting gdm manually with

cd /etc/init.d/
sudo gdm start



Does anyone know how to fix this to run gdm automatically on boot? Thanks for any help! :)

---

### Post by aysiu on 2008-08-24
So after it says it's *doing* a *normal boot* it boots to the command line instead of to the graphical login screen?

---

### Post by koenn on 2008-08-24
"No resume image, doing normal boot" is, IIRC, a message that is displayed at just about every boot. It's normal : (if I'm not mistaking), it's the OS checking whether its "just booting" or whether it has to restore a previous state (like, resume from hibernate, or so)

Also, gnome / gdm is to be considered just an application running on top of the OS, so there is nor really a discrepancy between "doing normal boot" and gdmfailing to start. It just means an application is not starting. period.


if you can start gdm manually the way you describe, the essence of your problem is that it no longer starts automatically. 

diagnostics
- check that /etc/rc2.d/S30gdm exists
- check that you're booting to runlevel 2 (and not to maintenance mode or anything else Gui-less)
```
me@nix:~$ runlevel
N 2
```

---

### Post by Werm on 2008-08-26
Yea, that's the problem it's not starting :-/

Without gdm, runlevel is 2 (I just checked)

/etc/rc2.d/S30gdm exists but "The Link "S30gdm" is Broken"

This link can't be used, because its target "../init.d/gdm" doesn't exists

whereis gdm

gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm /usr/share/man/man1/gdm.1.gz /usr/share/man/man8/gdm.8.gz

I created a new gdm file (found code on the net)t, restarted and same problem

opened both /etc/rc2.d/S30gdm and /etc/init.d/gdm and both work (not broken)

The driver I installed was a nvidia one.

---

### Post by Sycron on 2008-08-26
create a symlink:```
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S30gdm
```

---

### Post by Werm on 2008-08-26
> **Sycron said:**
> create a symlink:```
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S30gdm
```

ln: creating symbolic link `/etc/rc2.d/S30gdm': File exists

Boot up still doesn't start gdm

---

### Post by Sycron on 2008-08-26
type
```
sudo rm /etc/rc2.d/S30gdm
```
and then
```
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S30gdm
```

---

### Post by koenn on 2008-08-26
> **Werm said:**
> 
/etc/rc2.d/S30gdm exists but "The Link "S30gdm" is Broken"
This link can't be used, because its target "../init.d/gdm" doesn't exists

This completely contradicts what you said earlier :
> **Werm said:**
> I've been starting gdm manually with

cd /etc/init.d/
sudo gdm start


I get the feeling we're not getting the full story ...


Anyway, 
you need a valid etc/init.d/gdm, and it has to be executable
you need a /etc/rc2.d/S30gdm that points to /etc/rc2.d/S30gdm (or ../init.d/gdm)

I have no idea how you managed to break this, but you can either try Sycron's instructions to re-create the symlinks to the etc/init.d/gdm you created (did you set it executable ?), 
or reinstall gdm
```
sudo apt-get --reinstall install gdm
```

---

### Post by koenn on 2008-08-26
> **koenn said:**
> This completely contradicts what you said earlier :

hm, let me correct that, 
if /etc/init.d/gdm doesn't exist, your "sudo gdm start" would execute /usr/sbin/gdm , so what you say does make sense.
Sorry. 

Anyway, ... (see previous post)

---

