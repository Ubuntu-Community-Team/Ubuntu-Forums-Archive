---
title: "Big Problem"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by silentabe939 on 2008-03-06
So when i turn on my computer it starts booting, runs through th boot and stops displaying the line "Running Local boot scritps (/etc/rc.local)" and it just freezes there. Any ideas?

---

### Post by benbelly on 2008-03-06
Is this a fresh install, or has it been working for a while?  Did you just update some packages?  Was the kernel included?  Do you have the splash screen enabled (that locks up my system)?  Is it a laptop or desktop?  What kind of video card?  Any restricted drivers?

---

### Post by silentabe939 on 2008-03-07
Its a Hp Pavillion dv6000. This problem started when i tried to hook my laptop up to a monitor, i set ubuntu to use a monitor as my main. i logged off and then everything shut down. is there some way i could do a reinstall with a live cd and leave the home folder alone?

---

### Post by benbelly on 2008-03-07
I did that once.  Here is how I fixed it - it isn't pleasant.  Maybe someone else has a better suggestion.  This is all command line stuff, so I've tried to spell it out carefully.  Apologies if it's too complicated or too simple.

  Boot into the console, or recovery console, or whatever it's called.  The boot option that takes you to the command line.  Log in, then type:
```

~$ cd /etc/X11
/etc/X11$ ls -l xorg.conf*

```

  You will see a list of files something like this:
```

/etc/X11$ ls -l xorg.conf*
-rw-r--r-- 1 root root 3933 2007-12-23 13:17 xorg.conf
-rw-r--r-- 1 root root 2462 2007-11-15 19:41 xorg.conf.1
-rw-r--r-- 1 root root 3932 2007-11-16 20:08 xorg.conf.2

```

What you see are the backups of your xorg.config file.  You can restore a working backup by finding one dated with a  time you know your system was working.  For this case, let's say xorg.conf.1.  What you want to do is 1) make a backup of the current configuration - just in case we make things worse and want to get back here, 2) make the old xorg.conf.1 (or whatever number you choose) be your current xorg.conf.

You'll have to type your password when you use the sudo command.

```

/etc/X11$ sudo cp xorg.conf xorg.conf.broken
/etc/X11$ sudo cp xorg.conf.1 xorg.conf

```

If this change doesn't work, and you want to undo it, you just need to come back to the console and type
```

~$ cd /etc/X11
/etc/X11$ sudo cp xorg.conf.broken xorg.conf

```

But for now, try to reboot and see if your system can come up like it used to.
```
sudo reboot now
```

Hope that did it.  If so, and you still want to get an external monitor going, poke around the forums for xrandr.  After I did all this, that's what I found to get my external monitor going on my Latitude D630 laptop.

Post a reply if that didn't do the trick.  Maybe someone who knows more than I will have a better idea.

-Ben

---

