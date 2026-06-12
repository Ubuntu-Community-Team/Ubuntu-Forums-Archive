---
title: "Installing New Nvidia Drivers"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Sojurner on 2009-02-26
I have wrecked my system 3 times trying to get drivers installed. Nvidia came out with the 180 series vid drivers and i cant get them installed right. What is the best way to do this.. 

In synaptic i can see the files for the 180 series that i assume i need to install. I do that and it uninstalls the ones for my 173 series drivers. I also install the drivers that i get off the nvidia website before i use synaptic.  

Im not exactly sure what has happened each time but i need help. Can anyone tell me what i need to do in order to get the drivers installed correctly  so that when i reboot i dont go into low graphics mode.

---

### Post by taurus on 2009-02-26
It depends on which model of nvidia card you have.  If you have an older one, then you need to use the legacy driver.  Since you mentioned version 173, sounds to me like you have an older model of nvidia card.

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by Sojurner on 2009-02-26
no i do not have an older card. Im just using the drivers that were running already on the system. I am using an 8800GTS 640MB Nvidia Card. 

knowing that what would u recommend.

---

### Post by montysan on 2009-02-26
On a similar note:

taurus, can you tell me whether there are drivers in 8.10 that will run my Quadro2 MXR (NV11GL) with acceleration? I'm really struggling to work out how to work this out myself....I'm new to these issues, sorry. The readme notes for 8.10 indicated that I might have issues, and I didn't want to risk it.

---

### Post by taurus on 2009-02-26
> **Sojurner said:**
> no i do not have an older card. Im just using the drivers that were running already on the system. I am using an 8800GTS 640MB Nvidia Card. 

knowing that what would u recommend.

> **montysan said:**
> On a similar note:

taurus, can you tell me whether there are drivers in 8.10 that will run my Quadro2 MXR (NV11GL) with acceleration? I'm really struggling to work out how to work this out myself....I'm new to these issues, sorry. The readme notes for 8.10 indicated that I might have issues, and I didn't want to risk it.

If you are running Gnome, go into System -> Administration -> Hardware Drivers to see which version is recommended.  Install that version.  For my XFX 6800XT at home, I installed version 177 (recommended) and everything is working fine every since intrepid first came out.

---

### Post by Sojurner on 2009-02-26
i was mistaken.. 177 was what i am using now, not 173. I want to install the 180 drivers since those are the new stable ones. but everytime i do i get massive problems. They are supposed to be the new stable ones tho. I alway end up in low graphics mode after i do it and end up needing to revert back to my saved profile.

---

### Post by taurus on 2009-02-26
So version 177 is running fine on your machine but 180 gives you problem!  I guess latest is not always the greatest.

---

### Post by Sojurner on 2009-02-26
no but when support for it is in synaptic i would think it would work.

---

### Post by Stan_1936 on 2009-02-26
Have you properly removed the 177 drivers BEFORE you try installing the 180 drivers?

---

### Post by Sojurner on 2009-02-26
to be honest im not really sure if im doing it right. Some instructions on how to uninstall the driver and reinstall the new ones would be very helpful. 

I uninstall and install the 177 and 180 stuff in synaptic and then i installed the 180 drivers off the nvidia website and i never got any errors, but when i try and load my gui it craps out.

---

### Post by tulambin on 2009-02-27
Hey Sojurner
Had about the same problem and here's what I found out!
Check out my post.  [http://ubuntuforums.org/showthread.php?p=6798887&mode=linear&highlight=nvidia+180#post6798887](http://ubuntuforums.org/showthread.php?p=6798887&mode=linear&highlight=nvidia+180#post6798887)

---

