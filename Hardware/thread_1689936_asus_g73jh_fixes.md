---
title: "asus g73jh* fixes"
date: 2011-02-17
forum: Hardware
---

### Post by kezeb on 2011-02-17
I bought an Asus G73jh* last year and I realized that there was no info on certain things such as the keyboard backlight and getting rid of the tearing when playing video or with the Compiz effects enabled so I just decided to give you a few hints:

first the most anoying thing the video tearing:

download the prop. drivers that's if you have the ATI 58XX [here]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run") that's the latest driver they offer, and run " aticonfig --initial " after that restart your computer or the windows server gdm or kdm. Although it is not officially supported you can enable Tear free desktop by running this " aticonfig --set-pcs-u32=DDX,EnableTearFreeDesktop,1 " and once again restart the windows server or the computer. 

after that you can add the following ppa to your /etc/apt/sources.list 

" deb [http://ppa.launchpad.net/flozz/flozz/ubuntu](http://ppa.launchpad.net/flozz/flozz/ubuntu) maverick main "
" deb-src [http://ppa.launchpad.net/flozz/flozz/ubuntu](http://ppa.launchpad.net/flozz/flozz/ubuntu) maverick main "

and then you can install the keyboard backlight deal that will let you control the brightness " sudo apt-get install asus-kbd-backlight "
" sudo apt-get install alsa-tray " " sudo apt-get install cover-thumbnailer" I'm running kubuntu so you may need the rest of the packages listed in the ppa.


There's only one thing that pisses me off still and it's the not being able to suspend or hibernate I've tried unbinding my bus and USB 3.0, but still can't get the hibernate and suspend to work, i hope that you can and let me know if that's the case!!!!!

---

### Post by Ulix on 2011-04-05
Duude, Thanks for the info, I have one(Asus G73jh) but I was un aware of the limitation installing Ubuntu, I guest I'm Stuck with Windows until further notice,

---

### Post by kezeb on 2011-04-19
any day du'!!!

---

