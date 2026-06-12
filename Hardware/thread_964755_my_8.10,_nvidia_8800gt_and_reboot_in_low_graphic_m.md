---
title: "my 8.10, nvidia 8800gt and reboot in low graphic mode..."
date: 2008-10-31
forum: Hardware
---

### Post by Attila_fdd on 2008-10-31
Hello I installed the new Ubuntu II 8.10 stable, after i've downloaded all updates i installed the nvidia **177.80 restricted drivers**. I've rebooted the machine and all works fine, compiz, movies, and so on.
 I turned off my pc and i turned on this morning. At boot it seems to doesnt detect correct video card settings and it boot in **low graphics mode** asking me to:
use default drivers, install new config,... anything 
I do it says me to reboot but nothing works. So i used in console mode, stopped GDM and reinstalled nvidia drivers throught **envyng **in text mode. I rebooted the pc and all works again. And the same things appen if i shut down and restart my pc again. why?

---

### Post by cmat on 2008-10-31
Go to the recovery console and select "xfix". Then reinstall the drivers via EnvyNG. That may help.

---

### Post by Attila_fdd on 2008-11-18
it doesnt works, commands not found...

i have installed ubuntu 8.10 64bit version.
The problem appears when i shut down  and the i turn on the computer, not when im rebooting the machine... it is very strange...

---

### Post by PmDematagoda on 2008-11-18
Try this, first remove the nvidia-glx* drivers from Ubuntu using Synaptic or apt, then reinstall the Nvidia drivers, after this, edit a modules file like:-

1) Open the file:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nvidia_new nv"
```
and then press Ctrl+X and save the file, then see if your problem is solved.

---

### Post by Attila_fdd on 2008-11-20
it doesnt work, i tried also to install drivers manually, same thing.
If i shut down my pc the xorg doesnt work correctly, if i reboot or if i enter the bios before boot the OS the pc works correctly... would it be a bios problem? it is strange because with ubuntu 8.04 i didnt have these problems

---

### Post by PmDematagoda on 2008-11-20
This maybe a little big in terms of the output, but can you post(or attach the file) the output of:-
```
cat /var/log/messages
```

---

