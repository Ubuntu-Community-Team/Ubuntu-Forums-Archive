---
title: "NVIDIA Driver 96.43.09 / gnome-display-properties"
date: 2008-11-23
forum: General Help
---

### Post by SocratesTNR on 2008-11-23
All over the forums there are people complaining about problems with the **NVIDIA Driver** and it's effects on various programs - typically, the menu text disappears - this has happen in **OO**, **Google Earth**, **Amarok** and others.

Also I've found since tweaking the *xorg.conf* to get the appropriate display settings in the NVIDIA driver control panel, I lose the frames and title bar of programs.

The *gnome-display-properties* isn't showing the same display properties as the NVIDIA...


It seems to be related to using the fancy  screen effects - switching to old, plain, no effects cures all ills.

I'm still a beginner, so I'm all out of ideas; I've spent most of the day trawling this and other forums but although I know a great deal more about how Ubuntu works, I'm no nearer a solution.

Can someone more experienced than me, try an pull all the different threads together?

Some of the threads and bug reports I've been looking at:


[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836)

[http://ubuntuforums.org/showthread.php?t=83973&highlight=screen+refresh+rate+Hz](http://ubuntuforums.org/showthread.php?t=83973&highlight=screen+refresh+rate+Hz)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076unchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bugs](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076unchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bugs)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/222516](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/222516)[/CODE]

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836)



RUNNING:

AMD 1900 512 MB

2.24.1 (Ubuntu 8.10)

2.6.27-7-generic kernel

NVIDIA GeForce2 MX/MX 400

NVIDIA Driver: 96.43.09

---

### Post by stinger30au on 2008-11-23
the driver is a beta, nvidia have not released a full stable release yet

nvidia knew about this months before 8.10 was released

it affects not only ubuntu but many other distros as well

check the versions availbe here

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by SocratesTNR on 2008-11-23
Thanks, I'll check out the link...

---

### Post by yoramdavid on 2008-11-26
Hello,

Perhaps my problem has the same source then.
When I mouse over the title bar of any windows to minimise or close buttons, it greys out.
Also some text are not displayed very readable.
And finally, I have a screen resolution of 1280X1024 (good) @ 50 Hz. Other options are 56 & 57 Hz, but those make the screen flickery, whereas @ 50 Hz it feels normal.
Perhaps these are different problems with different reasons?
According to the Hardware driver program, I am using the version 173.
How do I update the drivers from there?

Thank you for any help

---

### Post by lamps06 on 2008-12-07
Does anyone know if the issues happen with the stable driver version, 96.43.07?  How do I tell which version I am running and is it possible to back-rev to the older, stable version if I find I am running 96.43.09?  Thanks!

---

