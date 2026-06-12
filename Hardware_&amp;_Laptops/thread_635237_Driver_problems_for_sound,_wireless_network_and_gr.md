---
title: "Driver problems for sound, wireless network and graphics."
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by firedragonsf on 2007-12-08
I got Ubuntu today. i have read other posts and i dont understand anything. please could you tell me how to fix it in lame mans terms?
heres the problem:

1. "The software source for the package  nvidia-glx-new  is not enabled" i get this when i try to unrestrict my drivers for a NVIDIA GEforce 8400M GS graphics card.

2. The sound doesnt work. any idea on where i can get sound drivers for "Realtek high definition audio" that work?

3. Same for networks card. no wireless. "802.11 b/g WLAN"

4. "The software source for the package bcm43xx-fwcutter is not enabled" i get this when i try to enable my drivers for ... firmware for broadcom 43xx chipset family. 

thanks for the help

P.s what is firmware for broadcom 43xx chipset family??

---

### Post by Yellow Pasque on 2007-12-08
#1 and #3 are because you don't have internet access. You don't have net access because of #4. Basically, what it's trying to tell you is that you need internet access to get the driver for your wireless device (catch22). Any chance that you could plug in to a router temporarily?

We'll worry about #2 when you have internet working.

---

### Post by firedragonsf on 2007-12-08
eh... im in ubuntu now and in this forum. i do have an internet connection.

---

### Post by Yellow Pasque on 2007-12-09
Oh, well then take a look at System -> Administration -> Software Sources, and make sure the restricted repo is enabled.

---

### Post by firedragonsf on 2007-12-09
i have gotten everything but my wireless fixed. 
solution:
graphics and #4 = reinstall ubuntu
sound = [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by firedragonsf on 2007-12-09
> **firedragonsf said:**
> fix for my graphics prob:
At first boot have an internet connection that helps.

1. Go to System ==> Administration ==> Restricted Drivers Managment
2. Check the enabled box and if you have internet it should fix it self.
3. If not reinstall ubuntu :P

fix for my sound prob:
Sound drivers fix for acer aspire 5720z 
		source: [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

1.Copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh 

2.Then "cd" to it in a terminal 
	code: "cd /home/henrik/Desktop"
  if your file is on desktop

3. then type "sudo sh alsa_1.sh"

4.Now reboot

5.Type "sudo sh alsa_2.sh"

6.Open up terminal and write this:
	"sudo gedit /etc/modprobe.d/alsa-base"

7.It will open up a script, scroll to the bottom, make a new line and write this:
	"options snd-hda-intel model=acer"


Text for alsa_1.sh

```
#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1
```





Text for alsa_2.sh

```
#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2
```





This worked om my acer aspire 5720z

hope it helps

---

