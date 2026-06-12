---
title: "a few problems"
date: 2008-08-31
forum: General Help
---

### Post by squall321 on 2008-08-31
just installed.. bad resolution. stuck at 800x600, so i searched through the forums to see the amazing amount of fixes. non of them worked what so ever.. It got to the stage of me trying to find the horizontal and vertical stuff. in xorg.conf these are missing. My monitor is a Hanns G HSG1027 is the model number btu for some reason i cant find the damn details i need. the nvidia drivers dont work either. Really dont no what the hell im doing wrong either.

Tried envy drivers but they borked my res to 640xetc disabled them. now its 800x600..

Specs:

card: 7600GT 256mb
CPU: 3.0ghz P4 HT
Ram: 2gB

---

### Post by falcon61102 on 2008-08-31
Try going to System>Administration>Hardware Drivers and enabling the Restricted Drivers for your card if you haven't done so already.

A note with Envy and the nvidia drivers, it's not like windows where once you install them and restart, your resolution is fixed.  Here you still need to tweek them a bit.  You can use nvidia-settings to accomplish this.  To run use:
```
sudo nvidia-settings
```

If it gives you an error about not being installed then you can install them either through the Synaptic Package Manager or this should do it too:
```
sudo apt-get nvidia-settings
```

---

### Post by DemonBob on 2008-08-31
When you tried envy do you do an uninstall first then reboot? Then try to use envy to install again, then reboot? 

Sometimes if you use the Hardware Drivers and enable Nvidia, then try to use envy it screws up. So i would use envy to uninstall reboot install reboot.

---

### Post by squall321 on 2008-08-31
tbh with you i dont no what ive done. i tried a few things and rebooted and it asked me to configure my monitor cause it was running in low graphics mode or something. so i checked around there and it also didnt have my monitor. 

how can i start a fresh completely and start from the beginning? i dont mean uninstall ubuntu

Ok i removed everything that was named nvidia lol. and i got my resolution sorted... go figure. now i dont have a nvidia driver.. i can seriously see me installing oen and having thsi problem again..

---

### Post by squall321 on 2008-09-01
Yea nothing is working now.. got resolution but none of  the drivers are working.. i think i rmeoved something i should have. 

how can i get a fresh start without reinstalling ubuntu ?

---

### Post by falcon61102 on 2008-09-01
You can uninstall any drivers that Envy installed through Envy and then if you uncheck the Enabled box in Hardware Drivers, that should bring you back to pretty much where you started.

---

### Post by squall321 on 2008-09-01
i tried that.. now i dont get any drivers when i try to install them.. its weird.. ah well il reinstall ubuntu today. see if that fixes it. but one thing.. when i get back to normal i get started with a nvidia restricted driver.. with that i still cant change resolution.. is there anyway i can keep the restricted driver but get my resolutions back up again ?

---

### Post by falcon61102 on 2008-09-01
If you are going to reinstall Ubuntu this is what I suggest and I just did it on my a new install I'm working on now.  Once you get Ubuntu installed, get your internet working.  Install Envyng-gtk and then reboot as it will ask.  Don't touch your Hardware Drivers part yet.  Once you reboot, load up Envy and select Automatically Detect hardware.  Let it run through it's process and at the end it will ask you to reboot again.  Complete the reboot and you should be looking at a beautiful high res login screen when it starts up.  If, at that point you are still having issues, then you can start playing with the Hardware Drivers part.

---

