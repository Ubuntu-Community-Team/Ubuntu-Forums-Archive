---
title: "Need ram/kernel advice"
date: 2008-10-31
forum: General Help
---

### Post by KingPin6 on 2008-10-31
I have a game server application that I run and it requires a lot of ram. I am at 4gb currently and using -server kernel it works fine. now im running into the issue where more and more ram is being used and today I actually maxed out my virtual mem on top of my ram. I wanted to switch to 64bit so I could use 8gb of ram, however the application doesnt work well in 64bit architecture with multiple bugs and very small uptimes in some cases. so before I take the plunge I wanted to get some advice on the issue from the community and see if anyone can suggest an alternative to switching to 64bit. I looked into bigmem but some easy searching told me ubuntu doesnt provide bigmem :(. Basic tools I require are Mysql as the DB backend, build-essentials to compile the application sourcecode, and apache+php to run its small site. 

Specs : 
Uname -a : Linux 2.6.20-17-server #2 SMP Wed Aug 20 16:54:26 UTC 2008 i686 GNU/Linux
Mobo : SuperMicro X7DBR-E Intel Xeon DualCore DualProc SATA
Proc : Intel Xeon-Clovertown 5345-QuadCore (x2)

---

### Post by Rhubarb on 2008-10-31
Perhaps if you told us what game server you're running others here may have experience with it?

Personally, I'm familiar with these games(on 32 and 64bit):-
ET:QW, Sauerbraten, UrbanTerror, AssaultCube, Quake3, Word of Padman, Postal2, Nexuiz, and Quake4.

---

### Post by KingPin6 on 2008-11-01
I dont doubt some of you would know about it, its used to "emulate" similar functionality to a popular mmorpg out there. but I cant change the software, it is what it is. I need advice on a workaround for my ubuntu to use >4gb or ram.

---

### Post by Rhubarb on 2008-11-03
From what I can recall the Ubuntu 32bit server kernel supports PAE.
If you've got a PAE supported motherboard, then AFAIK Ubuntu server (or Ubuntu Desktop with ubuntu server kernel) should support > 4GB of RAM.

Just grab this meta package: **linux-server** if you don't already have it.

---

### Post by kerry_s on 2008-11-03
just go ahead and compile your own kernel with bigmemory activated.
it's very easy.
grab the latest stable:
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.4.tar.bz2)

here's my notes, i start in the directory i downloaded to "~/Desktop" you can pretty much just copy and paste your way down the list:

sudo su
apt-get update
apt-get install kernel-package libncurses5-dev build-essential
mv *.tar.bz2 /usr/src
cd /usr/src
tar xjf *.tar.bz2
ln -s linux-2.6.27.4 linux
cd /usr/src/linux
make clean && make mrproper
cp /boot/config-`uname -r` ./.config
make menuconfig
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd /usr/src
dpkg -i *.deb
reboot

don't forget to make use of shift+? to help you under stand what the setting does.

---

### Post by KingPin6 on 2008-11-04
thank you very much for that, I will end up using it on a second machine im setting up now. The one I spoke of here I ended up going to 64bit and removing some key functionality that we can live without but with it gone the cpu usage goes down from 105% avg to 3 - 4% avg.

---

### Post by kerry_s on 2008-11-04
> **KingPin6 said:**
> thank you very much for that, I will end up using it on a second machine im setting up now. The one I spoke of here I ended up going to 64bit and removing some key functionality that we can live without but with it gone the cpu usage goes down from 105% avg to 3 - 4% avg.

1 little note, when installing the custom kernel, remove the old custom kernel first, as in boot to the old stock kernel. if you don't need headers you can remove that part "kernel_headers" and it will just do the image.
other than that it's just a whole lot of waiting, 5 hours in my case on this 450mhz 256mb ram laptop.
let me tell you, i'm on my 10th kernel tweak, i just been pushing it a little more each time. :p

so i just added a little reminder to my notes:

sudo su
apt-get update
apt-get install kernel-package libncurses5-dev build-essential
mv *.tar.bz2 /usr/src
cd /usr/src
tar xvjf *.tar.bz2
ln -s linux-2.6.27.4 linux
cd /usr/src/linux
make clean && make mrproper
cp /boot/config-`uname -r` ./.config
make menuconfig
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image
#with headers# make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
##stop reboot and switch to the stock kernel & remove old custom kernel
sudo su
cd /usr/src
dpkg -i *.deb
reboot


careful it's addicting, you'll want to try the experimental stuff, you will remove a little more each time, it's a never ending cycle. :lolflag:

---

### Post by sdennie on 2008-11-04
As stated above, the -server kernel has PAE enabled by default.  This allows you to use up to 64GB of RAM on a 32bit install.  There is really no need to switch to 64bit or compile a custom kernel if the only reason for the change is to go to 4GB to 8GB of RAM.

---

### Post by kerry_s on 2008-11-04
> **vor said:**
> As stated above, the -server kernel has PAE enabled by default.  This allows you to use up to 64GB of RAM on a 32bit install.  There is really no need to switch to 64bit or compile a custom kernel if the only reason for the change is to go to 4GB to 8GB of RAM.

hmm, so extra memory it treated as swap?

---

