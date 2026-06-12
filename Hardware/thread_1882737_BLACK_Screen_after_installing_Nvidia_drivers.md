---
title: "BLACK Screen after installing Nvidia drivers"
date: 2011-11-17
forum: Hardware
---

### Post by bulldoors on 2011-11-17
Hi, im using Ubuntu 10.04 LTS. I have a lot of stuff on there, from class and so on.
Im quite new to Ubuntu. I wanted to play some games. I noticed a really  poor performance on 3D games, and I realized the nVidia card was not  being used because the driver was not installed. I have a GT540M on my laptop. So I went to System->Administration->Additional Drivers and the nVidia driver was found as missing and ready to install, so I clicked and waited for it to install. When it was done I closed the window and restarted. When I tried to boot up, I only got a black screen with "Ubuntu Login", I logged in, tried that "sudo gdm service restart" cvar and still no GUI. Then I decided to uninstall the nVidia drivers with sudo apt-get *purge nvidia* and then sudo reboot. This time I didn't even had the "Ubuntu Login" thing, it was jut black. To access the Ubuntu Login again I had to press F6 while I see the Ubuntu loading logo for a couple of seconds before it goes just black. Or also with the Recovery Mode. In the Recovery Mode I tried the check for damaged packs options or something like that and still didn't work.

More stuff i've tried:

Pressing "e" to access the grub thing and change the "quiet splash" for "nomodeset" then pressing CTRL+X. I did this, and after pressing CTRL+X a shitload of words appear like if it was loading, but then I go back to the "Ubuntu Login" black screen. If I press "e" again and check the grub, the "quiet splash" line is still there and not "nomodeset".



When I tried to boot up, my screen went black. I see the Ubuntu logo for some seconds, then it's all black and nothing happens. Im not sure if it's actually loading because I had my sound on mute. Also I don't see any HD activity when it goes black.


I also installed laptop-mode-tools trying to fix the annoying famous "hard disk clicking" noise after rebooting after installing the nVidia drivers but I guess this has nothing to do with it. I also uninstalled the laptop mode tools and same happens anyway.

Wtf guys? I just wanted to play a bit in Ubuntu, and wasted all nite trying to fix this. Now I can't study or do anything school linux related. It's sad to aknowledge I would have done this in Win7 with 0 problems :(

Hope I get a solution, because i see myself having to install everything again :(

---

### Post by bulldoors on 2011-11-18
Cmon guys this is really urgent.

---

### Post by BillyBoa on 2011-11-18
All you could do is here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by seenthelite on 2011-11-18
What you have is nvidia optimus installed which requires a lot of configuration in linux. 
Some information on the situation with linux 

[http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus)
[http://www.phoronix.com/scan.php?pag...item&px=OTQxNg](http://www.phoronix.com/scan.php?pag...item&px=OTQxNg)

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

[http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus)

---

### Post by bulldoors on 2011-11-19
> **BillyBoa said:**
> All you could do is here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

How can I do any of that If im just on a black screen with the terminal?

---

### Post by bulldoors on 2011-11-19
> **seenthelite said:**
> What you have is nvidia optimus installed which requires a lot of configuration in linux. 
Some information on the situation with linux 

[http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus)
[http://www.phoronix.com/scan.php?pag...item&px=OTQxNg](http://www.phoronix.com/scan.php?pag...item&px=OTQxNg)

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

[http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1757821&page=5&highlight=optimus)

Oh god. Im just going to reinstall and never attempt to play anything 3D on Ubuntu again.

---

### Post by Dlambert on 2011-11-19
Fall back to recovery mode, hold shift on startup to reveal the grub menu, or try a distro like sabayon with drivers built in.

---

### Post by bulldoors on 2011-11-19
> **Dlambert said:**
> Fall back to recovery mode, hold shift on startup to reveal the grub menu, or try a distro like sabayon with drivers built in.

Yeah, and what do I do on the grub menu?

---

### Post by Dlambert on 2011-11-19
Isn't there recovery mode option?

---

### Post by bulldoors on 2011-12-06
OK so i had to format and reinstall after all. Sight

How do I install the drivers for my nVidia 540M in a away that the OS doesn't dies at the attempt?

---

