---
title: "Problems with nouveau driver"
date: 2015-03-06
forum: Hardware
---

### Post by Ramses_De_Vuyst on 2015-03-06
Hi there,
Recently i tried installing (l)ubuntu and i experienced some problems with the graphics card. I've tried Ubuntu, Xubuntu, Lubuntu and Mint.
The only linux distro i can run is for some reason Elementary OS. I'm guessing it uses some kind of different drivers. It uses a Ubuntu Raring kernel so i figured that shouldn't be the problem. I can't boot into any of the live cd's except for mint's compatability mode, because right after the loading screen (When you should see the desktop) it ****s up and i only get this image [http://imgur.com/L4FNVSe](http://imgur.com/L4FNVSe). I know it should have to do something with the nouveau drivers since when i try to install ubuntu it displays a random nouveau error: nouveau failed to idle channel [COLOR=#333333][FONT=monospace]0xcccc0000 / [/FONT][/COLOR][COLOR=#333333][FONT=monospace]0xcccc0001[/FONT][/COLOR]. This turned out to be a bug they won't be fixing any time soon. So my question actually was: Can i somehow boot into the lubuntu live cd using proprietary drivers?
Btw, my gpu is a GeForce 7500 LE.
Thanks in advance

---

### Post by kc1di on 2015-03-06
Hello Rameses_De_Vuyst and Welcome to Ubuntu,

There is a problem with the Nouveau driver, you will have to install the nvidia-current  driver to get your card working properly. 
First you need to boot in the nomodeset mode.
you can do that by hitting the tab key as the livecd starts to boot.  Then selecting F6 and select nomodeset > hit esc key and enter.  When the desktop comes up the resolution will not be right-- but you can do the install and when you reboot select advanced >recovery mode.  This will take you to a screen with several options select network and allow it to connect  you , when that is finished select root  sign in with your password.  on that line type the following ```
apt-get update
``` then ```
apt-get install nvidia-current
```
when it finishes installing type ```
shutdown -r now
```
the machine will reboot and you should be able to login to your desktop. 
good luck ;)

---

### Post by Ramses_De_Vuyst on 2015-03-06
Thanks for your input, but using nomodeset doesn't seem to work either. It still displays those black and white bars with yellow-ish pixels in the black bars. On Windows and Elementary OS i wasn't experiencing any problems. Would anyone have more suggestions for me to try? It should be possible to just create a live cd with those drivers built in but that would be more work than necessary (i hope). So basically i still can't boot into any form of gui except for the "Grub" part and the loading screen.

---

### Post by Ramses_De_Vuyst on 2015-03-07
> **kc1di said:**
> Hello Rameses_De_Vuyst and Welcome to Ubuntu,

There is a problem with the Nouveau driver, you will have to install the nvidia-current  driver to get your card working properly. 
First you need to boot in the nomodeset mode.
you can do that by hitting the tab key as the livecd starts to boot.  Then selecting F6 and select nomodeset > hit esc key and enter.  When the desktop comes up the resolution will not be right-- but you can do the install and when you reboot select advanced >recovery mode.  This will take you to a screen with several options select network and allow it to connect  you , when that is finished select root  sign in with your password.  on that line type the following ```
apt-get update
``` then ```
apt-get install nvidia-current
```
when it finishes installing type ```
shutdown -r now
```
the machine will reboot and you should be able to login to your desktop. 
good luck ;)
Anyone?

---

### Post by Ramses_De_Vuyst on 2015-05-07
Apparently i can boot into the gui on nomodeset running lubuntu 15.04, so i'm using that now. 
Thanks for your help :)

---

### Post by kc1di on 2015-05-07
With nouveau - you can also use the command ```
nouveau.noaccel=1
```

That works fine here.

---

