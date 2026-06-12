---
title: "Question about drivers NVIDIA"
date: 2011-11-23
forum: Hardware
---

### Post by slaykristian on 2011-11-23
Good morning at all,

just a question.

What can I do to install NVIDIA drivers from NVIDIA site under my Ubuntu studio 11.10 with customed rt kernel?!

It was since 2 distros wich I cannot install these drivers under a Vanilla kernel. 
Do you know if exists a workaround?!

Thanks in advanche friends.

Regards!

---

### Post by SeijiSensei on 2011-11-23
Use the "Additional Hardware" application in Ubuntu to load the correct drivers from the repositories.

---

### Post by T.exe on 2011-11-23
I was also having the same problem. Does the NViDiA installation say anything about killing the X session in order to install the drivers??

Press ctrl+alt+f1 (A terminal mode will open up, login with your 'username' and 'password')
And type the commands given below:

$sudo service lightdm stop (This command disables the lightdm used in ubuntu 11.10)

$cd to where you downloaded the drivers to (better to download the driver and keep it in your HOME directory itself for convenience)

$sudo chmod +x NVIDIA-Linux-x86-280.13.run (or whatever the driver filename is)

$sudo ./NVIDIA-Linux-x86-280.13.run (installation will start... follow the steps)

$sudo service lightdm restart (or reboot with $sudo reboot now, which is better)

---

### Post by T.exe on 2011-11-23
How ever.. its much easier and appreciated to use the repos. to download and install drivers,as** SeijiSensei **mentioned. 

[B]Except a NVIDIA start-up screen during boot, i don't see much of a difference between kernel installation and repository installation of NVIDIA drivers... khe khe khe!
[/B]

---

