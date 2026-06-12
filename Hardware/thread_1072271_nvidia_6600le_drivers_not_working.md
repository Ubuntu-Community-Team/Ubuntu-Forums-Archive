---
title: "nvidia 6600le drivers not working"
date: 2009-02-17
forum: Hardware
---

### Post by link0007 on 2009-02-17
Since I updated ubuntu, my graphics drivers have been acting very strange. On default, ubuntu loads in low graphics mode now, but when I go to recovery, and fix the x-server, it loads in 1024x768 like it should. But still GLX seems to be missing, as both games complain about it, and the nvidia config tool says there's no nvidia driver installed either.

I've tried removing all linux-restricted modules, and countless other steps nvidia wants me to take to install their drivers, but the result is the same as when fixing x-server from recovery.

I'm running ubuntu 8.04 on x64.. the driver I am trying to install is 180.something (29 or whatever).

Can anyone help me with this? If you need more details, or want me to execute some commands, just ask :)

---

### Post by tenmoi on 2009-02-17
Do a search like nvidia install problem on this forum first, i advise you.

---

### Post by link0007 on 2009-02-17
... Maybe a clue what topic you're refering to? I don't see any relating to my specific problem..

---

### Post by taurus on 2009-02-17
did you try to install the nvidia driver from terminal (by hand) or through System -> Administration -> Hardware Drivers?

---

### Post by link0007 on 2009-02-17
first the hardware driver menu, then the package manager, and then by hand... Tried every way I know or could find to get it working, but none of the normal ways worked. I've also checked and double checked xorg.conf for any oddities, and couldn't find any. I've also removed the nvidia module, all the other related modules, packages and files, and tried again, but none worked? I've done a lot of things! 

The odd part is that it *did* use to work very well, being able to run compiz without a sweat, and having no problems with Blender/phun/games or anything else using the graphics card extensively.

But now, even on 1024 resolution (when it's sorta-fixed I suppose, as the resolution is decent), every program relying on the graphics card won't start because of the missing modules/drivers/libraries.



edit: got it working again! Don't know what caused it, but following these steps to uninstall 180.29, and instead install 180.22, seemed to work:

1) stop display manager 

2) uninstall previously installed .run package

3) start the display manager, and use the synaptic package manager to remove all linux-restricted modules (and the likes). If done, stop the display manager again.

4) install the new nvidia driver via the .run package

5) start the display manager again.


No clue what was wrong, as the problem started by updating via the update manager.. Ah well, it's working again :D

Thanks for your help guys! I appreciate it :)

---

### Post by shields on 2009-04-04
> **link0007 said:**
> 
edit: got it working again! Don't know what caused it, but following these steps to uninstall 180.29, and instead install 180.22, seemed to work:

1) stop display manager 

2) uninstall previously installed .run package

3) start the display manager, and use the synaptic package manager to remove all linux-restricted modules (and the likes). If done, stop the display manager again.

4) install the new nvidia driver via the .run package

5) start the display manager again.


No clue what was wrong, as the problem started by updating via the update manager.. Ah well, it's working again :D

Thanks for your help guys! I appreciate it :)

I got up this morning and turned on the linux box only to find that once more, I am limited to 800X600 resolution. This has happened, without explanation, at least three times. I am using the nVidia Corporation NV44A [GeForce 6200] (rev a1).

Can you explain your procedure in greater detail? How do you stop the display manager? How do you uninstall the .run package? How do you restart the display manager? How do you remove restricted modules? How do you install the new nvidia driver via the .run package? 

Thanks.

---

### Post by link0007 on 2009-04-04
1) stop gdm:
/etc/init.d/gdm stop

2) uninstall current nvidia package:
sudo sh <name of your currently installed package>.run -uninstall

But I thinkt he synaptic package manager can do that too.. try it out I guess :)

3) start gdm: 
/etc/init.d/gdm start

uninstall linux-restricted modules via synaptic package manager

4) download the newest .run file from the nvidia site, and save it to your desktop or whatever. 

stop gdm again: 
/etc/init.d/gdm stop

in the command line, navigate to the desktop, and enter this code:
sudo sh <name of the package>.run



Hope that sorts things out for you! Feel free to ask if you have any questions ;)


oh: and back-up before you do this!! People forget that way too often ;)

---

### Post by shields on 2009-04-05
Oh -- this is too funny. My problem was that for some unknown reason I lost my higher resolution and could not get more than 800x600. I want 1024x768. So I started following your instructions. I opened a terminal and typed the first one to stop gdm.

Evidently that's not where I should have typed it, because it made the screen go blank and nothing more was there. So after five minutes, I pressed reset. When the machine came on, it came on in 1024x768. How in the world did that happen? :confused:

Now I am afraid to turn it off!  :)

I will try the rest of these steps the next time I lose 1024x768.

Thanks.

---

### Post by link0007 on 2009-04-05
Well when you stop gdm, you can only work via the commandline. this is nothing to be afraid of.

---

### Post by shields on 2009-04-05
> **link0007 said:**
> Well when you stop gdm, you can only work via the commandline. this is nothing to be afraid of.

I kind of expected something like the terminal command line, but there was no prompt there. There was just a blank screen. Typing commands (I typed "ls") revealed more nothing. Is that weird, or what?

---

### Post by link0007 on 2009-04-05
hm, that's odd.. maybe stopping gdm from inside gdm doesn't work? never tried, I always just boot into the commandline :p otherwise I think ctrl+alt+escape throws you into commmand line as well I think.

---

### Post by shields on 2009-04-05
OK -- when I try it, I will try from boot-up.

I seriously am not restarting this machine until I have to. Whew -- I missed 1024x768!

Thanks.

---

