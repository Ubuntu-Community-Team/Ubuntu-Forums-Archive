---
title: "GeForce G210M"
date: 2013-04-23
forum: Hardware
---

### Post by obermensch on 2013-04-23
Hi everyone, i need some help with driver install

here some innformation

i got a GeForce G210M card.
and my computer is "Asus UL30VT"

i need to get the nvidia drivers installed, and cuda. and if possible get opencl

but i am totaly ubuntu noob, all this need to be done in terminal, since i access my computer trough ssh

can someone make a simple guide to me really noob friendly? in that case i will love you!

Edit: i got Ubuntu 12.10 64bit running

---

### Post by darinschmidt on 2013-04-23
i have never done this myself but i'd install wget or download putty sftp and upload the linux driver which you should be able to get from their website. I'm only speculating what you could do to help push you in the right direction. But you shoudl be able to extract the contents of the package you download and install the driver. usually has a install.sh file or something that you have to chmod 755 <filename> and then as root type ./install.sh while in that directory.

But maybe this could be of some use for you [http://ubuntuforums.org/showthread.php?t=1970903](http://ubuntuforums.org/showthread.php?t=1970903)

---

### Post by obermensch on 2013-04-23
aparently im not the only one strugle with this, i found this guide after many google pages
[http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)



Once logged in, become root.

sudo su

Then, install the linux-headers-generic package.

apt-get update
apt-get install linux-headers-generic

Once that is installed, we need to upgrade the kernel to match the recently-installed headers, and reboot to load the new kernel we just installed.

apt-get dist-upgrade
reboot

After reboot, log in again (Ctrl-Alt-F1 to do so in text mode). Become root again.

sudo su

Now, it&#8217;s time to actually install the nvidia drivers.

apt-get install nvidia-current-updates

After this has been installed, you will get a number of status messages saying you&#8217;re done and that the drivers are installed. You are not done. If you reboot now, your computer will boot back to a black screen and be effectively bricked. I spent a full working day tearing my hair at this. There&#8217;s one more thing you need to do. You need to give the drivers their initial settings file.

nvidia-xconfig

After this step, you can finally reboot and use fast drivers, as the open source drivers aren&#8217;t there quite yet.

reboot

---

