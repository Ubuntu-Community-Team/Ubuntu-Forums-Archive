---
title: "Geforce 8800m GTS freezing"
date: 2011-10-23
forum: Hardware
---

### Post by Galicslayer on 2011-10-23
My video Card: Nvidia geforce 8800m gts 512m
Ubuntu 11.10 64-bit

Problem: Any driver later than nvidia 270 will freeze my system to the point that my mouse is stuck and it doesnt respond to any keyboard interactions.

Details: So far it seems to be a problem with the drivers themselves and nothing to do with compiz or the kernel. 
During the freeze i could still ssh into my computer and use top to see that Xorg is operating at 100% cpu.
So far i have found out that this is not specific to Ubuntu, this is a problem to this specific video card and every distribution of linux, including 32-bit (i literally tried every single one).
I had tried to install 270.41.19 onto Ubuntu but i had dependency problems with libgl1-mesa-glx, which i had downgraded(along with other packages) and cause the system to become unstable(obviously).

The only workarounds is to leave the default nouveau driver installed or to deal with driver 173 but those wont cut it when it comes to gaming.

---

### Post by sombomb on 2011-11-17
I'm having the same problem, and I've seen others report the same.

---

### Post by geoffmcc on 2011-11-17
I would try the latest Nvidia driver in ppa. It is version 285.05-09


```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```

Then restart, and verify correct driver is activated by pressing the Window/Super key and type
nvidia x server settings. Open and verify driver version

If you have problems installing due to hidden dependency's use 

```
sudo apt-get dist-upgrade
``` 
        
Hope this helps, please comment if it does

---

### Post by sombomb on 2011-11-17
I just installed it using the ppa method, but ended up with the same results as before.

---

### Post by efflandt on 2011-11-17
I recently developed a similar problem in 64-bit Win7, and less often in 64-bit Maverick and 11.10 with my GT 430.

In Win7 the screen would either freeze, or would have a weird regular pattern on it, then "if" it recovered, Windows would say "there was a problem with the video driver, but it recovered".  It started happening with 270 something driver and persisted with most recent 285 driver.

In 64-bit 11.10 the screen would freeze except for mouse cursor movement, but mouse clicks, scroll wheel, or keyboard input did nothing using nvidia-current or nvidia-current-updates drivers (apparently both 280.13).

I switched from straight HDMI cable to DVI to HDMI cable and have not had a problem since, so I may have had a cable problem.  But if "m" is for mobile and that is a laptop, trying a different cable may not be an option for you.

I almost wonder if it has anything to do with digital sound configured properly or not.  I did not configure or test HDMI sound because I am just using analog stereo with 2.1 PC speaker system.

---

### Post by sombomb on 2011-11-18
yeah unfortunately switching cables & or video cards is out of the question

---

