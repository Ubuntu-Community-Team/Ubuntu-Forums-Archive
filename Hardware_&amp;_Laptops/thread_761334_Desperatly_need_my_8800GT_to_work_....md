---
title: "Desperatly need my 8800GT to work ..."
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by TwiStEr55 on 2008-04-21
Ok, I got myself a new 8800GT and I cant get it to work.

I have now, used every method I have found.

I first used Gutsy and now do everything in Hardy RC (because it has a better recovery mode and a working 2d driver)

First thing I tried, was installing the driver through the restricted manager. It Automatically installed "nvidia-glx-new". After the reboot I got, what Id like to call "BLACK screen of death". The system boots up completly, but when gdm is starting my screen goes black and says digital power saving mode.

This is the exact thing I get no matter what method I have used to install the driver and not matter if gutsy or hardy.

I used the repos, I used Envy and I used the NVIDIA binary. I already tried the 2 17x.xx beta versions of nvidia ... same result. 

The card works flwlessly in XP and after reading somewhere it is an ubuntu thing I downloaded Opensuse 10.3 yesterday and installed it on a small partition Im using for testing. And indeed my card works there with the 169.12 drivers.

Im out of ideas and out of solutions I could find in the net and here. PLEASE help me.
I dont want to switch to another distro, I like my ubuntu especially my new glory hardy ....

---

### Post by jbeynon on 2008-04-21
[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

these worked for me with my 8600 GT

---

### Post by TwiStEr55 on 2008-04-21
I ve already tried the new driver versions ... same result. As said the "old" stable drivers 169.12 work for me under SUSE but not with ubuntu.

Anyone?

---

### Post by TwiStEr55 on 2008-04-22
Does anyone have an idea as to why i cant get it to work especially with ubuntu? ... It doesnt seem to be a driver issue exactly. 

To get it to run in SUSE i used the nvidia repo. I think it gets a precompiled kernel module from there. 
Also weird is the fact, that whenever I get this black screen of death ... the system totally freezes ... strg+alt+F1 or something like that has no result ... strg+alt+del neither. I have to hit the reset button. This always happens, when the driver seems to be properly installed, whether it is after evny did the install, nvifia-glx-new or did it manually with the binary ... i dont know what else to try ... I cant be the onloy one with this problem can I? ... Its an MSI card and its overclocked by default (not much)

thanks, Matt

---

### Post by krajator on 2008-04-25
I've got the exact same problem on my dell notebook with nvidia 8400gs since drivers 100.xx (I think 100.14 but I can't say for sure). I tried few other ubuntu-based distros (eg. mint and mepis) and the problem was still there. I managed to get it working once with envy but I think it's because it installed some old version of the drivers.

---

### Post by TwiStEr55 on 2008-04-28
ok I got rid of the black screen of death by adding "nvidia_new" to  /ec/default/linux-.....-blacklist-common

but the nvidia driver still doesnt load, but at least my system doesnt freeze anymore. 

I really dont know what to do anymore ... help :(

---

