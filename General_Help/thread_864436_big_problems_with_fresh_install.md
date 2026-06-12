---
title: "big problems with fresh install"
date: 2008-07-19
forum: General Help
---

### Post by cocodog13 on 2008-07-19
hi, im a linux newbi and have been using ubuntu for about 4 hours now (not the first distro iv used) and have so far run into a couple of problems. firstly, on the first boot after instaling ubuntu gnome wouldnt load after login(gave unspecific errors) and now after following the guide [heer(link)]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart") to try and get my wifi working im having so many problems its unbeleavable for a fresh install :( after following those instructions on ndiswrapper i tryed to run firefox(the network config utility said i had ip/dns ect) but firefox wouldnt run, so i decided to reboot(windows style :P) after clicking that little power icon in the top right for about 30 seconds i got bored and used the button in the p.c case. 

now the bloomin thing wont boot with the wireless card pluged in!! GRRRRR!

when i boot without the card in the system starts up and gets to the login screen but when you log in on any user exept root gnome hangs indefinitely. on root gnome loads but nautilus gives an error and NOTHING runs, not even the terminal.

i know there is not much(if any) usefull info heer but im not shure how to find info that is or what i will be able to get to with the system in this state.

thanks in advance for any help :)

---

### Post by WRDN on 2008-07-19
When you booted from the disk, did you check its integrity, as it sounds like corrupt packages have been installed?
You could try booting into Recovery Mode and selecting "Fix Broken Packages", and you may wish to "Fix X Server" (or words to that affect).
When the normal login screen appears, press Ctrl, Alt and F1 to arrive at the command prompt. Then, login and try starting the X Server using the command "startx".
If you can access synaptic, the it will list any broken packages.
I think there is another command to find broken packages, but someone else will have to provide it.

---

### Post by cocodog13 on 2008-07-19
i just noticed somthing. i think iv installed the i386 version of ubuntu on a amd64 pc :S, i downloaded both versions because i intended to install ubuntu on both my p.c (one being an amd64 athlon the other a intel quad 32) this is bad no?

---

### Post by WRDN on 2008-07-19
> **cocodog13 said:**
> i just noticed somthing. i think iv installed the i386 version of ubuntu on a amd64 pc :S, i downloaded both versions because i intended to install ubuntu on both my p.c (one being an amd64 athlon the other a intel quad 32) this is bad no?

Generally, the 32bit OS you installed has had less issues than the 64bit version.
On a 32bit CPU, you can only install a 32bit OS, but on a 64bit CPU, you can install a 32 or 64bit OS.
Thus, this should not have caused the problems you specified.

---

