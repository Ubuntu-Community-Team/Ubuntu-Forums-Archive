---
title: "Acer Aspire 4253 / eMachines D644"
date: 2011-06-27
forum: Hardware
---

### Post by bossdak on 2011-06-27
hi,

i have this laptop (d644 variant) and needs some help particularly on sound, usb and lock screen. I can't find any thread specific to this model so i created one.

this is the spec.
[http://support.gateway.com/us/en/emachines/notebook/2011/eMachines/emd/emd644/emd644nv.shtml](http://support.gateway.com/us/en/emachines/notebook/2011/eMachines/emd/emd644/emd644nv.shtml)

[http://support.acer.com/us/en/acerpanam/notebook/2011/Acer/Aspire/Aspire4253/Aspire4253nv.shtml](http://support.acer.com/us/en/acerpanam/notebook/2011/Acer/Aspire/Aspire4253/Aspire4253nv.shtml)

this is an amd e-350 based laptop. i have installed 10.10 64bit on it. i have also updated it.

-graphics works after installing drivers from ati website
-wifi (bcm43225 variant) works after installing proprietary broadcom drivers
-ethernet (Atheros Communications Device [1969:1083]) does not work. driver from atheros does not compile. just followed the readme, i'm not expert on this so there might be a workaround on this. i seldom use ethernet so i can just leave it as is for now.
-sound works but jack sensing does not work. you always get sound from both speaker and headphones.
-card reader works.

this is what i need help for. 
lock screen:
when i lock the screen and close the lid then open it, the display would not come up and after typing in the password and then hitting the power button, it would not shutdown (power button set to shutdown when pressed). i have to press the power button continuously to force shutdown it.

if i lock the screen and move the mouse such that the password prompt would appear then close and open the lid, the display would come back up.

i tried looking in the logs but i have no idea what to look for.

sound:
jack sensing does not work. sound always comes from speaker and headphones. tried the workaround for acer aod522 but it did not work for me or i have done it wrong.

usb:
sometimes it just stops working randomly.

thanks in advance for helping

---

### Post by bossdak on 2011-11-30
kernel 3.+ solved the jack sensing problems.
installed 11.10 but i did not like the ui so i installed 10.10 and installed kernel 3.+ but the broadcom drivers won't compile with the 3.+ kernel. so now i'm looking at another distro that has kernel 3.+ and doesn't use gnome 3/unity.

---

### Post by MoreOrLess on 2011-11-30
You can try Lucid (or Maverick, though support ends in April) and using the 2.6.x  kernel with updated audio modules: [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+packages](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+packages)

Debian Squeeze/6.x is another candidate if you like Gnome2.
Linux Mint 12 takes Gnome3 and customizes it to look/behave more like Gnome2.

---

### Post by Perfect Storm on 2011-11-30
> **bossdak said:**
> kernel 3.+ solved the jack sensing problems.
installed 11.10 but i did not like the ui so i installed 10.10 and installed kernel 3.+ but the broadcom drivers won't compile with the 3.+ kernel. so now i'm looking at another distro that has kernel 3.+ and doesn't use gnome 3/unity.

You could try Gnome Shell, it only takes a couple of packages and MB.
```
sudo apt-get install gnome-shell gnome-tweak-tool gnome-sushi gnome-contacts
```

logout, and then choose 'Gnome' before login.

---

