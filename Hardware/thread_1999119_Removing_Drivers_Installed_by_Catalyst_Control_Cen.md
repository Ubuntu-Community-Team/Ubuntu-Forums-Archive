---
title: "Removing Drivers Installed by Catalyst Control Center 12.4"
date: 2012-06-07
forum: Hardware
---

### Post by ads2996 on 2012-06-07
Hi

I installed catalyst control center 12.4 using the .run file. That worked fine but i noticed it would load or allow me to drag windows around workspaces. So i tried uninstalling something cant remember what though. Then after a reboot unity would load after login. But i installed gnome using command prompt and it worked fine. But unity is still broke. I am looking for a way to completly remove the drivers and replace them with the open source drivers.

Thanks in advance

---

### Post by Redblade20XX on 2012-06-07
Take a look here : [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

### Post by typhoon_tip on 2012-06-07
Do **exactly** the below before attempting anything else, each and every step must be exact ! Be very careful of the command variation for 64 and 32 bits !

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati

```

**Only for UBUNTU 32 bits**
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

**Only for UBUNTU 64 bits**
```
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core

```

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati

```

Restart the system.

Now you can either use the system as it is (open source driver) or install any AMD driver (from Additional Drivers or from AMD website, with the indicated procedure in the Wiki).

Cheers

---

### Post by QIII on 2012-06-07
I'm not really sure why Ubuntu users go through such obscure or complex measures to install ATI drivers.

AMD and Ubuntu are in bed together, folks.

I'll be adding to the wiki shortly.  This is dead easy.

---

### Post by typhoon_tip on 2012-06-08
> **QIII said:**
> This is dead easy.

... and also a quite stable procedure, I have tested a million times over many different machines, one can even write a batch on it and it just works !

---

### Post by ads2996 on 2012-06-08
I got it sorted thanks for all ur help

---

### Post by seansplayin on 2013-01-31
I followed the instructions for uninstalling as listed above and I just got finished after spending 6 hours trying to get my ubuntu to boot again. I wish I knew exactly which command I entered into the terminal that producted and error but I'm not really sure. Anyhow I rebooted my computer to a blank screen (monitor not syncing).  be verrrrryyyyy careful.

---

### Post by ads2996 on 2013-02-16
Sorry to hear about that happening, are you using a laptop or desktop.

---

