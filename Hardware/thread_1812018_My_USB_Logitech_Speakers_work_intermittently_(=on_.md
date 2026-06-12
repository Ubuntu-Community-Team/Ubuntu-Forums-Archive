---
title: "My USB Logitech Speakers work intermittently (=on and off)"
date: 2011-07-25
forum: Hardware
---

### Post by s3a on 2011-07-25
The USB speakers initially did not work at all so, I basically added the kernel module which is the driver for the USB speakers that I want loaded upon boot to the file that loads kernel modules upon boot (modprobe.conf) and then I added the kernel module I want blacklisted upon boot to the file that blocks kernel modules from being loaded upon boot (blacklist.conf):

```
georgia@deniz-desktop:~$ sudo echo "snd_usb_audio" >> /etc/modprobe.conf
georgia@deniz-desktop:~$ sudo echo "snd_hda_intel" >> /etc/modprobe.d/blacklist.conf
```

I then rebooted and found that the sound DOES work but it's very static-y and stops working and needs the USB plug unplugged then plugged back in for it to work again. Initially, I thought this was because I was using a USB extension cord but, the same happens when I use it directly. I use USB 1.1; could that be the issue?

I think this is the information for the USB interface of my computer:
```
georgia@deniz-desktop:~$ lspci -vv | grep USB
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
```

and this is the output of lsusb (it doesn't seem to detect it - I tried doing the command many times even at times where it was working):
```
georgia@deniz-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 041: ID 1130:1620 Tenx Technology, Inc. 
Bus 001 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
georgia@deniz-desktop:~$
```

Any help in making the speakers work permanently without interruption and static sounds would be GREATLY appreciated!
Thanks in advance!

---

