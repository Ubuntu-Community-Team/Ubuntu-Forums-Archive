---
title: "Help with Installation"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by want2ubu on 2009-03-24
I am new to ubuntu and am having a very difficult time installing Ubuntu. When I boot from a Live-CD, it frezzes. When  I was able to get the semi-graphic installation panel, it frezzes during installation (8.10). Is there 

1. a place I can install Ubuntu over the internet? 
2. a way to install it from an external usb HD easily?

I am trying to install the 64 bit version of Ubuntu on a blank (yes, no other OS and nothing else) internal hard drive. My other computers are all 32 bit. 

Thanks for your help in advance.

---

### Post by x33a on 2009-03-24
you can try a live usb, if you think that the problem has something to do with the cd drive.

[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

you can create a live usb from windows and then use that to install ubuntu.

---

### Post by spcwingo on 2009-03-25
You can boot with the mini CD to install.  This only a ~9.5MB iso.  It only has enough to boot the system, so if the CD drive is failing this will do minimal CD drive reading because it will pull in everything else to install from the repos.  The mini CD iso can be found here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

After the install and reboot you will only have a command line system.  Log in (you won't see "*" when typing your password, this is normal) and type one command:

```
sudo apt-get install ubuntu-desktop
```

Enter your password when prompted.  When that finishes (it might take a while) type:

```
sudo apt-get clean && sudo reboot
```

This will clean the apt cache and reboot into your new Ubuntu system.  :)

I have used this method on systems where Ubuntu refuses to install because of a failing CD drive.

---

### Post by deeinmetrodc on 2009-03-25
that's a great idea.... how could i do that on a system with a broadcom wifi requiring the non-free drivers that i have d/l'd and stored on a flashdrive?

---

### Post by spcwingo on 2009-03-25
> **deeinmetrodc said:**
> that's a great idea.... how could i do that on a system with a broadcom wifi requiring the non-free drivers that i have d/l'd and stored on a flashdrive?

Ditch the broadcom card for one that is natively supported.  :wink:

---

### Post by Roque2 on 2009-03-25
Lol too funny

---

