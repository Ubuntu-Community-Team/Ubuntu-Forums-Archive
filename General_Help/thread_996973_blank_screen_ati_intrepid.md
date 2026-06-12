---
title: "blank screen ati intrepid"
date: 2008-11-29
forum: General Help
---

### Post by toxic76 on 2008-11-29
After downloading some kernel updates released on friday
my screen turn black after reboot. I tried to reinstall 
fglrx for ati from root terminal in recovery mode since
try to fix xserver did not work..The only problem is that
apt-get install fails. No acess to internet what to do ?
Before intrepid i could reconfigure my xserver and select
veasa and get into gnome. But now i feel limited

---

### Post by radox1912 on 2008-11-29
i have this problem too(ati, kernel update). dont know how to solve it yet, but you can always boot the older kernel in your GRUB.
:) btw i think we

---

### Post by radox1912 on 2008-11-29
i have this problem too(ati, kernel update). dont know how to solve it yet, but you can always boot the older kernel in your GRUB.
:) btw i think we should wait for further updates

---

### Post by toxic76 on 2008-11-29
not sure if the option to boot older kernel works for
me since i have done some things to my system like
completly removed fglrx drivers (can not get them back)
apt-get fails.. Also i have no backup of xorg.conf
i was so sure that what i did should work since it helped
me once before when i upgraded from hardy i had the same
problem.. Using my vista computer right now and it sucks

---

### Post by toxic76 on 2008-11-30
radox1912 try this sudo aticonfig --initial -f
then sudo reboot i think that should be enough to do
the trick. If not then you should do the whole procedure
removing the drivers and then reinstall them 

to remove drivers manually:

sudo apt-get remove linux-restricted-modules-generic
sudo apt-get remove xorg-driver-fglrx

then to reinstall:

sudo apt-get install linux-restricted-modules-generic
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial -f
sudo reboot 

note before removing the drivers check if you have
internet connection while in root shell if not then 
download the packages and save them and install with dpkg
i had to download files in windows and then copy them to usb stick then mount it in terminal

---

### Post by toxic76 on 2008-11-30
can some one change the topic to [solved] or something ?
not sure how it's done here. But in the swedish ubuntu
forums we mark threads [solved] when the problem is solved

---

