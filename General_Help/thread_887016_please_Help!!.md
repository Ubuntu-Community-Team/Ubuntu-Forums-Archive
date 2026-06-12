---
title: "please Help?!!"
date: 2008-08-11
forum: General Help
---

### Post by UndeadAlex on 2008-08-11
gah idk what i did.
i just want to know if there's anyway to like restore ubuntu
back to like what it was when i first installed it.
or like if theres a way to reset all the packages to default or something along those lines?
the thing is my crazed father ripped the cd drive out of my laptop or else i would reinstall.
see what happened, is the stupid flash player thing is pissing me off.
ive done it many times but now nothings working
yeah im using hardy
and yes its the flash for firefox.
i've tried flashpluginnonfree and everything else
also, now i get an error when installing the flashplugin.
 this is what it is
"E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1"

:(

---

### Post by dacorr on 2008-08-11
try the live CD

---

### Post by Vadi on 2008-08-11
What exactly is wrong? You can reinstall a specific package (I don't know how to reinstall all packages).

---

### Post by mfaust731 on 2008-08-11
well, it wont be much help now, but you can back up the whole OS with a tar command and restore it pretty easily

to make a backup this would do it
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /


then you could restore it with

 tar xvpfz backup.tgz -C /

i usually make a backup of my wifes laptop every couple of months

---

### Post by Dylock on 2008-08-11
1) You said everything is not working, is the system not booting? Or does flash just not work? 

2) I'm assuming you want to use flash in firefox? Did you install the flashplugin-nonfree package from synaptic? Can you explain what you have done to try and get flash working

3) What version of ubuntu are you using?

---

