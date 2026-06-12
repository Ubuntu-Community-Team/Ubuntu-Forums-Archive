---
title: "tty1 is displayed before the GUI starts?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by :-( on 2009-11-02
Alright, I (a *kind* of (but not really) Ubuntu savvy person) have a slight but annoying problem. When I boot Ubuntu 9.10, it goes to the normal splash screen, but when it's done loading, the system randomly goes to tty1 and hangs there for about 5-15 seconds. Then it goes to the normal GUI, and it all works normally (except that there is a pop before any noise, but I'll fix that by going around Google, I just haven't bothered yet).  In case it helps, my laptop is a Gateway MX3701: [http://support.gateway.com/s/Mobile/Q106/Bishop/2905896Rcl2.shtml](http://support.gateway.com/s/Mobile/Q106/Bishop/2905896Rcl2.shtml)

---

### Post by Dasda on 2009-11-02
I have same problem. My ttyl screen last about 2-5 secs though.

---

### Post by :-( on 2009-11-03
Bump...

---

### Post by pastalavista on 2009-11-03
Mine was doing pretty much the same thing. The sound still 'pops' when activating or shutting down but the audio in general works fine except, in some certain flash players, it's a little scratchy sounding. But after an update to xsplash (not usplash any more) the 'tty1' just flashes on screen for half a second before the actual splash screen starts.

---

### Post by :-( on 2009-11-03
I've tried updating xsplash, but it is already up to date.

---

### Post by pastalavista on 2009-11-03
In the System-> Admin menu, open Software Sources and on the 'Updates' tab check the "proposed" and "backports" boxes. It was after I added those repos that I got the xsplash updates.

---

### Post by :-( on 2009-11-03
Thanks, but I tried that and it didn't work. Did you do anything other than that?

---

### Post by pastalavista on 2009-11-03
> **:-( said:**
> Thanks, but I tried that and it didn't work. Did you do anything other than that?
no, but then the rest of your system is probably very different from mine other than the GPU.

good-luck

---

### Post by :-( on 2009-11-03
Thanks.

---

### Post by :-( on 2009-11-03
Bump... Anybody else having this problem?

---

### Post by :-( on 2009-11-03
Just in case anybody is interested, you can solve the popping noise by typing
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```into the terminal, and changing ```
options snd-hda-intel power_save=
``` to 0 (for me, it was 10). All credit goes to [lonniehenry]("http://ubuntuforums.org/member.php?u=113395") for this!

---

### Post by falconindy on 2009-11-03
tty1 showing up is essentially normal behavior. I suspect that xsplash is tied to the boot procedure and terminates when run level 3 finishes and control should be handed off to run level 5 (GUI). However, at this point, the GUI isn't quite ready so you see the text based login console until gdm or whatever other graphical login manager is ready.

If I'm right, there's a "fix", but I won't make any assurances that you won't break something else by doing this. Go into /etc/rc5.d/ and you should see a bunch of numbered files. The numbers are essentially the order the files load in for that run level. If you lower the number associated with the file tied to your login manager (gdm, xdm, etc), you might be able to finish loading it sooner thereby reducing or eliminating the delay.

edit: ignore the above... just threw karmic on a VM and things have changed somewhat...

more edit: digging around /etc/init.d shows that xsplash is halted when init encounters the script to run a login manager. Without a fair bit of digging, I'll just say this: the fix is more ram and/or cpu cycles.

*shrug*

BSD style inits are so much easier to deal with....

---

### Post by :-( on 2009-11-04
Well, my computer has randomly stopped with the going to tty1. I think it may have had something to do with the xsplash update.

---

### Post by ublintu on 2009-11-17
Hi,
I have the same problem:  [http://ubuntuforums.org/showthread.php?t=1315876](http://ubuntuforums.org/showthread.php?t=1315876)

---

### Post by blegs38552 on 2009-12-08
Got it too. Have 2 GB RAM so I doubt that memory is the problem.

---

### Post by presence1960 on 2009-12-08
The popping noise I used to have. I found a fix on this forum. Open a terminal and run ```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

scroll down to the last 2 lines and change them to read this:


Power down HDA controllers after 0 idle seconds
options snd-hda-intel power_save=0 power_save_controller=N

Please note this works if you have an HDA audio card. Make sure to uncomment those lines as well as changing the values. Once I did this never got the popping noise again.

---

