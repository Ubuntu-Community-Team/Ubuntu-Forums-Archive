---
title: "NVIDIA Driver 'forgotten' after reboot"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by ady-e on 2007-11-18
Hi. I'm new to Linux and Ubuntu but am learning lots, fast, the hard way.

So far I have found this forum to be an invaluable source for setting up my new Ubuntu system and I thank all involved in this facility.

However, I have spent most of the weekend trying to install drivers for my NVIDIA graphics card. I have done this successfully a number of times now. This is because every time I reboot the machine Ubuntu goes into 'low graphics mode' and I can't find the driver and have to re-install it. My lshw -C video looks like this:

  *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 4000]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

and the driver I installed is NVIDIA-Linux-x86-1.0-9639-pkg1.run This was done in the following manner:

CTRL+ALT+F1
sudo /etc/init.d/gdm stop <to close GNOME and X Server>
cd /home/adrian/Documents <directory containing driver>
sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run <install driver>
sudo /etc/init.d/gdm start <restart GNOME and X Server>

This is also true for my WIFI Interface. After reboot I have to re-input WPA Key before connection is possible.

It sounds to me like there is some config files where information is sought by Ubuntu that may need changing.

If anyone can help I'd be very grateful. As I said, I'm new to Ubuntu so 'small baby steps' please ;)

Thanks

---

### Post by dfreer on 2007-11-18
Same issue here, with NVIDIA 100.14.19, Geforce Go 7400, AMD64 Gutsy. Haven't run into this issue before, but like the OP said, reinstalling the driver and then restarting the X Server/GDM will work until the next reboot.

EDIT:
This worked for me, maybe it'll help you out:
```
sudo vi /etc/default/linux-restricted-modules-common
```
Change this line:
DISABLED_MODULES=""
To this:
DISABLED_MODULES="nv"

---

### Post by ady-e on 2007-11-20
Worked! Superb! Thanks very much.

Luckily I have used the 'vi editor' a few times with Cisco Routers but have never liked it. would 'sudo -e' have worked in the same way?

---

### Post by dfreer on 2007-11-20
The main thing was to edit the file with root permissions, so that you can save it. I happened use vi, but you could've done it like so:
```
sudo gedit /etc/default/linux-restricted-modules-common
```
```
sudo nano /etc/default/linux-restricted-modules-common
```
```
sudo kate /etc/default/linux-restricted-modules-common
```

It appears that "sudo -e" opens the file with nano, which would work. I didn't know you could edit files like that myself, I guess you learn something new every day :D
Glad this worked for you!

---

### Post by ady-e on 2007-11-20
I stumbled on sudo -e when trying to edit the grub menu to set windows as default OS and shorten the wait time for wifes sake (technophobe). I'll try your other methods though.

To be honest, I had no idea what it meant at the time but with a fresh install what could have gone wrong?! Just re-install and try again! lol

Thanks for your help with the NV driver issue though. Much appreciated! :D

---

### Post by amorangi on 2007-11-25
I'm getting the same problem, though the solution above didn't work for me. Everything WAS working ok till I tried to get my microphone working and tried some alsa settings recommended by the forum. Upon reboot the nvidia driver wasn't loaded, and although it could be re-enabled and reloaded by restarting X on reboot it would be gone again. I think I'm going to have to do a reinstall as the quickest option to fix this - I've already wasted an hour and a half, on top of the 2 hours I've wasted trying unsuccessfully to get a simple microphone to work!
To say I'm not very happy about this situation is an understatement. I've been using Ubuntu since 4.10, but I still can't recommend it to "normal" users as there are just too many "simple" things that either don't work or break so badly unexpectedly they may as well be irreparable.

---

