---
title: "No Sound on Asus Eee PC Seashell 1005BX"
date: 2013-10-21
forum: Hardware
---

### Post by mabigonion on 2013-10-21
Hallo

I recently tried to install LUbuntu 13.10 Saucy on an ASUS Seashell 1005BX Notebook PC. Everything went well except the Sound, I had no sound and after doing various checks it was apparent that no Pulse Audio could be installed. I then tried XUbuntu and it worked, XUbuntu identified the sound system Realtek and I can watch films with Sound.

I would prefer LUbuntu as it is very fast on this computer, does anyone have a solution to the problem ?

Thanks in advance

---

### Post by mörgæs on 2013-10-21
You can add the Lubuntu desktop environment by 
```

sudo apt-get install lubuntu-desktop
```

This will allow you to choose between desktops during boot.

---

### Post by mabigonion on 2013-10-21
Please excuse my ignorance, during Boot will I land in a Menu-Option which allows me to select the Desktop or must I add an Option Sting to the boot command in Grub? That would be somewhat complex, so I would expect an Option-Menu - am I right ?

Thanks for your prompt answer

---

### Post by mörgæs on 2013-10-21
It will be a menu point close to when you enter user name and password. No changes in Grub.

---

### Post by dentaku65 on 2013-10-23
Hi,

create/edit 
```
sudo nano /etc/asound.conf 
```
Then paste this:
> pcm.!default {
    type hw
    card Generic_1
}
ctl.!default {
    type hw
    card Generic_1
} 

Save. Reboot

---

