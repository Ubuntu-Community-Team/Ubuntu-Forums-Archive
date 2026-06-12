---
title: "Asus xonar ds dual boot crackling sound"
date: 2010-11-26
forum: Hardware
---

### Post by henners91 on 2010-11-26
Hi all
   I've installed 64 bit ubuntu on my windows 7 32 bit desktop pc. All works great, it's super fast, only problem is that if i boot into ubuntu and then turn off pc and boot into windows all my sound is crackling loads, it's unlistenable. it will work again in windows if i remove the sound card for a few mins and reinstall it but this is completely impractical obviously.
 Is there any way to fix this? i really don't want to go back to on-board audio for my ubuntu install as i use sennheisser HD555's and they sound dreadful on-board compared to sound card.
 Thanks for any help given!

---

### Post by n0fxk03 on 2011-01-23
ASUS Xonar DS audio device
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
>>sudo /sbin/alsa-utils stop
>>sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
>>sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev
>>cd ~
>>rm -rf ~/alsa* ~/.pulse*
>>wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
>>wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2)
>>wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2)
>>sudo rm -rf /usr/src/alsa
>>sudo mkdir -p /usr/src/alsa
>>cd /usr/src/alsa
>>sudo cp ~/alsa* .
>>sudo tar xjf alsa-driver*
>>sudo tar xjf alsa-lib*
>>sudo tar xjf alsa-utils*
>>cd alsa-driver*
>>sudo ./configure
>sudo make
utils/link-modules /usr/src/alsa/alsa-driver-1.0.23
ALSA modules were successfully compiled.
[EMAIL="peter@ubuntu:/usr/src/alsa/alsa-driver-1.0.23$"]peter@ubuntu:/usr/src/alsa/alsa-driver-1.0.23$[/EMAIL] 
>>sudo make install

/////  Dual boot issue Asus xonar ds dual boot crackling sound 
[http://ubuntuforums.org/showthread.php?t=1631405](http://ubuntuforums.org/showthread.php?t=1631405)
Hi all
I've installed 64 bit ubuntu on my windows 7 32 bit desktop pc. All works great, it's super fast, only problem is that if i boot into ubuntu and then turn off pc and boot into windows all my sound is crackling loads, it's unlistenable. it will work again in windows if i remove the sound card for a few mins and reinstall it but this is completely impractical obviously.
Is there any way to fix this? i really don't want to go back to on-board audio for my ubuntu install as i use sennheisser HD555's and they sound dreadful on-board compared to sound card.
Thanks for any help given!
 
solution
[http://tweakers.net/productreview/26889/asus-xonar-ds.html](http://tweakers.net/productreview/26889/asus-xonar-ds.html)
Als laatste nog even de aandacht voor een dual-boot bug: Als je vannuit Linux reboot naar windows, 
dan is de geluidskwaliteit waardeloos. Een shutdown en een handmatige start werkt wel prima. 
Blijkbaar word het EEPROM niet goed gereset (door beiden drivers niet). Ook dit hopen we op te lossen.
Update: 
Na een samenwerking tussen mij en de driver-programmer is de dual-boot bug opgelost. 
Ook is er nu front-panel support en is de stereo-upmixing verbeterd (center en sub worden nu ook gebruikt). Check deze link voor installatie-instructies:
[http://ubuntuforums.org/showpost.php?p=9816705&postcount=9](http://ubuntuforums.org/showpost.php?p=9816705&postcount=9)
dualboot fix
 
 
//peter@ubuntu:/usr/src/alsa/alsa-driver-1.0.23$  
 
Step 2: Now copy the files to their place. The files are attached in an archive.
Kconfig                         
virtuoso.c
oxygen.h                        
oxygen_lib.c                    
xonar_wm87x6.c

Kconfig must be copied into 
/usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/ and
the other files cd /usr/src/alsamust be copied into 
/usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/.
>>sudo cp virtuoso.c /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/
>>sudo cp oxygen.h /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/
>>sudo cp oxygen_lib.c  /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/
>>sudo cp xonar_wm87x6.c /usr/src/alsa/alsa-driver-1.0.23/alsa-kernel/pci/oxygen/
>>cd /usr/src/alsa
>>cd alsa-driver*
 
>>sudo ./configure
>sudo make
//ALSA modules were successfully compiled.
//peter@ubuntu:/usr/src/alsa/alsa-driver-1.0.23$ 

>>sudo make install
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---

### Post by Ranger21 on 2011-02-09
I must say that, Fix doesn't work with new kernels!
I Simply recommend you to turn off Linux with Shutdown and your sound will be fine.
Im using dual boot too, and just shutdown linux, not restarting...
Well there's also a problem that front-panel mic doesn't work and you will have sound both from front-panel + from backpanel.

---

