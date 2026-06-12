---
title: "kernel 2.6.28-13 generic problem install nvidia"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by jelsa on 2009-06-21
I have updated to the newest kernel 2.6.28-13 using automatic update.

after installation is done then I reboot my machine, then there are dual boot kernel which are :
- 2.6.28-11-generic
- 2.6.28-13-generic

if I choose 2.6.28-11 there would be no problem but when I choose 2.6.28-13, a problem appears in my NVidia driver which is not supported in kernel 2.6.28-13. I have reinstalling using NVIDIA-Linux-x86-96.43.11-pkg1.run from NVidia website but it tells the kernel is not supported

Anybody has suggestion whether I have to erase 2.6.28-13 kernel or something else?

---

### Post by jelsa on 2009-06-22
No one care!

---

### Post by Chemical Imbalance on 2009-06-22
Do you have an older GPU?  You are using very old nvidia drivers...

---

### Post by running_rabbit07 on 2009-06-23
Check in System> Administration> Synaptic Package Manager while booted into the 2.6.28-13 kernal. Once there, in the quick search type NVIDIA then wait a second. In the list below there should be a program called nvidia-180-libvpau, if the box beside it is not colored green, you need to click it and mark for install. Once you mark for install click on the green apply button to the left of the quick search. After this is done installing restart your PC. Your screen quality should return to the way you had it with the old kernal.

If that nvidia program was already installed when you checked it, you should mark it for uninstall and then reinstall it.

If the above doesn't work, take notes of what actions you tried and post them on here with as much info as you can. The more info you give, the better our friends here will be able to help. Good luck.

One other thing you could do is go to the same search field in synaptic manager and search StartUp-Manager. It should be one of few programs listed underneath. Install it and then you can open startup-manager under the system- administraion menu. Under the Boot Options tab you can click on the scroll for Default Operating System and highlight the 2.6.28-13 kernal. I don't know if doing this will cause problems in the future with updates but it would keep you from being tempted to load the bad kernal and it will still show your microsoft boot loader upon powering up.

I am sure that if the first thing doesn't fix your problem some one here would walk you through uninstalling the bad kernal and reinstalling it. I personlly don't know how to uninstall kernals nor repair them.

---

### Post by jelsa on 2009-06-23
Thanks for the help.

I did install, delete, and reinstall the driver but all of them doesn't work, I gave up then I go to Synaptic Package Manager and search everything smell like 2.6.28-13 then delete them all.

in fact deleting these kernel will automatically delete boot loader menu for kernel 2.6.28-13. So I stay tune to kernel 2.6.28-11

---

### Post by systemgod on 2009-06-23
For what it's worth: my NVIDIA card (9800GT) works fine with kernel 2.6.28-13. Note I used the Ubuntu-supplied NVIDIA driver via System->Administration->Hardware drivers. I did not download the driver from the NVIDIA website myself. If you use the Ubuntu-supplied driver it will get upgraded automaticaly every time the kernel gets upgraded.

Nico

---

### Post by renkinjutsu on 2009-06-23
since you did a kernel update, it's no surprise that your video drivers are broken.. The module probably doesn't work for the new kernel

the reason you can't install the driver from nvidia's website is probably that you installed the new linux image without installing the linux headers

boot up the new kernel and ```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by jelsa on 2009-06-25
[renkinjutsu]("http://ubuntuforums.org/member.php?u=668873"):
 
Thanks for the support and I'll do your this installation procedure someday or perhaps I'll be waiting to the next kernel.

---

### Post by johnio on 2009-07-13
I am having a similar problem with the 2.6.28-13 using an older Nvidia Card (GeForce 3) using the recommended ubuntu supplied nvidia driver (version 96) . I experience crashes as soon as I try to log into gnome.  Booting using 2.6.28-11 works fine though.

---

