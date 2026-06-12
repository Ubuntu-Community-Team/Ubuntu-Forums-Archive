---
title: "Cant install serial ports with MCS9865 instructions"
date: 2010-03-23
forum: Hardware
---

### Post by ESimard on 2010-03-23
Hi, New to ubuntu, I am attempting to install two serial ports that contain the Moschip drivers.  The two ports installed correctly and run under Windows so I assume the card is ok.

Under ubuntu 9.10 lspci shows the card present.  Following the Linux install instructions that came with the card I attempted to install the MCS9865 drivers.

The "make" command showed no errors after I ran it after entering the command sudo -s.

The "make install" showed two errors the output was:

root@ernie-desktop:~/Desktop/MCS9865_Linux/MCS9865_V1.0.0.6# make install
cp mcs9865.ko mcs9865-isa.ko /lib/modules/2.6.31-20-generic-pae/kernel/drivers/serial/
depmod -A
chmod +x mcs9865
cp mcs9865 /etc/init.d/
ln -s /etc/init.d/mcs9865 /etc/rc.d/rc3.d/Smcs9865 || true  	
ln: creating symbolic link `/etc/rc.d/rc3.d/Smcs9865': No such file or directory
ln -s /etc/init.d/mcs9865 /etc/rc.d/rc5.d/Smcs9865 || true
ln: creating symbolic link `/etc/rc.d/rc5.d/Smcs9865': No such file or directory
modprobe mcs9865
modprobe mcs9865-isa	
root@ernie-desktop:~/Desktop/MCS9865_Linux/MCS9865_V1.0.0.6# 

lshw-gtk shows the two devices but with the message "this device hasen't been claimed"

I think the problem is with the ln command above but am unsure on how to fix or proceed.  mcs9865 does indeed reside in /etc/init.d

root@ernie-desktop:/etc/init.d# ls mcs*
mcs9865

and the directory /etc/rc5.d also exists.


Thanks in advance for any help.

_Ernie

---

### Post by scorpionstudios on 2011-01-10
I refer you to my solution in this thread: [http://ubuntuforums.org/showthread.php?t=1663575](http://ubuntuforums.org/showthread.php?t=1663575)

Hope this helps you / anyone browsing this.

Niall

---

