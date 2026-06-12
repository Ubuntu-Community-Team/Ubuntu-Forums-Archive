---
title: "nForce sound drivers"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by GRUbY on 2005-03-15
I know that similar subject was already discussed, but i still don't have answer on my problem. I've installed nVidia nForce driver FORCE-Linux-x86_64-1.0-0301-pkg1.run but i don't know how to make it work (default driver). And also i still have snd_intel8x0 modules running and i don't know how to get rid of them. In nVidia readme everything is explained how to do it on other distributions - i have Hoary - and i don't know which files and where i should modifie. Thanks for your help (as quick as possible :]), regards
GRUbY

---

### Post by wylfing on 2005-03-15
I haven't seen a satisfactory answer to this either. 

Below is more or less what I did to get the 0292 driver installed. (I later went back to snd_intel8x0 because of mixing issues, but supposedly the 0301 driver unlocks hardware mixing.) I'm going from memory so hopefully this is about right. It may be necessary to run depmod -a at some point.

1. Get a console (Ctrl+Alt+F1).
2. Switch to runlevel 1 (sudo teleinit 1).
3. Forcibly remove snd_intel8x0 using rmmod -f.
4. Rename snd_intel8x0.ko to snd_intel8x0.ko.disabled.
5. Create a text file /etc/modutils/nvsound (it doesn't have to be named that, but that's where to make it) containing one line:

alias snd-card-0 nvsound

6. update-modules
7. Reboot.

On the way back up, alsa will complain about not seeing any sound cards. That's because there's no longer an alsa driver installed (nvsound is an OSS module). Open a terminal and type 'sudo lsmod | grep nvsound' to see if the nvsound module is installed. If it is, try running xmms with the OSS output plugin and see if you get sound. You may also need to run nvmixer to adjust volume levels and so on.

Now, getting the nvsound module to play nicely with the rest of your system is another trick entirely. However, you may be able to run 'gstreamer-properties' and pick OSS for output and let the hardware mixing do its thing. That could possibly work.

When I get a stretch of time when I don't have to be particularly productive I will experiment and see for myself.

P.S. I know the instructions above are a filthy, brutal way of doing this. If anyone can teach me to do it better please do.

Edit: Erp, it's /etc/modutils not /etc/modules.d my mistake. Corrected above.

---

### Post by GRUbY on 2005-03-17
Thanks - everything worked, but i still can't hear several sources of sound :( . Maybe i still shoud somehow enable hardware mixing ???

---

