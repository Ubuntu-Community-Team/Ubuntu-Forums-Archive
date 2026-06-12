---
title: "Terminal &quot;not responding&quot;. Sometimes just white screen when terminal opens."
date: 2008-07-25
forum: General Help
---

### Post by Lakjin on 2008-07-25
Okay I have ran into this problem a few times now.

Sometimes when i open Terminal, it doesnt bring up the usual promote, lakjin@w/e i dont remember. Sometimes its just a blank white screen, and nothing happens. When i hit "x" to quit, it asks me to force quit and tells me terminal isnt responding. I always have to restart to fix it.

Any idea whats up? I did try google search and the search tool here, but TBH i dont know what keywords to try. Anything with "Terminal" in it brings up way too many results. Thx

---

### Post by binarycortex on 2008-07-25
I am having the same problem, if I leave my ubuntu up and running for more than a day or two my terminal will nolonger open. I tried using 'killall gnome-terminal' via the alt+F1 login, but it said there were no processes killed. Can anyone help with this?

Ian

---

### Post by Lakjin on 2008-07-25
this problem is getting more and more frequent...

and i noticed when it happens, it just doesnt affect terminal. i cant view pics, use my panels, load system monitor, restart, etc.

i have to restart via ctrl alt f2 -> alt ctrl del

so maybe its a nautilus problem?

---

### Post by Lakjin on 2008-07-27
bump?

---

### Post by Lakjin on 2008-07-29
bumpx2. anyone know whats up? i also submitted a bug report on this.

---

### Post by Lakjin on 2008-07-30
anyone?

---

### Post by nsivin on 2008-07-31
I have had the same problem with a blank terminal that does not show input. I have tried two things that may be relevant. 
(1) I normally use the desktop computer, with an NVIDIA Geforce graphics card, in portrait mode. I went back to landscape mode, and it made no difference. I thought that the proprietary driver might be responsible, but this suggests it isn’t. 
(2) I tried typing commands into the blank screen, and found that, although they do not appear, those that open a GUI, such as gedit, work. Those that don’t are useless, since the blank screen does not act as standard output. 
This looks like a definite bug. If someone wants me to try anything to narrow the problem down, contact me at [email]nsivin@sas.upenn.edu[/email].

---

### Post by bob67 on 2008-08-19
I have the EXACT same problem. It's exactly as you describe it. If I leave the computer running overnight, I am no longer able to open the terminal (or anything for that matter) in the morning...

My thoughts are that something is turning off the disk and not turning it back on? That's just purely a guess though.

---

### Post by nsivin on 2008-08-20
I finally solved the problem. The restricted NVIDIA driver I had installed was nvidia-glx. That is what caused the trouble. When I wiped out and reinstalled Hardy, I got a message offering to install a restricted driver. The one it offered was, instead, nvidia-glx-new. I accepted and have had no problem since.

---

### Post by kabaforo on 2008-11-19
I am entirely new to linux, just installed it a day ago. My problem is that when launch the terminal, it just goes white and i dont know what to do about it.

Please help if you can. Thanks
kabaforo

---

### Post by unutbu on 2008-11-19
kabaforo, it seems, according to this thread, that a white terminal may be caused by using the wrong video card driver. 

If you have a modern Nvidia card, you should use the nvidia-glx-new package. 

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package.

If you have a GeForce4, you may need the nvidia-glx
package.

Here are instructions on how to install packages:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

