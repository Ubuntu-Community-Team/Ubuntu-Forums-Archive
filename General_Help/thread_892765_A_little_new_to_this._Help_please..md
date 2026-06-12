---
title: "A little new to this. Help please."
date: 2008-08-17
forum: General Help
---

### Post by beachedwahle on 2008-08-17
I am a little lost. I am trying to learn linux and am new to it. I love it.
I want to install Compiz-Fusion but I don't know how. I'm not really up on my linux command line stuff yet. If anyone could help me out it would be greatly appreciated. Or if anyone has any better suggestions. I'm using a persistant bootable linux distro hardy heron (8.04) on a 2GB USB Drive.

:confused:](*,)

---

### Post by Stemp on 2008-08-17
If you have Hardy Heron then Compiz-Fusion is already installed.
Depending on the video card you are using, evrything should work with :
Go to System -> Preferences -> Desktop Effects and click 'Enable Desktop Effects'

---

### Post by UbuntuNerd on 2008-08-17
[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/](http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/)

---

### Post by beachedwahle on 2008-08-17
> **Stemp said:**
> If you have Hardy Heron then Compiz-Fusion is already installed.
Depending on the video card you are using, evrything should work with :
Go to System -> Preferences -> Desktop Effects and click 'Enable Desktop Effects'

I don't have a Desktop Effects option in that drop down.  I have an appearance option. But when I click that and go to visual effects and choose normal or extra it says desktop effects could not be enabled.:confused:

---

### Post by Genius314 on 2008-08-17
> **beachedwahle said:**
> I don't have a Desktop Effects option in that drop down.  I have an appearance option. But when I click that and go to visual effects and choose normal or extra it says desktop effects could not be enabled.:confused:

Try going to System>Administration>Hardware Drivers (you'll have to type in your password). If you see a driver there for your video card that says "not in use", then enable it. Reboot, and try enabling the normal or extra effects again.

---

### Post by beachedwahle on 2008-08-17
> **Genius314 said:**
> Try going to System>Administration>Hardware Drivers (you'll have to type in your password). If you see a driver there for your video card that says "not in use", then enable it. Reboot, and try enabling the normal or extra effects again.

The only driver I have there is a broadcom wireless chip driver. Its the only one on the list. I have an ATI Radeon xpress1100 if that makes any difference. 


BTW. Thanks for trying to help me out everyone.

---

### Post by Stemp on 2008-08-18
That's pretty weird, your card is listed as supported in the fglrx driver (the ATI proprietary driver).
So Hardware Drivers should give you this option.
Maybe you should take a look at EnvyNG : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by beachedwahle on 2008-08-18
I found this page 

[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)

I think it might be what I need. I'm just not sure if I can do it all in the terminal. 

I tried that EnvyNG but when I used the command:
sudo apt-get install envyng-gtk

It said that the package couldnt be found.

---

### Post by Bart_D on 2008-08-18
TRY THIS AT YOU OWN RISK............BACK UP ALL IMPORTANT DATA NOW!!!

After a quick 2 minute search on GOOGLE, I came up with this:

[http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/](http://www.pendrivelinux.com/2007/11/04/usb-pendrive-linux-install-from-windows/)

IMPORTANT NOTE:  I haven't tried this because I am not running Ubuntu from a USB drive so if you have questions you should direct them to the folks on that site.  I just searched for the a few key words describing your problem and found that link::::::I Cannot answer your squestions.

---

### Post by beachedwahle on 2008-08-19
That did not help. Thanks though. This is frusterating. Why won't my graphics card get recognized

---

