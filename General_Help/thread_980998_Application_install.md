---
title: "Application install"
date: 2008-11-13
forum: General Help
---

### Post by thilakderm on 2008-11-13
HI guys. Please help me out. I have transferred a VLC player in rar format from a windows PC to my ubuntu. How to install it

---

### Post by taurus on 2008-11-13
VLC player is available from the repos.  Install it either with System -> Administration -> Synaptic Package Manager or open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by Portmanteaufu on 2008-11-13
> **taurus said:**
> VLC player is available from the repos.  Install it either with System -> Administration -> Synaptic Package Manager or open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

Once you've done that, a shortcut to launch the VLC player should appear under Applications -> Sound and Video -> VLC. (As seen [here.]("http://www.debianadmin.com/images/songbird/9.png"))

---

### Post by lifestream on 2008-11-13
Hello thilakderm, and welcome to Ubuntu :)

Whenever you want to install something, you should look in **Applications -> Add/Remove...**. There will be a search bar at the top right. You can enter something there, like, vlc. Then you will see it. Click the check box to install it.

Make sure it says ***Show: All Available applications***.

BY THE WAY, **if** you can't play music and video files yet, go on that Add/Remove, and install Ubuntu Restricted Extras.

You might have to enable restricted repositories:
> 
System->Admin->Software Sources
*enter password*
*Enable* Proprietary drivers for devices (restricted)
*Enable* software restricted by copyright or legal issues ( multiverse)
[I]Close, Reload.
When done, go to Add/Remove... search for ubuntu restricted extras, click it, install it.[/I]


---

