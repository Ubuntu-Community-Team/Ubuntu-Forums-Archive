---
title: "Nvidia Geforce GT 650M driver installing problem"
date: 2014-05-17
forum: Hardware
---

### Post by Erdem on 2014-05-17
Hello

I have an asus N56VZ laptop which have Nvidia Geforge GT 650M graphic card and i am using Ubuntu Gnome 14.04
i try to install driver on software center and i even try to install with NVIDIA-Linux-x86_64-331.67.run driver file but its freeze at start up. any solution for that?

thanks for your answers

---

### Post by zer010 on 2014-05-27
I also have a 650M in my hp laptop.  This particular graphics card has the (in)famous Optimus technology.  Basically, it's supposed to switch between the onboard graphics for low intensity tasks and then switch to the nvidia graphics for high intensity tasks, like gaming.  In the past, I used Bubmlebee when I wanted to specify a certain program to use the nvidia card.  I've heard that nvidia's drivers are getting better at supporting Optimus in Linux.  I've not implemented any solution as of yet, just relying on the Intel graphics.  I'd like to know if there are any opinions on the best route to using the 650M.  I'm mostly leaning on going with Bumblebee again because it worked pretty well before.  As far as Erdem's issue, I've not really heard of this happening, but it does concern me as to what path I should take to use the nvidia card.

---

### Post by Djalmahal on 2014-05-28
I have the Asus 56NV with NVidia 650m. Once I install 14.04 it only uses the Intel grpahic card. I installed the NVidia 331 driver through "Additional Drivers". After that it uses Nvidia graphic card but it freezes every now and then, sometimes every 5 minutes. When I switch back to noveau it works fine but no speedy graphics (glxgears shows 60 fps, nvidia had over 1000fps). I'm still trying things out. I'll let you know.

---

### Post by leodido22 on 2014-06-13
I have an Asus N56VZ with GeForce GT 650M. I'm "stuck" with nouveau because of the problems that nvidia 331 driver causes (as described by Djalmahal). Not found any solution yet ..

---

