---
title: "Couldn't generate /etc/X11/Xorg.conf (SOS)"
date: 2010-02-11
forum: Hardware
---

### Post by gegadeath on 2010-02-11
Hi folks, 

I'm in big trouble, I have an intel graphics card and everything worked well untill I accidently installed a package called xserver-xorg-video-intel-dbg. the Xserver doesn't work any more and it says "couldn't generate /etc/X11/Xorg.conf..." Thanx in advance !

PS: my laptop is a compaq CQ60-120ES

---

### Post by hyde_78 on 2010-02-11
try the following:
1 restart your laptop into recovery model and login.
2 type these words in terminal:
#Xorg -configure 
it will generate a file named xorg.conf.new in HOME.
3 then
#cp xorg.conf.new /etc/X11/xorg.conf
4 restart

Maybe someone knows much more convenient way but I'am sure it's working.

---

### Post by gegadeath on 2010-02-11
Hi and thanks for the reply, I did what you told me but didn't fix the problem. a new configuration file was generated under the name "xorg.conf.new" then I moved it to /etc/X11/**xorg.conf** (I changed the name of course) but the Xserver still won't start. I wonder if there is a way to reinstall the Xserver anew. Thanks in advance !!

---

### Post by Satoru-san on 2010-02-11
> **gegadeath said:**
> Hi and thanks for the reply, I did what you told me but didn't fix the problem. a new configuration file was generated under the name "xorg.conf.new" then I moved it to /etc/X11/**xorg.conf** (I changed the name of course) but the Xserver still won't start. I wonder if there is a way to reinstall the Xserver anew. Thanks in advance !!

Reinstalling wont help in the least.

Do this

put in a usb drive. 

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
cd /mnt/usb
sudo dmesg > dmesg
sudo cat /var/log/Xorg.0.log > Xorg
cd ..
sudo umount usb
```

Plug the drive into the computer you are on now and post those logs in [code] tags please.

---

