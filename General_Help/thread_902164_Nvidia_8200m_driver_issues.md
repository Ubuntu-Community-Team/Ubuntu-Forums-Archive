---
title: "Nvidia 8200m driver issues"
date: 2008-08-27
forum: General Help
---

### Post by VonKrunkovich on 2008-08-27
I have ZERO experience with Linux. I just installed Ubuntu 8.4 on my laptop tonight, and most everything is working properly except for two things. Number one, my video card was detected and drivers were installed, but once i restarted my computer it would begin to boot Ubuntu then the screen would turn off. After that i couldn't login until i repaired Ubuntu, and then it would be back to the default 640x480 resolution. Also my sound is very scratchy, and I'm really not sure why.

---

### Post by aman.agx on 2008-08-27
Hi,
You can try doing what I have mentioned in my post in the following thread

[http://ubuntuforums.org/showthread.php?t=902159]("http://ubuntuforums.org/showthread.php?t=902159")

---

### Post by Ms_Angel_D on 2008-08-27
Try the following

First go to System » Administration » Hardware Drivers and make sure the Nvidia Accelerated Graphics Driver enabled

the run:
```
sudo apt-get install nvidia-settings
```

then press alt+f2 and run:

```
sudo nvidia-settings
```

Go to "X Server Display Configuration", select your resolution of choice, click on "Apply", and then click on "Save to X Configuration File". 

You may need to reboot to see the changes

---

### Post by VonKrunkovich on 2008-08-27
When I try to enter, sudo apt-get install nvidia-settings , it says [sudo] password for phoenix (which is my name) and it won't allow me to enter any characters.

---

### Post by aman.agx on 2008-08-27
you cant see characters in linux when you type a password in terminal. Just type it there and press enter

---

### Post by VonKrunkovich on 2008-08-27
Well the first time i followed your instructions it gave me an error and told me to run a certain command and restart the x server so i did so and then i tried to re-enter that preference menu for the vid card and when i ran the command nothing happened. Also, upon further inspection i noticed that the screen on my laptop is not being detected as a valid display.

---

### Post by Ms_Angel_D on 2008-08-27
Please don't double post, One thread is plenty for the same issue. What command did it tell you to run?  My display isn't detected properly either however it still runs.

---

### Post by VonKrunkovich on 2008-08-27
I appologize for the double post. I can't recall the exact command, but it was something like nvidia-x configure. I'm sorry i should have written it down.

---

### Post by Ms_Angel_D on 2008-08-27
Did you reboot? I always need to reboot after saving to x before my Nvidia settings take effect, just restarting the xorg doesn't seem to work properly.

---

### Post by VonKrunkovich on 2008-08-27
Yeah, I restarted, and that's when the command you gave me stopped bringing up the menu.

---

### Post by Ms_Angel_D on 2008-08-27
That's very strange indeed, I would love to be of more assistance, however I don't think My knowledge on the matter goes any further you may want to check out [EnvyNG]("http://albertomilone.com/envyngfaq.html#A") I personally have not needed to use it however a lot of people seem to use it and to fix their problems.

---

### Post by Garratt on 2008-08-27
read that other thread again

envy is simple and will more than likely fix any problems

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by aman.agx on 2008-08-27
You can try this post 
[http://ubuntuforums.org/showthread.php?t=902159]("http://ubuntuforums.org/showthread.php?t=902159")
It has two ways to resolve this issue choose the one you find easy. I think metal hell is telling the same thing but it might still be useful to look at it

---

### Post by VonKrunkovich on 2008-08-27
When i try to go to the Nvidia X Server Settings this is what appears 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


when try to run "nvidia-xconfig" in the terminal this is what appears

  phoenix@Doomsday-Device:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

phoenix@Doomsday-Device:~$ 


I'm sure I'm just doing something wrong

---

