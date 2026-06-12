---
title: "Techwell 6805 pci card"
date: 2013-03-02
forum: Hardware
---

### Post by jameswilson1977 on 2013-03-02
Hi all
I have a techwell 6805 based 32 channel card that i want to use on ubuntu.
I have installed 12.04 lts tonight and the card is seen but no /dev/video devices are listed.

I have seen that i need to add the driver but i have failed so far. I did update the kernel to 3.8.1 using this guide 

[http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/](http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/)

in the hope the drivers were now included. Alas it didnt help.

I then followed this post [http://ubuntuforums.org/showthread.php?t=1088843](http://ubuntuforums.org/showthread.php?t=1088843) and had make issues.

I know its me but id like to get this card working if i can.

Any advice greatly appriciated or if you need anymore info please let me know.

Thanks

James

---

### Post by jameswilson1977 on 2013-03-03
Update
Removed the 3.8 kernel and went back to 12.4 current (3.2)

then this worked


mkdir techwell cd techwell/ git clone git://gitorious.org/tw68/tw68-v2.git tw68-v2/ make sudo make install sudo modprobe tw68 lsmod|grep tw dmesg

---

