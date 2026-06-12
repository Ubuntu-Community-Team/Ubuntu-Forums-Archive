---
title: "Installed new video card"
date: 2009-08-09
forum: Hardware
---

### Post by windowsmademecrazy on 2009-08-09
So i installed a new video card and went to nVIdia for drivers as i searched on google and said to go there once i get it on my desktop and install it like nvidia tells me to, this is what it does: 
thomas@thomas-desktop:~$ sh NVIDIA-Linux-x86-185.18.31.pkg1.run
sh: Can't open NVIDIA-Linux-x86-185.18.31.pkg1.run
thomas@thomas-desktop:~$ 

Says it cannot open it, the driver says for linux in general and people have said they installed it properly any reasons to why it cant open it? As well im a large nub to ubuntu, well installing external drivers that is. btw my card is a Nvidia 9500GT ive read lots but nothing on how its not installing correctly, :guitar:, and i hope i put this in the right place, if not crap.

---

### Post by overdrank on 2009-08-09
> **windowsmademecrazy said:**
> So i installed a new video card and went to nVIdia for drivers as i searched on google and said to go there once i get it on my desktop and install it like nvidia tells me to, this is what it does: 
thomas@thomas-desktop:~$ sh NVIDIA-Linux-x86-185.18.31.pkg1.run
sh: Can't open NVIDIA-Linux-x86-185.18.31.pkg1.run
thomas@thomas-desktop:~$ 

Says it cannot open it, the driver says for linux in general and people have said they installed it properly any reasons to why it cant open it? As well im a large nub to ubuntu, well installing external drivers that is. btw my card is a Nvidia 9500GT ive read lots but nothing on how its not installing correctly, :guitar:, and i hope i put this in the right place, if not crap.

Hi and you can use the ctrl, alt, F1 keys to reach the command line and login.
Then you will need to stop x
```
sudo /etc/init.d/gdm stop
```
Then cd ( changed directory ) to the location of the driver, which is usually the desktop.
```
 cd ~/Desktop
```
Then you can run the nvidia driver
```
sudo sh NVIDIA-Linux-x86-185.18.31.pkg1.run
```
The when complete reboot
```
sudo reboot
```
You may also receive a error for the installation of build-essential

---

### Post by windowsmademecrazy on 2009-08-09
what does stop x do it seems like its stuck on the black screen with the scrolling txt like upon start up etc.

---

### Post by windowsmademecrazy on 2009-08-09
Ok so i did all that to find out 

 ERROR: nvidia-installer must be run as root
what does it mean to be run as root and how do i do that.

k i forgot to put sudo infront xD other than that aparently i cant get x to stop.

---

### Post by overdrank on 2009-08-10
> **windowsmademecrazy said:**
> Ok so i did all that to find out 

 ERROR: nvidia-installer must be run as root
what does it mean to be run as root and how do i do that.

k i forgot to put sudo infront xD other than that aparently i cant get x to stop.

Sorry for the delay in response. Are you using Ubuntu or Kubuntu?

---

### Post by Deiu on 2009-08-12
> **overdrank said:**
> 
The when complete reboot
```
sudo reboot
```


Why reboot? You can just start gdm and it will work. The _only_ time when you should reboot Linux is after updating/installing the kernel. 

Don't mistake Linux for Windows. ;)

---

