---
title: "whereis inittab"
date: 2008-11-28
forum: General Help
---

### Post by hirohitosan on 2008-11-28
Hello again!
How can I start my Ub in text mode and switch to text login (runlevel 3).
There is no inittab or something like this?

thanks

---

### Post by sdennie on 2008-11-28
An easy way to do this is to go to System->Administration->Services and turn off gdm (Note: This will also immediately kill your X session).  If you also want a pure text-based boot (no splash screen), edit /boot/grub/menu.lst and change:

```

# defoptions=quiet splash

```

To

```

# defoptions=quiet

```

And then run:

```

sudo update-grub

```

---

### Post by oldos2er on 2008-11-28
> **hirohitosan said:**
> Hello again!
How can I start my Ub in text mode and switch to text login (runlevel 3).
There is no inittab or something like this?
thanks

 Nope, there's no inittab. Instead, there's Upstart: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by x1a4 on 2008-11-28
> **oldos2er said:**
> Nope, there's no inittab. Instead, there's Upstart: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Although *buntu will honour an inittab file if you create one.

---

### Post by meastwood on 2008-11-28
doesn't use inittab any more:

either change the runlevel you boot into
in /boot/grub/menu.list add the boot param  single  though this is in effect recovery mode.

if you do not want a desktop and still use runlevel 2 then disable gdm(gnome, I guess kdm for kde)
# update-rc.d -f gdm remove

you can then bring up desktop from the cmdline with startx

To re-enable gdm
# update-rc.d gdm defaults
or (for the same result)
# update-rc-d gdm start 20 2345 stop 01 016 .
(you need the last .  when you explicitly state runlevels and script S|K numbers)

---

### Post by hirohitosan on 2008-11-30
> **vor said:**
> An easy way to do this is to go to System->Administration->Services and turn off gdm (Note: This will also immediately kill your X session).  If you also want a pure text-based boot (no splash screen), edit /boot/grub/menu.lst and change:

```

# defoptions=quiet splash

```

To

```

# defoptions=quiet

```


I don't have 
# defoptions=quiet splash in /boot/grub/menu.lst instead I have:
```

kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4e93fc51-495b-4cff-bfc7-8a17191aaa4e ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
 
```

is there where I have to delete splash?

thanks

---

### Post by sdennie on 2008-11-30
It's very strange you don't have the "# defoptions" in /boot/grub/menu.lst unless you hand edited the file in the past.  Regardless, removing the "splash" from what you've posted will work unless you do actually have the "# defoptions".  In which case it will only work until the next kernel install.

---

### Post by x1a4 on 2008-11-30
> **hirohitosan said:**
> I don't have 
# defoptions=quiet splash in /boot/grub/menu.lst


You should have it.  It should be among all the comments well above the kernel entries, below the text 

### BEGIN AUTOMAGIC KERNELS LIST

When editing menu.lst be sure not to uncomment all the commented entries as they're needed for a variety of scripts, including update-grub, to be able to recognize the various elements in the file.  If you want to make your own comments use more than one # sign.

---

### Post by x1a4 on 2008-11-30
> **meastwood said:**
> doesn't use inittab any more:
Upstart is familiar with /etc/inittab and if someone wants to use one they're welcome to create one.

---

### Post by meastwood on 2008-11-30
> **x1a4 said:**
> Upstart is familiar with /etc/inittab and if someone wants to use one they're welcome to create one.

that's true

---

