---
title: "[SOLVED] 3D acceleration fails: BadRequest"
date: 2008-11-14
forum: General Help
---

### Post by jon.mithe on 2008-11-14
Hi,

Struggling to find a solution to this problem. I recently upgraded from 8.04 to 8.10 and my 3D acceleration seems to of broke, not even the mesa drivers seem to work.

fglrxinfo, glxinfo, glxgears all throw this out:


```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
```


I've tried the basics, removing and reinstalling fglrx from synaptic but still the same problem.

I've removed fglrx and would of though it would drop back to the mesa drivers, but I still get the same error.

I've tried enabling the drivers from jocky / hardware devices but nothing happens (download/install window pops up for 1 or 2 seconds then dissapears, no error messages, nothing).

I'm guessing this problem is something to do with x / gnome since by the error message and it seems to be failing the same regardless of the drivers used.

I have a fairly bog standard core duo with an ATI (unsure which one, pc is a dell, couple years old and was not exactly cutting edge...). With 8.04 I had fglrx installed and working perfectly (had some trouble I fixed here [http://ubuntuforums.org/showthread.php?t=846016](http://ubuntuforums.org/showthread.php?t=846016)), its just the upgrade has made things fail.

Any help to fix or understand this would be great cheers,
Jon.

---

### Post by jon.mithe on 2008-11-14
Solved it but not sure exactly what did it.

Removed fglrx, few days later restarted pc -> fglrx pairmode setup broke horribly.

Reinstalled fglrx but had to configure screens.  Aticonfig kept failing when trying to add pairmode and directing to my backup xorg the pair modes kept on being lost.

So, did a "sudo dpkg-reconfigure xserver-xorg".  Aticonfig, still wouldnt accept pairmodes.  Did a "sudo amdcccle" and change things in the gui setup, restarted my pc and my setup was correct (after logging in I had to go to screen resolution and set it to the big screen in the dropdown).

Checked my 3D drivers, and everything magically worked.  glxgears ran well over 1000fps. 

My best guess would be the reconfiguring xserver-xorg fixed the problem as reinstalling fglrx before hand did not do anyting (+ mesa did not work).  If any else if having these problems, word of warning, reconfiguring that will break and fancy dual screen setups you have.  Fairly straight forward nowadays to setup dual screens.

Jon.

---

