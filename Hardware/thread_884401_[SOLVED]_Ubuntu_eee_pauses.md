---
title: "[SOLVED] Ubuntu eee pauses"
date: 2008-08-09
forum: Hardware
---

### Post by karlhm76 on 2008-08-09
Hi all, I recently got an eee 900 and so naturally I decided to get rid of the default OS and put a real one on it. I chose ubuntu eee.

After running some configuration scripts I've noticed that when I'm on battery power I get annoying pauses. The whole system pauses for about 1/2 a second every 10 seconds or so. 

When I check top I notice that hald flashes up after each pause.

Its very annoying because when I'm listening to music or watching video it will skip when the pauses occur.

Anyone else has this problem, or offer some solutions?

The script I ran is below. It fixed the webcam and a few other minor issues for me but seems to have introduced this problem. It may be related to CPU scaling or ACPI because it only seems to occur on battery power. 

```
echo "* Installing ACPI modules"
sudo apt-get update
sudo apt-get install -y -f build-essential module-assistant eeepc-acpi-source  --force-yes
sudo m-a a-i eeepc-acpi
sudo cp /etc/modules ~/modules.tmp
sudo chmod 777 ~/modules.tmp
echo "eeepc-acpi" >> ~/modules.tmp
sudo chmod 644 ~/modules.tmp
sudo mv ~/modules.tmp /etc/modules

echo "** Installing OSD"
wget http://eee-osd.googlecode.com/files/eee-osd_2.1-0eeeXubuntu1_i386.deb
sudo dpkg -i eee-osd_2.1-0eeeXubuntu1_i386.deb
sudo rm ~/eee-osd*

# Wifi already works
#echo "** Installing WLAN"
#wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
#tar zxvf madwifi-nr-r3366+ar5007.tar.gz
#cd madwifi-nr-r3366+ar5007
#make clean
#make
#sudo make install
#cd ..
#sudo rm -R ~/madwifi-nr*

echo "** Fix shutdown problem"
sudo cp /etc/default/halt ~/halt.tmp
sudo chmod 777 ~/halt.tmp
echo "rmmod snd_hda_intel" >> ~/halt.tmp
sudo chmod 644 ~/halt.tmp
sudo mv ~/halt.tmp /etc/default/halt

echo "** Fine tune the system"
sudo cp /proc/sys/vm/dirty_writeback_centisecs ~/dirty_writeback_centisecs.tmp
sudo chmod 777 ~/dirty_writeback_centisecs.tmp
echo "1500" > ~/dirty_writeback_centisecs.tmp
sudo chmod 644 ~/dirty_writeback_centisecs.tmp
sudo mv ~/dirty_writeback_centisecs.tmp /proc/sys/vm/dirty_writeback_centisecs
sudo cp /etc/fstab ~/fstab.tmp
sudo chmod 777 ~/fstab.tmp
echo "tmpfs /var/log tmpfs defaults,noatime 0 0" >> ~/fstab.tmp
echo "tmpfs /var/tmp tmpfs defaults,noatime 0 0" >> ~/fstab.tmp
echo "tmpfs /tmp tmpfs defaults,noatime 0 0" >> ~/fstab.tmp
sudo chmod 644 ~/fstab.tmp
sudo mv ~/fstab.tmp /etc/fstab

echo "** Enable CPU speed scabling"
sudo apt-get remove powernowd
sudo apt-get install cpufrequtils sysfsutils
sudo modprobe p4_clockmod
sudo cp /etc/sysfs.conf ~/sysfs.conf.tmp
sudo chmod 777 ~/sysfs.conf.tmp
echo "devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand" >> ~/sysfs.conf.tmp
sudo chmod 644 ~/sysfs.conf.tmp
sudo mv ~/sysfs.conf.tmp /etc/sysfs.conf
sudo cp /etc/modules ~/modules.tmp
sudo chmod 777 ~/modules.tmp
echo "p4_clockmod" >> ~/modules.tmp
echo "cpufreq_ondemand" >> ~/modules.tmp
sudo chmod 644 ~/modules.tmp
sudo mv ~/modules.tmp /etc/modules
sudo rm -R usr_src
sudo rm -R var_cache_modass
sudo rm dirty_writeback_centisecs.tmp

echo "** Fixing web cam"
sudo apt-get install subversion
svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
cd linux-uvc
sudo make
sudo make install
sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
sudo modprobe uvcvideo

echo ""
echo ""
echo "Done! Please reboot now. Type sudo reboot"
```

---

### Post by starcannon on 2008-08-09
I run a 2g, two 4g's, and an 8g respectively. I do not know how much if any information on these models will carry over to the 9xx series; that said, on the eee's i have (7xx series), it is frequently the case that I must shutdown, pull the battery, wait 15~30 seconds, put the battery back in, boot up, and issues are gone. Yeah ACPI is fouling up.

Some possible fixes for this may include(your gonna hate me for this) reinstalling default OS and making a copy of the kernel config file located in /boot then reinstalling Ubuntu, then... compiling a new kernel using that config file, if the stars align, and you have all the modules you need (you may need to compile those as well, check asus.com for sources) then your acpi issues *may* be resolved.. gl, and hang in there, these little machines are popular enough that I expect full support to be default in the not too distant future.

---

### Post by karlhm76 on 2008-08-09
Thanks for your help. I ended up reinstalling the OS. Worked out the problem as well - CPU scaling.

Best not to scale the CPU unless you're really fanatical about battery life.

---

