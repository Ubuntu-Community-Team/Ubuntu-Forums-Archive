---
title: "New HP pavilion, how to enable wifi"
date: 2011-05-04
forum: Hardware
---

### Post by pontifor on 2011-05-04
Hi,  trying to put Ubuntu 10.10 32bit on a new laptop, it installs great but does not seem to see the wireless card ( it is not broadcom I had the guy at best buy check before buying ).  

the laptop is a HP Pavilion dm1-3025dx

the output of lspci lists a RaLink Device 539f which I believe is the wireless card.

however there is only the eth1 interface in the output of ifconfig, the device does not appear configured, any ideas how to proceed would be appreciated.

thx,
Stefan

---

### Post by hammad1337 on 2011-05-05
Bump

---

### Post by jayron1 on 2011-05-05
You can enable wifi by turn it to the right.It will turn blue if your wifi is enable other wise it will show red if it is disable.

---

### Post by hamburgers on 2011-05-08
Hi, I would like an answer to this question too, Thanks!

---

### Post by Blasphemist on 2011-05-08
It looks like you aren't the first with this issue. See these threads please.

[http://ubuntuforums.org/showpost.php?p=10452987&postcount=42](http://ubuntuforums.org/showpost.php?p=10452987&postcount=42)
[http://ubuntuforums.org/archive/index.php/t-1685430.html](http://ubuntuforums.org/archive/index.php/t-1685430.html)

> 1. Download the file contained at this link: [http://barkmunchers.com/dm1z/RT.tar.gz](http://barkmunchers.com/dm1z/RT.tar.gz)

2. Extract the files to a directory. Then open a console, navigate to the directory that you extracted the files to then run the following commands:

sudo make
sudo make install
sudo mkdir -p /etc/Wireless/RT5390STA
sudo cp RT5390STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat
sudo cp ./os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt5390sta.ko

Note that for the last command above I used the option <uname -r>. This will copy the files to the current running kernel version. Make sure you are running the kernel that you wish to get the wireless running on...

Now edit /etc/modules to add the line 'rt5390sta' at the end

Then run:

sudo depmod -a
reboot


---

