---
title: "HP Laserjet 1020 Not Printing"
date: 2009-03-05
forum: Hardware
---

### Post by linuxpyro on 2009-03-05
I am having a problem with my HP Laserjet 1020 on Intrepid, one which seemed to not exist before I upgraded.  The printer is installed and detected, but will not print; the properties box thinks the printer is unplugged or turned off, when it is on and plugged in via USB.  I searched around and found that this particular one needs its firmware given to it when it is turned on, and followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1047372&highlight=hp+1020").  Now, when the computer boots or I restart the printer I get this in /var/log/messages:

[code]
Mar  5 19:48:15 Rock /etc/hotplug/usb/hplj1020: foo2zjs: ... download successful.
Mar  5 19:48:31 Rock python: hp-toolbox(init)[9933]: warning: hp-toolbox should not be run as root.
Mar  5 19:48:33 Rock kernel: [ 2878.641171] usblp0: removed
Mar  5 19:49:20 Rock kernel: [ 2925.757860] usb 1-3: USB disconnect, address 9
Mar  5 19:49:22 Rock kernel: [ 2927.732022] usb 1-3: new high speed USB device using ehci_hcd and address 10
Mar  5 19:49:22 Rock logger: loading hp_laserjet_1020 firmware 001 010
Mar  5 19:49:22 Rock kernel: [ 2927.890019] usb 1-3: configuration #1 chosen from 1 choice
Mar  5 19:49:22 Rock kernel: [ 2927.900331] usblp0: USB Bidirectional printer dev 10 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
Mar  5 19:49:23 Rock python: hp-firmware[9999]: warning: hp-firmware should not be run as root.
Mar  5 19:49:23 Rock /etc/hotplug/usb/hplj1020: foo2zjs: loading HP LaserJet 1020 firmware /usr/share/foo2zjs/firmware/sihp1020.dl to /dev/usb/lp0 ...
Mar  5 19:49:23 Rock /etc/hotplug/usb/hplj1020: foo2zjs: ... download successful.
Mar  5 19:51:01 Rock kernel: [ 3026.445437] usblp0: removed
[code]

Note: I think this part is from when I restarted the printer instead of rebooting, and I think that's the reason for the removed bit.

The problem is that, though it seems to have downloaded the firmware successfully, it still does not print.  Instead it still shows up as being off or unplugged, anything put in the queue just sits there.  I tried loading the firmware manually (using sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0), but there was still no effect.  The only thing that will make it print is removing the printer in the printing box and then readding it, either through the Gnome menu or by using HP's tool.  

Any ideas?  Again, this printer worked in 8.04.  Has anyone got it working in 8.10?

---

### Post by bhaverkamp on 2010-04-09
Did you get this resolved? I am having same issue. Does not work in lucid either.

---

### Post by keplerspeed on 2010-04-09
I did a how to a while back. My how to still works with 9.10.

[HP Laserjet 1020 on ubuntu]("http://ubuntuforums.org/showthread.php?t=1172301")

---

### Post by ramjet_1953 on 2010-04-09
Have you tried installing [COLOR="Blue"]hplip[/COLOR] and [COLOR="Blue"]hpijs-ppds[/COLOR]?

They can be installed through Synaptic or

```
sudo apt-get install hplip
```
```
sudo apt-get install hpijs-ppds
```

If you do this, it will take a little while to install, as Python and its' libraries need to be installed.

You just click on the HP toolbar icon and it is very easy to then set-up HP printers.

Regards,
Roger:)

---

### Post by bhaverkamp on 2010-04-10
That did the trick. Thanks. I tried the suggestion from first poster first. The 'sudo apt-get remove hp*' wanted to remove several hundred packages but asked me if I really really wanted to do this. I of course bailed. I am a happy camper now.

---

