---
title: "Ubuntu 9.04 nvidia driver glx missing on display : 0.0 problem !"
date: 2009-07-21
forum: Hardware
---

### Post by shankar_mg on 2009-07-21
Hi,
I am using nVidia GeForce 6600 graphic card with OS as Ubuntu 9.04 (Jaunty Jackelope). I installed the recommended driver nvidia-glx-180 in my system for enabling desktop effects in my system. But when I use glxgears command, I get the following output
Xlib: extension "GLX" missing on display ":0.0"
Error: couldn't get an RLB, Double-buffered visual

Can somebody guide me how to get over the problem. I even tried earlier version of glx like nvidia-glx-173 and nvidia-glx-71 but i still have the same problem.

Regards,
Shankar

---

### Post by Nazaroo on 2009-07-21
I'm no expert, just curious:

Did you:

(1) Run the nVidia configure program from a console or commandline first?

(2) Click on Preferences/Display Pulldown Menu in Linux and get redirected to the nVidia options/configure program?

From there I think you ought to hit the "Save to X Configurattion File" button on the "X Server Display Configuration" menu.

...
hope this helps.

---

### Post by shankar_mg on 2009-07-22
Hi,
 I tried saving to X configuration file but it didnt solve the problem. Can somebody help me with this issue.

Regards,
Shankar

---

### Post by shankar_mg on 2009-07-24
Hi all,
I solved this problem by updating my nVidia driver from 180.44 to 185.18.14. 

Be careful when you are upgrading it as we have to stop our X windows system and do it in text screen.  For detailed steps on installing nVidia driver, check the last reply by jefkin @ [http://ubuntuforums.org/showthread.php?t=1148293&page=2](http://ubuntuforums.org/showthread.php?t=1148293&page=2)

Thanks,
Shankar

---

### Post by shankar_mg on 2009-08-29
Hi all,[COLOR=#FF0000][B]
[COLOR=Black]  [/COLOR][/B][/COLOR]The problem with nvidia-glx is solved in new version nvidia 185.18.36. Please follow the steps below to get rid of the GLX issues.
[COLOR=#FF0000]****[/COLOR]
[COLOR=#FF0000][B][COLOR=Black]
[/COLOR]1.[/B][/COLOR] Open a terminal and paste the following commands to add the Launchpad repository:
sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

[COLOR=#FF0000]**2.**[/COLOR] Import the GPG key:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

[COLOR=#FF0000]**3.**[/COLOR] Now you can install the Nvidia 190.xx beta drivers:
sudo apt-get update && sudo apt-get install nvidia-190-modaliases nvidia-glx-190

Source of help : [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

Regards,
Shankar

---

### Post by shankar_mg on 2009-08-29
Hi all,
 In previous post, just change number 190 to 185 to get the stable nvidia version.

Rgds,
Shankar

---

