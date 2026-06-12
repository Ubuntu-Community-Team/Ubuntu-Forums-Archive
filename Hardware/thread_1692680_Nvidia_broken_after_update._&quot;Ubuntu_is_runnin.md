---
title: "Nvidia broken after update. &quot;Ubuntu is running in low graphics mode.&quot;"
date: 2011-02-21
forum: Hardware
---

### Post by killabudz on 2011-02-21
Hey everyone. A couple of weeks ago, this error message started coming up when booting up. After the error message, is just a dead screen, no way to enter any commands, nothing. Running ubuntu 9.10. 

"Ubuntu is running in low graphics mode. the following error was encountered. you may need to update your configuration to solve this.  [EE NVIDIA[O] failed to load tje NVIDEA kernel module.       [EENVDIA[O] ***aborting***.    [EE screen[s] found,but none have a usable configuration. "

Not sure if it was an update that broke it, or what, but this is happening on my grandfathers computer, so one way or another I have to help him. The two biggest obstacles are that I live in FL, him in NJ; and that the pc contains his most recent tax info, which hasnt been backed up. The tax info is in a crossover bottle, In Quicken. I would just have him reinstall, but i must first save the quicken data. 

So I'm thinking that the easiest thing would be to fix the graphics driver, but without him being able to get to a prompt I dont even know where to start. Can someone please help?

---

### Post by gsgleason on 2011-02-21
At that point, press Ctrl+Alt+f1 (or any f-key through f6) to switch to another terminal.  you should be able to log in.

What I would do then is back up and remove /etc/X11/xorg.conf and reboot without one there, which should use the default driver (nv or nouveau), at which point you can use the 'Additional Drivers' thing to re-install nvidia drivers.

---

### Post by killabudz on 2011-02-21
Thank you very much for the reply. I immediately called him to try this, only to find out that at the screen where the error message appeared, the keyboard and mouse are unresponsive (both are ps/2). 

Once I learned this, I instructed him to boot from the live cd, and guided him through the process of backing up and removing the xorg.conf file. 

After this, rebooting DID bring us further, we actually got to a new screen on which the desktop background was visible. Here we encounter the message "A crash report has been detected blah blah click here", and also the update manager with the message along the lines of (but not verbatim) "an update failed, you may continue with a partial uppdate or close". 

Unfortunately, at this point- keyboard and mouse are still unresponsive, even though the PC is NOT frozen/locked/halted.

I can feel the progress but were not there yet!

Any ideas?

---

### Post by killabudz on 2011-03-01
help?

---

### Post by Yellow Pasque on 2011-03-01
Boot to recovery mode (Hold shift after the BIOS posts if the GRUB menu doesn't normally appear). Choose root prompt with networking, log in, and uninstall/reinstall the nvidia driver from there. The nvidia kernel module should really be set up using dkms, so kernel updates don't bork the system.

---

### Post by killabudz on 2011-03-02
Thank you for the reply. He gets home soon, so I will try your suggestion. But, first, I told him too buy a USB keyboard and mouse to plug in and see if they respond, since he is all the way at his normal desktop screen, but the p/s2 devices arent responding.

---

