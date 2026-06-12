---
title: "Is there any way to..."
date: 2008-07-15
forum: General Help
---

### Post by axenory on 2008-07-15
Is there anyway to install the drivers that were installed by default when I installed ubuntu?

I accidentally removed my soundcard drivers (alsa) and Now I dont know how to go back.

What do I have to do to get it back to work? is there an automacally way that ubuntu recognize the driver is missing or failing? I dont want to re format because of that ******.....

THANKS!!!

---

### Post by fyo on 2008-07-15
Is there a way to.... **actually write in the thread title what your query is about?**

Yes, there is.

---

### Post by fyo on 2008-07-15
If you need to reinstall Alsa, fire up Synaptic and install "alsa-base" and "libsdl-1.2debian-alsa". You might want to add the gstreamer alsa plugin and the alsa utils package.

---

### Post by phantomjoker on 2008-07-15
quite simply qo into synaptic package mannager and look for any files you might need - also have a look at what hardware you have incase you dont have the drivers.

---

### Post by chrisccoulson on 2008-07-15
Removing alsa will also remove the ubuntu-desktop meta package. You should be able to fix this by doing
```
sudo apt-get install ubuntu-desktop
```

---

### Post by axenory on 2008-07-17
None of your solutions have solve my problem :( 

I didn't unistall alsa. I am not sure what I did but I tried to install OSS and Alsa was replaced by it. How can I revert? I have tried everything you told me... Ive reach nothing yet. I need more help :( I dont want to reformat my lap

---

### Post by chrisccoulson on 2008-07-17
Without knowing exactly what you've uninstalled, it will be difficult to help you. Maybe you could have a look in your /var/log/dpkg.log, as this will contain a record of packages that were installed/uninstalled/upgraded etc

---

