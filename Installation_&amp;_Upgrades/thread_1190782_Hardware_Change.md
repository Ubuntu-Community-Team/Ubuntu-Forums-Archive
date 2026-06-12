---
title: "Hardware Change"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by bmalpas on 2009-06-18
I had Ubuntu 9.04 installed, had to change graphics card to a ATI Asus 2600 Pro AGP, when i boot up now i get same symptoms as user here.

[https://answers.launchpad.net/ubuntu/+question/73783](https://answers.launchpad.net/ubuntu/+question/73783)

I have booted into the live cd with same issue, it boots to ubuntu and i can "ctrl + alt + f1" to get to command line but as i am noob at linux not sure what i can do to fix it.

any help would be appreciated :)

---

### Post by masux594 on 2009-06-18
to resolve the Ati BlackScreenOfDeath uninstall the ati catalyst that i suppose u have installed..
```
sudo apt-get remove fglrx-amdcccle fglrx-kernel-$(uname -r) fglrx-kernel-source xorg-driver-fglrx
```
now, reboot 
```
sudo reboot
```
.. when the computer starts, your GUI will return the same as ever, without graphic acceleration..

Sysc, A

---

### Post by bmalpas on 2009-06-19
> **masux594 said:**
> to resolve the Ati BlackScreenOfDeath uninstall the ati catalyst that i suppose u have installed..
```
sudo apt-get remove fglrx-amdcccle fglrx-kernel-$(uname -r) fglrx-kernel-source xorg-driver-fglrx
```now, reboot 
```
sudo reboot
```.. when the computer starts, your GUI will return the same as ever, without graphic acceleration..

Sysc, A


Hi Thanks for the reply i have tried this but it didnt work it said that there were none installed and that the package couldnt be found.

When it loads to what would normally be the login screen it goes all pixelated and uncoeven with parts of the b ios screen showing

---

### Post by masux594 on 2009-06-20
before upgrading.. did you had installed the catalyst?

Sysc, A

---

