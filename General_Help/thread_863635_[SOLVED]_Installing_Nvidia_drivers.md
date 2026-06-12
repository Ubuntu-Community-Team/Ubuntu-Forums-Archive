---
title: "[SOLVED] Installing Nvidia drivers"
date: 2008-07-18
forum: General Help
---

### Post by Ataris on 2008-07-18
I've installed .run files before, but in the readme for installing the nvidia drivers it mentions something about a linker, and backing up my xorg. I don't quite understand what this means.

Shouldn't it be a simple matter of running the sfx file and that's it?

---

### Post by phidia on 2008-07-18
What version of ubuntu are you using and what nvidia model gpu are you enabling?
In Hardy all you need to do is click on System>Admin>Hardware Drivers and enable your card. If it isn't listed there take a look at the how to [here]("http://ubuntuforums.org/showthread.php?t=797270&highlight=nvidia+hardy").

---

### Post by Ataris on 2008-07-18
I have 8.04, but when I tried KOTOR II on Wine it said I didn't have good enough drivers, so I downloaded the .run file from Nvidia.com.

I don't have Internet access on my Linux computer, either, so I have to download everything separately from a public computer.

My card's drivers are already enabled. I've gotten plenty of games to run fine.

---

### Post by Ataris on 2008-07-18
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

That's the link to where I downloaded it.

---

### Post by jonian_g on 2008-07-18
Install EnvyNG, it's in the repositories.

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System tools>EnvyNG and install the drivers from there.
It installs the latest drivers (173.14.09) with no effort, just by pressing an apply button.

Installing the driver from the nvidia website is a really bad idea.
Why it's a bad idea? Because every time you get a kernel update (three times till now after Hardy released), you have to reinstall the driver.

---

### Post by Ataris on 2008-07-29
Whoops, forgot about this thread. I just used EnvyNG, worked fine.

---

