---
title: "Ati drivers :("
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by BuBBa123 on 2006-02-04
umm.. i fucked up my post :/

---

### Post by jamesford on 2006-02-04
i made myself a little script for isntalling ati drivers for my 9600 some time ago, it works on every pc ive tried it on...dont know if it can help you, and u use it on your own risk. in case u wanna give it a go, heres the script
---------------------
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-`uname -r`
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf
-------------------
copy/paste into empty text file, save as ati_driver_install.sh (or whatever you like) to homedir or desktop
righclick the file > properties >permissions > mark the topmost execute box

run the file...

---

### Post by BuBBa123 on 2006-02-04
Cant find the ap-get package..

FATAL: Error inserting fglrx (/lib/modules/2.6.10-6-386/misc/fglrx.ko): Invalid module format

---

