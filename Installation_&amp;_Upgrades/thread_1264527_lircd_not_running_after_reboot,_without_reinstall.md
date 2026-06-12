---
title: "lircd not running after reboot, without reinstall"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by jingo_man on 2009-09-12
hi all

i have installed lirc-0.8.5 (downloaded and compiled from source) for the mcsesb2 device in an antec fusion remote case (the provided iMon device is horrible to use and even worse to look at! but i did get the iMon remote & IR receiver working from various guides that are available here and elsewhere on the net.)

after compiling and installing the device, i run:
sudo modprobe lirc_mceusb2
sudo lircd
sudo irw

and i can see codes from the remote, so i presume all is working. then i reboot.

nothing works when i startup. this is what i type:
sudo lircd
irw (note this time round i no longer require the sudo prefix - it errors when this is missed straight after install)

nothing appears on screen...

i have checked:
lsusb
lsmod
dmesg
ls /dev/lirc*

and it all seems normal, i.e. i see "lirc_mceusb2" & "lirc_dev" aswell as the 0471:0815 vendor:product id's for the philips device.

now i have noticed that the method i am installing it doesnt seem to create the /etc/init.d/lirc script or the /etc/lirc/hardware.conf files, but it does get the device up and running on first install. just not after any reboots. i have also tried copy/pasting someone's versions of the above scripts, however they seem to have simply changed the text from the iMon setup, which i think is wrong, as there's no need to have 2 devices with this remote - that is an iMon fudge, from what i can gather.

if i go back to the source files directory and re-run "sudo make install", the device works again, as before until i reboot...

this is driving me crazy. can anyone help?

jingo_man

i have ubuntu jaunty (9.04) with nothing on it, except i updated the nvidia graphics currently.

---

