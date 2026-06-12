---
title: "need help with VNC please"
date: 2008-09-11
forum: General Help
---

### Post by keq on 2008-09-11
ok, i asked about this about a week ago and i attempted to do it myself but its just not working....

ill set the story, i am new to ubuntu and for my entire life have used windows, i know a few commandline things to get me around in ubuntu but NOT MUCH.

i have a desktop machine with ubuntu 8.04 installed which is going to be wired to my router, i then have my laptop with windows xp installed on that, what i want to be able to do is "remote connect" to the linux box and be able to control the box from my laptop.

i tried installing tightVNC on both boxes and im not sure if it even installed on the linux box.

i also dont know how to find the server address of the linux box so that i can put that in the vncviewer on the windows laptop so that i can connect.

can anyone give me step by step instructions on how to install the "best" free vnc on the linux box and set it up with a secure password so its not just open to the world and then how to find the server address so that i can then connect with the laptop.

Thank You

---

### Post by gvartser on 2008-09-11
Maby this thread could help you out:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

/g

---

### Post by scoob8000 on 2008-09-11
It's actually very easy, and you don't even need to install anything on the Ubuntu box.

Just go to System > Prefs > Remote Desktop.

You can check the top two options, and specify a password below.

That's all there is to it!  :)

---

### Post by keq on 2008-09-11
> **scoob8000 said:**
> It's actually very easy, and you don't even need to install anything on the Ubuntu box.

Just go to System > Prefs > Remote Desktop.

You can check the top two options, and specify a password below.

That's all there is to it!  :)

ok now how do i get the server address that i need to use the viewer and connect to the linuxbox

---

### Post by rbc on 2008-09-11
If it is just a home network, if you are using Remote Desktop, you should be able to just use the linux computer's name, but if you want the IP, go to terminal (on the Ubuntu machine) and type ifconfig

---

### Post by keq on 2008-09-12
> **rbc said:**
> If it is just a home network, if you are using Remote Desktop, you should be able to just use the linux computer's name, but if you want the IP, go to terminal (on the Ubuntu machine) and type ifconfig


oooook thank you, im stuck in windows mode and i was typing in ipconfig HAHA

thank you

---

