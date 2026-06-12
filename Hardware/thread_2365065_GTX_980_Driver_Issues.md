---
title: "GTX 980 Driver Issues"
date: 2017-07-01
forum: Hardware
---

### Post by go-fish on 2017-07-01
Hey guys, hope I posted this in the right place. Apologies in advance, I'm fairly new to linux, this might be a wall of text.

PC Specs out of the way:

CPU: i7 5930K
GPU: Gigabyte GTX 980
Motherboard: MSI X99A Tomahawk
RAM: 16GB HyperX DDR4 @ 2133Mhz
Boot Disk: Samsung 950 Pro NVME

So I've got Ubuntu GNOME installed on my PC, installation went just fine at first. After first installation, did all of my updates, installed some programs, and rebooted. After the UEFI initialized, it skipped the GRUB options menu and went directly to a gray screen with a gray border. After about 10-20 seconds, it advanced to the screen that I enter my decryption password into, except the resolution was blown out (Low graphics mode maybe?) and I couldn't enter any text, the system was unresponsive. After another reboot, the GRUB menu showed up, but the only way I am able to boot the system is by entering 'advanced options', pressing 'e' on the 'recovery' option, and adding 'nomodeset' and 'xforcevesa'. I wait a minute, and select 'resume normal boot' when prompted. Seems to work normally after that, but I'd like to make sure I'm using the Nvidia driver and not have to do this every time I boot the system. Does anyone have any idea what I can do? None of the guides I've found in this forum or others have worked, yet. I appreciate any help!

---

### Post by Bashing-om on 2017-07-02
go-fish; Hello and Welcome to the forum .


Of interest here is what is going on with the GPU:
Post back - Between Code Tags - the output of terminal commands:
```

cat /var/log/gpu-manager.log
sudo lshw -C display
dpkg -l | grep -i nvidia
lsb_release -a

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
where we are looking to install the 375 version driver, from our repo: per;
[http://www.nvidia.com/download/driverResults.aspx/118290/en-us](http://www.nvidia.com/download/driverResults.aspx/118290/en-us)

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-07-02
Welcome. To use the Nvidia driver, you must install it. When you get the machine to a desktop using the 'nomodeset' option (probably the only one you need), check in 'Additional Drivers'. The driver for your card should be there. Install and reboot _without_ using the nomodeset command on restart and let us know how far you get.

(PS: You need the Canonical Partners repository open for the Nvidia driver, so check 'Software and Updates' and 'Other Software' and make sure you have that repo enabled.)

---

