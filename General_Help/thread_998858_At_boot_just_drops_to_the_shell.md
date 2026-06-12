---
title: "At boot just drops to the shell"
date: 2008-12-01
forum: General Help
---

### Post by jchysk on 2008-12-01
Hello. I'm running 8.04 Ubuntu. I installed some updates yesterday, one of which I believe was a Xorg update. I was asked to restart and didn't do so until today. 
After it was running I noticed the sound was muted and when I clicked it I got some no gstreamer error or something and aplay detected no sound card. I looked up online some solutions and found something that said to uninstall and reinstall Alsa, so I tried that and I restarted. I can't remember the exact command but it was something like sudo apt-get --purge remove alsa something, and then I reinstalled it.
Since then when I boot it just drops to a shell. I've tried booting to different versions of the kernel and using recovery mode. I don't see any errors or really even know how to approach finding a solution to this problem. I'm fairly helpless without a GUI. Please help!


Some additional information I realized. At boot, the Ubuntu logo with the bar going across shows up and when the bar gets to the end is when it drops to shell. There's this message:

Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/blah) = sdc5(8,37)
kinit: trying to resume from /dev/by-uid/blah
kinit: No resume image, doing normal boot...

I don't know if that means anything. It doesn't seem like an error message.

Before that logo shows up there's a message:
Kernel alive
Kernel direct mapping tables up to 100000000 @ 8000-d000
which I always see during startup and have always ignored.

---

### Post by taurus on 2008-12-01
Log in with your username and password.  Then, what happens when you run this command at the prompt?

```
startx
```

---

### Post by freqhack on 2008-12-01
Assuming the rest of your system is ok... run the following command once you've logged in.

```
startx
```


This should start an X Windows session. If it does, then go to System > Administration > Login Window

Under the first tab (General) make the 'Default Session' Gnome.

---

### Post by freqhack on 2008-12-01
Taurus, you beat me by 1 minute :rolleyes:

---

### Post by jchysk on 2008-12-01
omg you guys are amazing! No idea what happened to make it stop doing that but that worked perfectly. Thanks a lot guys!

---

### Post by taurus on 2008-12-01
Looks like when you "purged" alsa, you probably also removed gdm.  So, you need to reinstall it so it would boot to GUI login screen for you unless you don't mind logging in and start your Gnome session with startx.

Log out of Gnome session and when you are back to the prompt, run

```
sudo apt-get update
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

---

