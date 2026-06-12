---
title: "XP wont boot after ubuntu installed"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by flairtorc on 2009-09-19
i have spent a lot of time looking at all the solutions for this posted by everyone....and none of them have ever worked..i'm 6 hours into this and i just want it to work...my issue is that when i turn on my comp, go down and hit Windows XP Professional as boot location, it gets past the starting screen..but the instant the windows loading screen pops up right after that...it reboots..i have gone through F8 and tried every boot method and none have worked...i am in dire need of help:(

---

### Post by Partyboi2 on 2009-09-19
If you have a Windows disk try booting it and choosing the recovery console option, then at the prompt type
```
fixboot
```

---

### Post by flairtorc on 2009-09-19
ok ill try that and tell you what happens

---

### Post by bumanie on 2009-09-19
Go into console mode of xp and type FIXBOOT followed by FIXMBR. You will then have to reinstall grub. [Follow this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by flairtorc on 2009-09-19
didn't work...and to bumanie, didn't work because if i try any start up mode even all the ones after pressing F8 it will restart imediatly after i hit it..as in...any startup mode for Windows XP Profesional leads to reboot

so....anymore ideas?....a lot i've already tried as my subject post states

---

### Post by swerdna on 2009-09-19
boot off of the xp install cd, go to the end and select to "R" for Repair instead of to install. Log as administrator. Run this command: ```
chkdsk c: /f
```Once for me that fixed the exact same situation as you have.

---

### Post by flairtorc on 2009-09-19
don't have the cd...don't know where my dad puts them all...and i usually know where everything in this house is

---

### Post by bumanie on 2009-09-20
What I was suggesting also was meant to be done from the xp installation cd - sorry if that was not clear. Before you can fix xp, you will need the installation cd where, as the post above says, you need to choose the repair function. You will have to get the cd from your father. You could try super grub disk - it can re-write windows compatible boot sectors, but xp installation is the best way to go if you can get hold of the installation cd.

---

### Post by flairtorc on 2009-09-20
again...i don't have the installation disks

---

### Post by flairtorc on 2009-09-20
ok..i found a disc, got it to boot...logged in...but explorer process starts...then restarts...over and over again...i could even see it happening on the task manager...does anyone know how to fix this one by chance..

also when i log in i instantly get an error saying that a process isn't running asking me to terminate or debug, which neither do anything and no matter which i press i always get the restart loop of explorer

---

### Post by Partyboi2 on 2009-09-20
Try running  'sfc /scannow' to verify their integrity of the windows files.
Start>Run ```
sfc /scannow 
```Otherwise you may need to ask on a Windows support forum.

---

### Post by flairtorc on 2009-09-20
the explorer isn't there long enough for me to click anything...it's chaotic....would safe mode alow me to do it?

---

### Post by Partyboi2 on 2009-09-20
Try it and see.

---

### Post by flairtorc on 2009-09-20
well it was tricky...but i got it....it scanned...then i started the explorer process afterwards...worked for about 30 seconds...also i forgot to include that another process called dwwin also restart loops along with explorer..they are the only two..so...the scan didn't work

---

### Post by Partyboi2 on 2009-09-20
You could try a repair installation if you are comfortable doing one.
[http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm](http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm)
After wards you will probably need to [[COLOR=Blue]restore grub[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") using a Ubuntu live cd to be able to boot into Ubuntu.

If that does not work I would suggest starting a thread on one of the Windows forums about the problem to see if you can avoid having to reinstall Windows.

---

### Post by oboedad55 on 2009-09-20
> **Partyboi2 said:**
> You could try a repair installation if you are comfortable doing one.
[http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm](http://pcsupport.about.com/od/operatingsystems/ss/instxprepair1.htm)
After wards you will probably need to [[COLOR=Blue]restore grub[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") using a Ubuntu live cd to be able to boot into Ubuntu.

If that does not work I would suggest starting a thread on one of the Windows forums about the problem to see if you can avoid having to reinstall Windows.

Man, I looked at the first of those repair pages. And people say Linux is complicated? "Find your 25-digit code". Makes me shudder.

---

### Post by Partyboi2 on 2009-09-20
> **oboedad55 said:**
> Man, I looked at the first of those repair pages. And people say Linux is complicated? "Find your 25-digit code". Makes me shudder.
You haven't memorized your 25 digit code yet :p

---

### Post by flairtorc on 2009-09-20
sorry..i kinda fell asleep..working on the problem for about 6 hours kinda ate my day aways, the original problem is fixed, but the loop of explorer and dwwin processes came up, and a sfc /scannow didn't fix it, i'm kinda at a loss for ideas, and most of you can probably guess this didn't start till **after** i installed ubuntu

---

### Post by flairtorc on 2009-09-20
Hold the phone everything works now seeing as i am posting this from my windows side, i just did the scan twice and everything works grand, thanks Partyboi2 for the help :)

---

