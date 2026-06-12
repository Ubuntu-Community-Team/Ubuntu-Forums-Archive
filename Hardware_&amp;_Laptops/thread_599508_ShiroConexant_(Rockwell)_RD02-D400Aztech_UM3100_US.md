---
title: "Shiro/Conexant (Rockwell) RD02-D400/Aztech UM3100 USB 56K Modem"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by popot on 2007-11-01
Works with Ubuntu 7.10 Gutsy Gibbon Server.

Acknowledgment:
1. [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
2. [http://www.spinics.net/lists/linux-usb-devel/msg10326.html](http://www.spinics.net/lists/linux-usb-devel/msg10326.html)

With the pristine undefiled Ubuntu 7.10 Gutsy Gibbon Server, I got this with dmesg:
> [   24.351947] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: Zero length descriptor references
[   24.351952] 
[   24.352015] cdc_acm: probe of 1-2:1.0 failed with error -22
[   24.352033] usbcore: registered new interface driver cdc_acm
[   24.352038] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

So I went and did,
> sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 build-essential linux-source module-assistant debhelper
As I don't fully comprehend this, the command above might be overkill, do advise.

> sudo -i
cd /usr/src
tar xjf linux-source-2.6.22.tar.bz2
ln -s linux-source-2.6.22 linux
cd /usr/src/linux
cp /boot/config-`uname -r` ./.config
make menuconfig

This is followed by kernel configuration menu, scroll down to Load an Alternate Configuration File and choose .config (which is the default).


Before continuing with kernel config, type in 
> sudo pico /usr/src/linux-source-2.6.22/drivers/usb/class/cdc-acm.c

and add,
>        { USB_DEVICE(0x0572, 0x1324), /* Conexant RD02-D400 */
       .driver_info = NO_UNION_NORMAL, /* has no union descriptor */
       },

after,
>         { USB_DEVICE(0x0870, 0x0001), /* Metricom GS Modem */
        .driver_info = NO_UNION_NORMAL, /* has no union descriptor */
        },
for reference, please look at [http://www.spinics.net/lists/linux-usb-devel/msg10326.html](http://www.spinics.net/lists/linux-usb-devel/msg10326.html)

Correction: (0x0572, Ox1324) might not be correct, do 
> lsusb
which gives me
> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0572:1328 Conexant Systems (Rockwell), Inc. 
Bus 001 Device 001: ID 0000:0000
So seeing Conexant Systems (Rockwell), Inc next to it, its probably your modem. So instead of > (0x0572, Ox1324), in my case, it is > (0x0572, 0x1328 ). 

After this,
> 
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd /usr/src
dpkg -i linux-image-2.6.22.9-custom_2.6.22.9-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.22.9-custom_2.6.22.9-custom-10.00.Custom_i386.deb
shutdown -r now

This is the result of my new dmesg:
> [   43.211859] cdc_acm 1-2:1.0: ttyACM0: USB ACM device
[   43.215211] usbcore: registered new interface driver cdc_acm
[   43.215217] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

Used wvdialconf and pppconfig, with modem = /dev/ttyACM0, no problem with dial up.

---

### Post by YCW on 2008-04-22
Hi there friend. 
Is your aztech um3100 56k usb modem working fine and are you abled to fax out or not?. Oh, btw, my name is rick yong and i m using ubuntu 7.10 gnome 2.20.1 and i do have broadband connection which is working fine. Last night i purchased this unit and frankly speaking i really do not quite understand what your actual step is so i hope you be kind enough to list out the steps for me will you friend. Also, your post is in nov 2007 so i m wondering whether there be any changes in your steps or not. Pls advise thank you

---

### Post by popot on 2008-06-24
faxing is beyond the scope of this thread. Try hylafax, do a search on the ubuntu forums.

---

### Post by popot on 2008-07-01
Just made modem work for Ubuntu Hardy Heron 8.04 i386 Server.

Thank you to following websites for its help. For a detailed explanation, look in the links:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild?highlight=(kernel)|(git)]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild?highlight=(kernel)|(git)")
[https://wiki.ubuntu.com/KernelGitGuide?highlight=(kernel)|(git)]("https://wiki.ubuntu.com/KernelGitGuide?highlight=(kernel)|(git)")
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild?highlight=(linux-header)|(dpkg)]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild?highlight=(linux-header)|(dpkg)") 

Just follow the commands in command line interface,

1.
> sudo -i

2.
> apt-get update 
apt-get install git-core linux-kernel-devel fakeroot build-essential

3.
> mkdir /home/ubuntu
cd /home/ubuntu

4.
> git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ubuntu-hardy

5.
> export GIT_DIR=/home/ubuntu/ubuntu-hardy/.git
git pull

6.
> pico /home/ubuntu/ubuntu-hardy/drivers/usb/class/cdc-acm.c

and add,
> { USB_DEVICE(0x0572, 0x1328 ), /* Conexant RD02-D400 */
.driver_info = NO_UNION_NORMAL, /* has no union descriptor */
},
after,
> { USB_DEVICE(0x0870, 0x0001), /* Metricom GS Modem */
.driver_info = NO_UNION_NORMAL, /* has no union descriptor */
}, 


7. # Save away local commits
>   git rev-list --reverse origin..HEAD > local-commits
  git branch new-head origin
  git checkout new-head

8. # This will stop on first error. Cleaning up failures is an excercize for the user
>   for cmt in `cat local-commits`; do git-cherry-pick $cmt || break; done
  git branch -f master new-head
  git checkout master
  git branch -D new-head

9.
> cd /home/ubuntu/ubuntu-hardy/

10.
> debian/rules updateconfigs

11.
> 
AUTOBUILD=1 fakeroot debian/rules binary-debs

12. If the following commands do not work, the XXs might change: "linux-image-2.6.XX-XX-server_2.6.XX-XX.XX_i386.deb". So just do ls, to find out the XXs. 
> cd /home/ubuntu/
dpkg -i linux-image-2.6.24-20-server_2.6.24-20.35_i386.deb

13. 
> shutdown -r now

This is my new dmesg:
> [   44.333421] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[   44.343749] usbcore: registered new interface driver cdc_acm
[   44.343753] /home/ubuntu/ubuntu-hardy/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters

---

