---
title: "Make Ubuntu Primary + Upgrade Problems"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Beckenor on 2009-06-17
I have two problems with Ubuntu.

[LIST=1]
[*]I want to make Ubuntu the primary operating system on my PC. My new laptop came with Vista Home Premium pre-installed, and I want to keep it just to play games, but I want Ubuntu to have the bigger partition so i can use it for everything else.
[*]I installed Ubuntu off of the free CD from the website, and I am trying to upgrade a few major changes, such as too Firefox 3.0. But whenever I try to run the Update Manager, an Error messages opens saying I don't have enough space in my "/" Drive. I tried emptying my Recycle Bin and using 'sudo apt-get clean' in the command line, but there still isn't enough space.
[/LIST]
I am a newbie to Ubuntu, and except for these minor problems I really like it! Please help make my experience with Ubuntu more pleasing.

---

### Post by Idefix82 on 2009-06-17
Welcome! Can you open the terminal, type in
```
df
```
and post the output here? This will tell us what space you have available on which partition and we can take it from there. Before you do that, you might want to mount the Windows partition (e.g. by clicking on it in the file manager) so that that is included in the output of df and we can see how much space you can dispense with on the Windows partition.

---

### Post by raymondh on 2009-06-17
And for reference

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

as well as these for start-up options

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

and this for resizing

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Therion on 2009-06-17
> Here's how to install Vista and Linux (with Vista installed first). 
Step-by-step instructions that assume no knowledge of Linux. 

(Now updated for Ubuntu 9.04).

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Mark Phelps on 2009-06-17
If you installed Ubuntu "inside" Vista (using Wubi) and you accepted the default space allocation, you most probably don't have enough available space now to expand the installation.

The Wubi guide linked below, about 3/4 of the way down, shows how to rezise the virtual space:  

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by Beckenor on 2009-06-19
Therion, your hyperlink was very helpful, now I know what I did wrong. Unfortunately, now I must uninstall Ubuntu, so I may install it again the right way. Any advice?

---

### Post by Beckenor on 2009-06-25
I have solved my problem with Vista, and my computer is now running as smooth as ever. Thank you all for you're suggestions, especially Therion's. His was very helpful.

---

