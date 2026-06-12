---
title: "External monitor on notebook"
date: 2008-06-07
forum: Hardware
---

### Post by trm96 on 2008-06-07
I have a HP Pavilion ZE4800 notebook running Hardy, what I want to do is be able to connect up an external monitor to it via the VGA port on the back of it but I have no idea on how to get it to work. If i use the FN F5 keys it does not do anything I even rebooted to see if i could Hardy to detect the display but still nothing... I have tried searching Google but with no luck to figure out what to do...

Thanks in advance for any help...

---

### Post by Derf the on 2008-06-07
> **trm96 said:**
> I have a HP Pavilion ZE4800 notebook running Hardy, what I want to do is be able to connect up an external monitor to it via the VGA port on the back of it but I have no idea on how to get it to work. If i use the FN F5 keys it does not do anything I even rebooted to see if i could Hardy to detect the display but still nothing... I have tried searching Google but with no luck to figure out what to do...

Thanks in advance for any help...
Same question for me, just that mine is HP Compaq 8510w, but all the rest the same.

Thanks also...

---

### Post by Derf the on 2008-06-10
Hello again trm96, I read many related and amost related threads and think that the best info was this 'How to...'
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
But without having all the names and settings for my video card etc. I was not particlaily sucsessful in setting both screens.
What I could get was a simple "cloned" screen after the simple " sudo dpkg-reconfigure -phigh xserver-xorg " in a 'run' box ([alt]+f2); then restarted the computer.
I did do a " sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup " first, just in case something went wrong, but nothing did!

Hope things worked out OK for you too
WFT

---

### Post by trm96 on 2008-06-10
Actually this is exactly what i want to do. I have this crappy notebook set up on a coffee table and want to be able to use it with the lid closed kinda like a really crappy workstation, I cant do much else with it since I get about 10Mins of battery out of it.

When I put in the above command (into a terminal window) I got the following: 
```
brett@ubuntu-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080610104450
```

BTW I *did* backup the config file first as I always do.

---

