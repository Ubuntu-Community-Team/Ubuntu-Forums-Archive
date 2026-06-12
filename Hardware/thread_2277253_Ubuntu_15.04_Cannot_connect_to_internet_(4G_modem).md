---
title: "Ubuntu 15.04: Cannot connect to internet (4G modem). SOLVED."
date: 2015-05-07
forum: Hardware
---

### Post by osmoma on 2015-05-07
Hello,
I made a fresh installation of Ubuntu 15.04 and got problems with connecting to internet by my 4G-device.
Also I was unable to connect after first boot.

My laptop is Kudu-professional from System76.com with Intel-components for CPU, GPU and network.
The 4G modem is [FONT=Ubuntu]WöW by NOS in Portugal.[/FONT]

We discussed this same bug earlier in Vivid Beta.
Ref: [http://ubuntuforums.org/showthread.php?t=2261135](http://ubuntuforums.org/showthread.php?t=2261135)

**I was able to get internet connection** after running these commands (see the above thread).
---
$ sudo service network-manager stop

$ echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

$ sudo rmmod iwlmvm iwlwifi 
$ sudo modprobe  iwlmvm iwlwifi 

$ sudo service network-manager restart
---
The 4G-hotspot is now visible and works fine.
Then the system must be updated with:
$ sudo apt-get update
$ sudo apt-get upgrade 
$ sudo apt-get dist-upgrade 

Then reboot.
And the laptop will most-likely connect well to the web by this 4G device.   Just in case you need this info ;-)

---

