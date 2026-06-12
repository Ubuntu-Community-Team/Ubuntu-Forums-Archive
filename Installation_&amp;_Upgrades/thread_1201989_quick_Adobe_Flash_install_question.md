---
title: "quick Adobe Flash install question"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by arash1 on 2009-07-01
New to Ubuntu, so please bare with me.

Was having problems with my Flash 10 running slowly in Firefox, so am trying flash 9.  Am following this guide step by step:

[http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

I am stuck at this point.  The install is asking:

[B]Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla):[/B]

The path is "/usr/lib/mozilla" and when I type that in it says 

**WARNING: Please enter a valid install path.**

When I type in something random like "a" I get this error:

**WARNING: /home/myusername/install_flash_player_9_linux/a is not a directory.**

Am I doing something wrong?  I have verified that I have a /usr/lib/mozilla folder.

Thanks

---

### Post by lovinglinux on 2009-07-01
That tutorial is for an old release of Ubuntu and I doubt flash 9 will help to solve your problem.

BTW, the path is correct.

I presume you have the latest Ubuntu release right? It is Ubuntu 9.04 Jaunty Jackalope right?

I also presume you sent me a PM because you have already found my tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Have you tried the optimizations and solutions provided there?

What is your graphics card model?

---

### Post by arash1 on 2009-07-01
Correct as to the Ubuntu versions.

I have not read through your guide, but will now.  I would still like an answer, if there is one, to the original question even if installing Flash 9 won't work.  I'm just trying to get used to Linux, and don't understand the error I am getting when I type in what seems to be a correct path.

The video card is the Intel GMA 950, I think.  I have an Eee 900a laptop.  I can't find Ubuntu friendly drivers for this card, but I imagine they are out there somewhere.

Any ideas on the Flash install?

---

### Post by lovinglinux on 2009-07-01
> **arash1 said:**
> Correct as to the Ubuntu versions.

I have not read through your guide, but will now.  I would still like an answer, if there is one, to the original question even if installing Flash 9 won't work.  I'm just trying to get used to Linux, and don't understand the error I am getting when I type in what seems to be a correct path.

The video card is the Intel GMA 950, I think.  I have an Eee 900a laptop.  I can't find Ubuntu friendly drivers for this card, but I imagine they are out there somewhere.

Any ideas on the Flash install?

Stick with Flash 10 and follow the instructions below to improve your graphics card performance. Flash really sucks on Jaunty. I have my share of problems with it, but in your case I believe the bigger problem is the graphics card.

**Performance regressions on Intel graphics cards**
*From: [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)*

> Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (252094). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running the following command on a terminal

```
sudo gedit /etc/X11/xorg.conf
```

and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.

It should look like  this:

```
Section "Device"
	Identifier     "Configured Video Device"
	Driver         "Intel" *(or something else)*
	Option	  "MigrationHeuristic" "greedy"
EndSection

```

> Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running the following command in the terminal.

```
sudo gedit /etc/X11/xorg.conf
```

and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

It should look like this:

```
Section "Device"
	Identifier     "Configured Video Device"
	Driver         "Intel" *(or something else)*
	Option        "AccelMethod" "UXA"
EndSection

```


> **[color=#CC0000]Warning:[/color]** In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use the command below to revert the UXA option:

```
sudo nano /etc/X11/xorg.conf
``` 


[color=#CC0000]**It's a good idea to try the command above before doing any changes, so if you need to revert the changes, you know how to do it.**[/color]





If none of the above helps, some users reported success with [using an older driver version](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4). 

You could also try [this tutorial](http://ubuntuforums.org/showthread.php?t=1130582), but is not recommended for beginners.

---

### Post by arash1 on 2009-07-02
when I edit my xorg.conf file, my device section looks like this:

> 
Section "Device"
        Identifier     "Configured Video Device"
EndSection


It doesn't have anything about drivers in there, which I am assuming is a problem.  

I added the **Option	  "MigrationHeuristic" "greedy"** line, and no improvement in flash which is probably no surprise.

---

