---
title: "Installing nVidia drivers, post ATI. 9800GTX+. Missing dependencies?"
date: 2008-09-06
forum: Hardware
---

### Post by Voidhawk9 on 2008-09-06
Have recently replaced my ATI card with a Geforce 9800GTX+. I'm confident I've well removed ATI drivers, but I can't get nvidia ones to install.
I've trawled the forums here for answers, tried a multitude of things, which has helped me make progress, but I'm stuck at this point.
Using EnvyNG, attached is the end of the output. Sorry it's an image, I couldn't seem to copy/paste from the Envy terminal, and I'm out of patience for today. :confused:

Help, please? There's an expensive piece of hardware that needs to be used!!!

---

### Post by Voidhawk9 on 2008-09-06
Synaptic reports a broken package, and lists nvidia-glx-new-envy, but it always fails to fix it, or in fact change anything. "Add Remove Programs" won't run, reporting a major fault with the package manager...

In summary, no joy yet.

---

### Post by Voidhawk9 on 2008-09-07
Anybody seen this before??

---

### Post by luxorvan on 2008-09-07
I just recently upgraded to the nvidia drivers supplied by nvidias website. If you got an error with envy I have another way that will probably help a little more. You need to use synaptic package manager and search libc and go through all of them and make sure you have all the libc packages "not just" libc6 thats already installed. Once you do that then download the driver from nvidia and save to your desktop. Then heres the instructions!
1. ctrl+alt+f1 while logged in will take you to where you need to be
2. login (name/password) otherwise you'll get nowhere!
3. type( cd ~/Desktop  ) hit enter
4.then enter( sudo su root ) then enter password
5. then enter(  /etc/init.d/gdm stop   ) stops x!
6. for 64 bit( sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run ) 
   or (  sh NVIDIA-Linux-x86-173.14.12-pkg1.run  ) for 32 
Hopefully you can handle it from there! I hope this helps, but if libc isn't installed already it won't work and it will keep telling you to install libc. good Day! You may want to start from a fresh install also

---

### Post by Voidhawk9 on 2008-09-07
luxorvan, your method failed where all preceding had failed. THANKYOU! :)

---

### Post by Crafty Kisses on 2008-09-07
Can you post all your system specs? I think that would help a lot.

---

### Post by Voidhawk9 on 2008-09-07
AMD 770 motherboard, 6000+ CPU, 2GB RAM, and the GTX+. Working now, though.

---

### Post by Jim42 on 2008-09-11
Excuse me, is there a way you could post the solution to this problem?, I'm having a similar issue, basically i just acquired a 9800GTX+, i have tried almost everything i could find:

- Tried envyng with the 173.xx driver
- Installed the 177.xx driver manually
- Installed nvidia-glx-new

Every time getting a similar result. The screen showing the console on and off about 3-4 times, then sending an "ubuntu is running in low-graphics mode" ... and something about not finding the graphics card. The message is hard to read cause the screen is split in 4, the two bottom squares showing something similar to ubuntu, and the top two some greenish-text-like noise.

Envy said my card was not supported, and i told it to install it anyway, the result was the same.

I just can't find a solution, and i really don't wanna install window$ T.T.

note: A fresh install of ubuntu looks ok-ish, and this happens after I try to install any of the drivers, no propietary drivers are shown, and I'm using hardy 8.04.

---

