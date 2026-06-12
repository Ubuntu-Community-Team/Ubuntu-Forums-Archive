---
title: "Conexant/Libc6/libc driver problems"
date: 2008-08-13
forum: General Help
---

### Post by ZeroRider13 on 2008-08-13
(copied and pasted)Im trying to get my internal Conexant to work. I got the first package listed on linuxant.com, and got an error dependency for alsa-linux-driver. I went back on linuxant and got the alsa-linux-driver.deb. When I tried to install this, I got an error dependency for libc6-dev. When I tried to install that, it gave me an error for "linux-libc-dev" I keep getting these erros, so is there anywhere I can get all the drivers I will need?  If I'll only need linux-libc-dev then please tell me where to get it.  Thanks alot.

---

### Post by DeathOnJuice on 2008-08-13
Install as many things as you can from Synaptic. Libc6-dev, for example, will be in there. It will take care of all dependencies.

---

### Post by rossjman1 on 2008-08-13
I used to have a Conexant Riptide sound card years ago, and the ones from that website you posted didn't work. I had to get the free version of oss ([http://www.opensound.com/](http://www.opensound.com/)). It's been a while, but I think you may have to compile it, and then run the command "soundon" to turn sound on and "soundoff" to turn it off.

---

### Post by ZeroRider13 on 2008-08-13
Death, I downloaded libc6-dev from the ubuntu site onto a flash drive and transferred everything but that had a dependency for linux-libc-dev.  I dont have an interent connection on that computer so I dont think I can dwnload from synaptic. 

Ross, hey, why would I need a sound thing for getting rid of lib dependencies and installing drivers for a modem?  Im not saying you;re wrong, im new to linux and you probably have it dead on, im just asking, thanks.

Will I keep running into depencies or is there a package I can download to help all of these?

---

### Post by DeathOnJuice on 2008-08-13
> **ZeroRider13 said:**
> Death, I downloaded libc6-dev from the ubuntu site onto a flash drive and transferred everything but that had a dependency for linux-libc-dev.  I dont have an interent connection on that computer so I dont think I can dwnload from synaptic. 

Ross, hey, why would I need a sound thing for getting rid of lib dependencies and installing drivers for a modem?  Im not saying you;re wrong, im new to linux and you probably have it dead on, im just asking, thanks.

Will I keep running into depencies or is there a package I can download to help all of these?

Ah, downloading a package with all of its dependencies. I was just struggling with this problem. There were several scripts and complex methods offered, but although this is dirty, it's easy.

Fire up a LiveCD, as it will have no extra packages installed. Install the packages you want without installing anything else first. Then, copy all .debs from the /var/cache/apt/archives directory to the flash drive. You could also make a download script in Synaptic instead of installing the packages, so that you could download these packages easily even on computers with them already installed. But this shouldn't be necessary for you.

---

