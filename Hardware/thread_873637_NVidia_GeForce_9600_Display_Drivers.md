---
title: "NVidia GeForce 9600 Display Drivers"
date: 2008-07-29
forum: Hardware
---

### Post by jdenicholls on 2008-07-29
I'm having problems with my graphics card. I cannot seem to download any display drivers for it, even though I found the relevant drivers on the [NVidia Website]("http://www.nvidia.com/object/linux_display_amd64_173.14.05.html"), I cannot download them through EnvyNG or the Hardware Drivers app built in to Ubuntu.

Any ideas?

---

### Post by pedrogent on 2008-07-29
Have you just recently installed Ubuntu? Or have you just recently added this card to your system?

Open up a terminal and type:

```
sudo aptitude install nvidia-glx-new
```

This should do the job. If not, let me know.

---

### Post by jdenicholls on 2008-07-29
Seems to have installed ok, but my Steam has stopped working for some reason, so I'm gonna have to reinstall steam to see if the drivers are working properly. Thanks for your help.

---

### Post by pedrogent on 2008-07-29
No problems. Let me know how it turns out.

---

### Post by jdenicholls on 2008-07-29
Lol not good. I tried to reinstall steam but now whenever I try to launch a game or even just install a game the entire thing crashes. Must be an issue with WINE, although it wasn't doing this before I installed those drivers so perhaps they are the problem?

---

### Post by blazercist on 2008-07-29
actually nvidia-glx-new doesnt support the 9600 AFAIK, I have the 9600 and I needed to use the drivers from the nvidia site to get 3d.

download the driver to your /home dir.
sudo apt-get install build-essential
ctrl+alt+f1
login
sudo chmod +x NV*
sudo /etc/init.d/gdm stop
sudo sh NV*
Follow onscreen directions
sudo /etc/init.d/gdm start
enjoy

---

### Post by jdenicholls on 2008-07-29
Ok thanks, I'll give that a shot. Thanks.

---

### Post by jdenicholls on 2008-07-29
Ok I have a small problem. I cannot place those files into the /home dir because only the root user can alter the content of that folder. Any suggestions?

---

### Post by blazercist on 2008-07-29
um i didnt literally mean /home its supposed to be in your home folder.  /home/your_user_name_here/
or
/home/$USER/
works too

if it downloads to your desktop you should be able to drag and drop to your home folder

---

### Post by jdenicholls on 2008-07-29
Ok I managed to install the drivers this time and I can see they have been recognised because I can access them through Applications-->System Tools-->NVidia X Server Settings.

The only problem is that my sound has now gone. I think this may be because I uninstalled some sound drivers by accident during the install process, because my sound uses NVidia sound drivers. Any ideas on how to fix this?

Also thanks very much for your help so far. I'd be stabbing at this in the dark without your help :)

---

### Post by jdenicholls on 2008-07-29
Ok weird thing is that my sound just came back randomly. Now my media players and everything work.

Only some of my games work at the moment, like Gnometris and Nibble. However when I try to launch something graphics intensive like Pingus (Lemmings basically) the game just loads and crashes in an instant.

Edit: Got Warsow to work, from the repos. Strangely it only affects some games.

---

### Post by xodus1 on 2008-07-29
load those program using the terminal it may pinpoint the problem

---

### Post by jdenicholls on 2008-07-30
And how might one do that? I'll have to look it up. I'm guessing the terminal should read out what the issue is.

---

