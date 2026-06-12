---
title: "problems with amd radeon hd 8xxxs series graphic card"
date: 2013-11-20
forum: Hardware
---

### Post by luciduci on 2013-11-20
Hi, i've bought Acer laptop e1-522 with AMD quad-core processor A4-500 (1.5Hz), and installed Ubuntu 12.04.3 LTS 64-bit.

I think, that i have problems with AMD Radeon HD 8330, couse my laptop doesn't work correctly.
I try update drivers from soft ware centre, manually from amd site, i try official manuals, non oficial,i think, that i try everything, but these all "experiments" haven't solved my problems :/  
 I've 3big problems: 
1.During restarting screen flashes, I mean it still flashes black and white stripes
2.I can't turn off laptop- when i try it, screen flashes like during restarting, after few seconds it stops flashing and processor looks as it has shut down, but screen already shows "clear" logo without flasing, but cursor isn't loading and it's only still turn on and led at start buttom lighting. 
3. i mean, that couse of problems with graphic card and drivers, processor can overheats during the demanding work with graphic/video editors 

now, i have installed drivers from instalation disc, and It does what I described above.

-after trying to update amd catalyst drivers, I always had to reinstall the system because nothing worked properly -terminal had black, ubuntu logo during shutdown also had a black background and I still have on screen flickered strips in the upper left corner next to the launcher, and in menu of additional drivers still writes installed but not activated, whatever I tried anything

-open drivers didn't work at all, ubuntu start in text mode 

At older (5-6years old) dual-core laptop i have ubuntu 12.04.3 32-bit, but except for a problem with switching off too and few corrections of hibernation and suspend mode it works good. But theese all I soved by fixes. 

/please exuse my english, i hope, that you understand what i mean :) /

---

### Post by heir4c on 2013-11-20
Try Ubuntu 13.10 because your card is very new. 13.10 uses the 3.11 Linux-kernel-version and support now the HD 8000 series (what I read on internet)

---

### Post by luciduci on 2013-11-21
Oh great! thanks :) i will try it

---

### Post by luciduci on 2013-11-22
i tried to do it, but after boot install CD, after violet ubuntu login screen, screen was white... i try both modes in UEFI. only try ubuntu and install ubuntu mode... can i have broken instalation disc ?

---

### Post by heir4c on 2013-11-22
Use the nomodeset on boot, see for that in the link:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
or shorter answer:
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)
or:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by luciduci on 2013-11-23
i tried to do it, but i have had only black grub with 4 options- try ubuntu, install, instal-for manufacturer and disk check... th  there aren't any advanced options, any tabs F2-F6 and commads didn't work...  i'm in miserry :-( I have already desperate of it...  i will try kernel in 12.04, and if it is not resolved, I will have to invent something new ...

---

### Post by heir4c on 2013-11-23
U don't see when you boot the purple screen with at the bottom the small logo's?
(Normally you must see them when you start a liveCD. But I see theme not when I start a live-usb)

---

### Post by luciduci on 2013-11-23
no, i see only black with theese options after boot live cd [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) -boot in efi mode...  and i was able to upgrade 13.10, after i try installed 13.04, which started in text mode,and



   it looked like it was updated successfully,but not... after load ubuntu screen i saw white screen! :-/



really huge thanks for your willingness and patience!  :)  but  I'll probably stay on good old-12.4 and try and search ad wait :-D

---

### Post by heir4c on 2013-11-23
No problem, I try to help where I can. 
I hope you find a solution or maybe in a few weeks there is better support. 
Succes!

---

### Post by blackhat1337 on 2014-03-06
> **luciduci said:**
> Hi, i've bought Acer laptop e1-522 with AMD quad-core processor A4-500 (1.5Hz), and installed Ubuntu 12.04.3 LTS 64-bit.

I think, that i have problems with AMD Radeon HD 8330, couse my laptop doesn't work correctly.
I try update drivers from soft ware centre, manually from amd site, i try official manuals, non oficial,i think, that i try everything, but these all "experiments" haven't solved my problems :/  
 I've 3big problems: 
1.During restarting screen flashes, I mean it still flashes black and white stripes
2.I can't turn off laptop- when i try it, screen flashes like during restarting, after few seconds it stops flashing and processor looks as it has shut down, but screen already shows "clear" logo without flasing, but cursor isn't loading and it's only still turn on and led at start buttom lighting. 
3. i mean, that couse of problems with graphic card and drivers, processor can overheats during the demanding work with graphic/video editors 

now, i have installed drivers from instalation disc, and It does what I described above.

-after trying to update amd catalyst drivers, I always had to reinstall the system because nothing worked properly -terminal had black, ubuntu logo during shutdown also had a black background and I still have on screen flickered strips in the upper left corner next to the launcher, and in menu of additional drivers still writes installed but not activated, whatever I tried anything

-open drivers didn't work at all, ubuntu start in text mode 

At older (5-6years old) dual-core laptop i have ubuntu 12.04.3 32-bit, but except for a problem with switching off too and few corrections of hibernation and suspend mode it works good. But theese all I soved by fixes. 

/please exuse my english, i hope, that you understand what i mean :) /

Hi, I am new to the forums, but I had seen your question/problem. And it helped me install my system, so I wanted to pay it forward.
And just installed kali linux on my e1-522-5659 with the Radeon HD 8330. And I hope you can expect to have sucess following my advice.

1. Set the bios to boot in "legacy" not "UEFI" and run the linux(mint,kali, ect) installer. Unless you have completed this step. Skip to step2.
2. At the GRUB MENU select "compatibility-mode" And log in using the default drivers.
3. Make sure your connected to internet. At the compatibility desktop, open mozilla, or IW browser. Navigate to [www.amd.com](www.amd.com)
3. Click driver/support. navigate to driver.
4. Fill out the form,select mobile card, HD series 8XXX, on OS specs specify 32 or 64 bit. and click find options.
4.2. Uninstall previous drivers except the default gflrx, if you had attempted to install previous.
5. Select the "beta" drivers from the drop-down list (it supports the HD 8**X series graphics drivers.) Download & Install, using the grphx install mode. 
6. reboot, enjoy.


~~note: if you have already attempted to install other drivers, you WILL need to uninstall them before your fresh install of the "Beta" amd drivers, or you will run into compatibility issues.~~
:P

---

