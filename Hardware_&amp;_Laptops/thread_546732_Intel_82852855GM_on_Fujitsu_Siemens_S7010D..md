---
title: "Intel 82852/855GM on Fujitsu Siemens S7010D."
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by ifconfig on 2007-09-09
Hi.

I have read every guide and tried 915resolution but nothing helps me.

In Xfce when I'm opening a menu the menu first contains lines i various colors and after 0.5 s it looks alright. It's the same problem when I run an application that needs password, the whole screen gets full of these lines and the it brings up the password dialog.

And when I had installed the system I could watch movies in vlc, but now the video either gets blue or black.

I'm running Xubuntu Feisty on a Fujitsu Siemens S7010D.

xorg.conf says:
```
        
Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver          "i810"
BusID           "PCI:0:2:0"
Option          "DRI"

```

It's an Intel Extreme card.

And I'm running it in 1024x768, 16 bit color depth. I have tried 24 bit, no difference.

Any ideas?

/Magnus

---

### Post by El Rogueo on 2007-09-09
> **ifconfig said:**
> 
xorg.conf says:
```
        
Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver          "i810"
BusID           "PCI:0:2:0"
Option          "DRI"

```


The lines are from the greying of the screen when the password box comes up, which in turn happen because you're having resolution problems.

Are you SURE you have the right drivers for your card? [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html) says you should be using the 855GM drivers, not the i810.

Threads with similar/same problem as you I've posted in today~

[http://ubuntuforums.org/showthread.php?t=546082](http://ubuntuforums.org/showthread.php?t=546082)
[http://ubuntuforums.org/showthread.php?t=546838](http://ubuntuforums.org/showthread.php?t=546838)

try a forum search, someone must have found a working solution by now if the problem is so common.

---

### Post by ifconfig on 2007-09-10
> **El Rogueo said:**
> The lines are from the greying of the screen when the password box comes up, which in turn happen because you're having resolution problems.

Are you SURE you have the right drivers for your card? [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html) says you should be using the 855GM drivers, not the i810.

Threads with similar/same problem as you I've posted in today~

[http://ubuntuforums.org/showthread.php?t=546082](http://ubuntuforums.org/showthread.php?t=546082)
[http://ubuntuforums.org/showthread.php?t=546838](http://ubuntuforums.org/showthread.php?t=546838)

try a forum search, someone must have found a working solution by now if the problem is so common.

Okey. I'll see if I can solve it. The resolution is not my problem, because I have non-widescreen.
I noticed yesterday that when I run a fullscreen game X crashes and brings gdm.

/Magnus

---

### Post by El Rogueo on 2007-09-10
Sorry for the confusion. By "resolution problem", I meant the fact that you're looking at things in 16 bit color, and I assumed that your graphics are capable of more.

> **ifconfig said:**
> 
I noticed yesterday that when I run a fullscreen game X crashes and brings gdm.

Can you manually restart X via the command? 

What do you mean by bringing gdm? Can you run the game within that, or is gdm not a GUI?

Also, does the game play fine in windowed mode?

---

### Post by ifconfig on 2007-09-10
> **El Rogueo said:**
> Sorry for the confusion. By "resolution problem", I meant the fact that you're looking at things in 16 bit color, and I assumed that your graphics are capable of more.



Can you manually restart X via the command? 

What do you mean by bringing gdm? Can you run the game within that, or is gdm not a GUI?

Also, does the game play fine in windowed mode?

I ran X in 24 bit earlier, changed to 16 bit to see if it helped me.
The reason I mentioned "resolution" were to not confuse you because I have seen many with this chip having problem with their resolution.

This is what happends when running a fullscreen game. The screen turns black, I see output from the boot in the console and gdm starts and I can log in again.

Games runs perfect in windowed mode.

/Magnus

---

### Post by El Rogueo on 2007-09-10
> **ifconfig said:**
> 
This is what happends when running a fullscreen game. The screen turns black, I see output from the boot in the console and gdm starts and I can log in again.

Games runs perfect in windowed mode.


I must apologize, but I have to be sure: are you sure your graphics (integrated or card) is capable of rendering the game in full screen?

I still feel that the source of the problem is driver-related, but I will begin seeking additional solutions

---

### Post by ifconfig on 2007-09-11
> **El Rogueo said:**
> I must apologize, but I have to be sure: are you sure your graphics (integrated or card) is capable of rendering the game in full screen?

I still feel that the source of the problem is driver-related, but I will begin seeking additional solutions

Yes, it should be. I have used it with other versions/dists earlier.

/Magnus

---

