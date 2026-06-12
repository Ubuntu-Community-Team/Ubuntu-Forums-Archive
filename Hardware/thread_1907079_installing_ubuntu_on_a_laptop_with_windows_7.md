---
title: "installing ubuntu on a laptop with windows 7"
date: 2012-01-10
forum: Hardware
---

### Post by adrianp918 on 2012-01-10
i want to use my windows 7 machine and also have ubuntu on it, is there a way to dual boot the both of them and pick what one i want to run?

---

### Post by wolfen69 on 2012-01-10
First, backup your stuff to an external drive and defrag windows. Then boot directly to the ubuntu cd and select "try ubuntu" to make sure all of your hardware is compatible.

Then you can start the installation and choose "install ubuntu along side of windows". Then you will see a "slider" that you use to choose how much hard drive space you want ubuntu to use. I personally, would give it at least 40gb if you have the room. The rest is pretty much self-explanatory. Come back with any questions you may have.

---

### Post by oldfred on 2012-01-10
Besides backup, I would use Windows to shrink the Windows partition, but not to create any new partitions. If you create partitions with Windows it converts from basic to dynamic which is not compatible with anything.

Also make a Windows repairCd or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Dual Boot Win7 & Ubuntu
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Mark Phelps on 2012-01-11
Agree with oldfred -- and would go further to suggest you AVOID using the slider to resize the Win7 OS partition.  Win7 is real touchy about its OS partition being messed with from "outside".  You risk getting it corrupted and then being unable to reboot from it.

The Win7 Disk Management utility is clumsy and primitive, and it limits how much you can shrink the OS partition -- but it won't damage it.

---

