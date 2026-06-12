---
title: "Upgraded to GTX 1060, Ubuntu 16.04 freezes on resume"
date: 2016-10-09
forum: Hardware
---

### Post by rilkeansoul on 2016-10-09
Was running 16.04 perfectly with GTX770 and proprietary Nvidia driver. Also works fine with Noveau.
Upgraded to GTX 1060, works very nicely, except workstation freezes upon resume from suspend.
Before freeze, blocky graphics on monitor resume, then mouse moves but have to hard reset.

---

### Post by halda on 2016-11-14
Exactly what I am facing. Upgrading to 16.10 made it worse. I did not find another workaround. Now I am left with Ctrl+Alt+F1 and "sude service lightdm restart" command. It will restart all your apps in GUI. Blah...

---

### Post by oldfred on 2016-11-15
NVIDIA GeForce GTX 1060 Offers Great Performance On Linux
[http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1)

You typically have to purge all old nVidia drivers as any new nVidia driver does not, and then creates conflicts.
And version in Ubuntu repository is not new enought, you have to add the ppa with very newest drivers.

       
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
    
Should only show standard drivers in repository.
       
 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  


 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 


 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by halda on 2016-11-15
@oldfred Thanks for "generic" answer, but I have tried that. Ubuntu offers 367.57, the PPA offers 370.28
Already installed also with --purge the old ones. None has changed. I searched a lot before I posted here :) I tried everything I have found on 16.04. Then upgraded to 16.10 which made it worse! Then desperately reinstalled (clean install) to 16.04 and the exact same problem. But this issue does not seem to be only on Ubuntu as I have found another "nvidia suspend freeze" problems when I searched for the solution.
EDIT: there is maybe one thing related - on 16.04 it usually does not happen directly on login screen. I can usually write password and it is OK. But then when I try to use dash or Alt+Tab or other Unity things, the GUI starts lagging and freezing sometimes with blocky screen graphic. On 16.10 it freezes directly on login screen, always after returning from suspend.

UPDATE: it is maybe OpenGL related. I tried to switch off "OpenGL Settings" -> "Allow Flipping" in NVIDIA X Server Settings. The laggy GUI immediately disappears and appears as I turn it off/on. The other problem that occures is that I have no mouse cursor :D or there is a nasty blocky window about 100x100 pixels and the "virtual" cursor is in its left upper corner. I also tried Xubuntu enviroment and there was only the missing cursor issue.
So the question is - is it caused by Nvidia drivers (even the newest ones 370.28)? As I did not have any problem using my GTX660OC.

UPDATE2: I can not use print screen, as the nasty box is not there! So I had to take a photo: [IMG]http://i65.tinypic.com/300s842.jpg[/IMG]
you can see, that I also right-clicked to have context menu to make you see, where the cursor should be.

---

### Post by halda on 2016-11-20
So, updated to newest Nvidia 375.20. The "Allow Flipping" feature still has to be disabled, but ... wait for it.... the nasty blocky window has not appeared yet! It seems the problem solved itself, as usual :P Nah, more testing in progress, but it seems promising as my system is usable again.

---

### Post by petersaints on 2017-03-15
Were you able to fix the missing cursor problem? Disabling "Allow Flipping" prevents the system from displaying artifacts and eventually freezing. However, I do have that same missing cursor. Usually, as soon as I play some video (e.g., YouTube) the cursor just vanishes. It's still possible to use the mouse but the cursor becomes invisible. Trying to get to a "tty" just hangs the system in black screens and I'm unable to get to the destkop without rebooting my system.

I have experienced this problem on both Ubuntu 16.10 and Fedora 25. And I'm on a laptop with a GTX 1060. The problem would probably not happen if this was not a GSYNC enabled laptop which is directly connected to the GTX 1060, bypassing the integrated Intel GPU. When I bought, I knew it had GSYNC, but I wasn't aware that GSYNC implied that the Intel card would be disabled and inaccessible. Actually, I'd prefer to just use the Intel card on Linux and disable the GTX 1060 on Linux, since I usually don't do very heavy graphical tasks on Linux.

---

