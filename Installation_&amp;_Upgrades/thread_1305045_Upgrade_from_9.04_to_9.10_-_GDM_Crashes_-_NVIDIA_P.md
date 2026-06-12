---
title: "Upgrade from 9.04 to 9.10 - GDM Crashes - NVIDIA Problems"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jdwannam on 2009-10-29
After using the upgrade manager to bring the system from 9.04 to 9.10, the machine hung after booting the kernel as it tried to start the Gnome Display Manager (GDM).  I was unable to log into the console of my workstation as the GDM was trying to start multiple times a second preventing keystrokes from being registered 75% of the time.  I was able to stop GDM from continually reloading by ssh'ing into the box from a laptop and running sudo /etc/init.d/gdm stop.

So upon trying to run xinit I saw that it was failing to load the Nvidia kernel module and quitting.  So, I manually edited the /etc/X11/xorg.conf file to use the nv driver instead for the time being.  This worked to get into my gnome-session.

I'm downloading the Nvidia driver version 173 at the moment to see if it works any better than the new driver.  It seems from reading around that there is a problem compiling the new Nvidia kernel module during the upgrade.  It's too bad that this kind of bug wasn't worked out before final release, but such is life.

Update:
Well, I get the same results with the Nvidia driver version 173.  I've had to ssh back into the host again to stop GDM from blowing up.  I have switched back to the nv driver and was able to log in again.

---

### Post by upchucky on 2009-10-29
there are a few workarounds to setting up an nvidia card, the following link is the only proper way to set up nvidia that enables the card to its full potential.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by tomtom12 on 2009-10-29
> **upchucky said:**
> ... the only proper way to set up nvidia that ..

No way, on 9.04 all was fine... so why direct back to old post??

---

### Post by upchucky on 2009-10-29
i just finished setting up my nvidia card using the instructions of that old post.

since it works for me just fine, i have not bothered to look if a new method has superceded that old post.

---

### Post by tomtom12 on 2009-10-30
Tried the instructions, but it failed. The driver said I needed version 173.14.xxx  as the newest do not support my old nvidia... well that explains. 
Solution really simple: installed nvidia-173 from synaptics... :)))) restart...done ;)

---

### Post by fixerdave on 2009-10-30
> **tomtom12 said:**
> Tried the instructions, but it failed. The driver said I needed version 173.14.xxx  as the newest do not support my old nvidia... well that explains. 
Solution really simple: installed nvidia-173 from synaptics... :)))) restart...done ;)


Yup... worked for me.

Boot to recovery mode, continue to login (console), sudo apt-get install nvidia-glx-173, reboot, and it worked.

Now I just have to get my XP partition back.  No big deal as I haven't used it in months - and kind of expected as I mucked about with the partitions before doing the install.  But, I like my racing sim, once in a while.


Thanks for the info on this; having graphics is nice.

   David...

---

