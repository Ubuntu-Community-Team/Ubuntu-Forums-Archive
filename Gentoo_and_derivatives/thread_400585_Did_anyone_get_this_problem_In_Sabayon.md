---
title: "Did anyone get this problem In Sabayon?"
date: 2007-04-03
forum: Gentoo and derivatives
---

### Post by darksong on 2007-04-03
I just installed Sabayon, everything is working fine, drivers, beryl ect. I edit my X.11 config file so i can get my proper screen resolution but once i do this my Berly wont work anymore...

can anyone suggest anything that will solve this?

---

### Post by igknighted on 2007-04-03
> **darksong said:**
> I just installed Sabayon, everything is working fine, drivers, beryl ect. I edit my X.11 config file so i can get my proper screen resolution but once i do this my Berly wont work anymore...

can anyone suggest anything that will solve this?

try running the acceleration manager again.  Also, try to run 'beryl-manager' in the terminal to determine that it works.  If it works still and even after the acceleration manager it won't start on boot, create a symlink from the bery manager (its in /usr/bin) into the ~/.kde/Autostart folder.

---

### Post by darksong on 2007-04-03
:D just got it working again but it won't load beryl as its default manager still =(

---

### Post by igknighted on 2007-04-03
I think the issue is KDE defaulting to a saved session where beryl wasn't being used as the WM.  Try disabling this in the control center.

Also, at the KDM login screen, choose KDE and not previous.

---

### Post by darksong on 2007-04-04
> **igknighted said:**
> I think the issue is KDE defaulting to a saved session where beryl wasn't being used as the WM.  Try disabling this in the control center.

Also, at the KDM login screen, choose KDE and not previous.

what options will i need to change in the KDE control center - there seems to be no option for beryl as a windows manager under the control centre :S

---

### Post by igknighted on 2007-04-05
> **darksong said:**
> what options will i need to change in the KDE control center - there seems to be no option for beryl as a windows manager under the control centre :S

The setting you need to change has nothing (directly) to do with beryl.  You need to set the default session to be a fresh (new) session, not a saved session or resuming your previous session (I think one of these is default).  Alternatively you could set up everything you want running at boot and save the session then to be the default one.

If you set up a clean session to boot into and then add the beryl-manager to the Autostart folder it should load up no problems.  Beryl itself might have a setting in its own manager that would tell it what wm/window decs to use by default too, but you would have to explore that yourself, I'm not sure.

PS, speaking of beryl and KDE... anyone know of any work going on a qt version of beryl manager?  The whole gtk thing really bothers me.

---

### Post by anunnak on 2007-06-13
> **darksong said:**
> I just installed Sabayon, everything is working fine, drivers, beryl ect. I edit my X.11 config file so i can get my proper screen resolution but once i do this my Berly wont work anymore...

can anyone suggest anything that will solve this?

:(:( -  I have the same problem ... and I didn't find out how to make beryl work again, yet :(
I tried on many different computers, (graphics cards,monitors)  
- /sabayon 3.4 l2/ 3.3/3.3mini/  I got the same |   boot the live CD in , install the system, reboot - 
beryl works fine at the default resolution - If I change to any other resolution 
(#nvidia-settings)  ... bery stops - 
I can't select it as window manager anymore -- if I try to run beryl in CLI, I got the :
--
Checking Display :0 ...
Checking for XComposite extension : failed
No composite extension
134546341 screens detected. 
--
then I tried to run accelerator manager (# accel-manager), but it is already active. 
no problem found there.

does really nobody else have that problem ?!

---

### Post by mips on 2007-06-13
Try the Sabayon Forums or IRC channel.

---

### Post by igknighted on 2007-06-13
> **anunnak said:**
> :(:( -  I have the same problem ... and I didn't find out how to make beryl work again, yet :(
I tried on many different computers, (graphics cards,monitors)  
- /sabayon 3.4 l2/ 3.3/3.3mini/  I got the same |   boot the live CD in , install the system, reboot - 
beryl works fine at the default resolution - If I change to any other resolution 
(#nvidia-settings)  ... bery stops - 
I can't select it as window manager anymore -- if I try to run beryl in CLI, I got the :
--
Checking Display :0 ...
Checking for XComposite extension : failed
No composite extension
134546341 screens detected. 
--
then I tried to run accelerator manager (# accel-manager), but it is already active. 
no problem found there.

does really nobody else have that problem ?!

This is a very different issue than above.  His/her Beryl worked but did not load on startup, yours does not work period.  Depending on your graphics card there are very different solutions.  For nvidia, enable composite in xorg.conf and make sure you are using the proprietary drivers.  For ATI make sure you are either (a) using FGLRX, XGL and have composite disabled - OR - (b) using the 'radeon' driver and an r4XX or older card, no XGL, and have composite enabled.  If it still wont load, then start posting in the sabayon forums or IRC as there is likely something more serious wrong.

---

### Post by anunnak on 2007-06-14
I found a solution for me 
what I did is - made a fresh install with a cheatcode (F5 at boot menu)

Code:
noddc res=1920x1200 refresh=60 opengl=nvidia

and no need to change resolution after install  

if Beryl does not start at boot - here's code :
ln -s /usr/bin/beryl-manager ~/.kde/Autostart

---

