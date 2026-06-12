---
title: "Disable firewire port?"
date: 2008-09-04
forum: Hardware
---

### Post by bogoliubov on 2008-09-04
Hello. On my laptop I have a firewire port which I never use. Since I've seen that the module for the firewire port is on the list in "powertop", I'd like to disable it, and do it so that it will be disabled when I reboot the laptop.

How can I do this? Can I be sure that the module for the firewire port isn't needed for something else?

$ lspci | grep 1394
05:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

$ lsmod | grep ohci
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394

---

### Post by lswb on 2008-09-04
You can blacklist these modules by putting these lines in any file in the /etc/modprobe.d directory:

blacklist ohci1394
blacklist ieee1394

You could use an existing file like /etc/modprobe.d/blacklist or make a new file for instance named firewire-blacklist in /etc/modprobe.d and put the lines there, that way it would be easy to find should you want to change it in the future. Files in /etc must be edited as root, i.e. use sudo vi or whatever editor you prefer to use to open or create the file.

---

### Post by bogoliubov on 2008-09-05
Thanks, but it doesn't work. I The modules are present when I reboot. No idea why...

---

### Post by bogoliubov on 2008-09-08
Bump...

---

### Post by hacker128 on 2008-12-16
This is a bit late, but...

What I did:

sudo bash #Enter your password

cat > /etc/modprobe.d/firewire-blacklist
blacklist sbp2
blacklist ieee1394
blacklist ohci1394
#press Control-D

rmmod sbp2 ohci1394 ieee1394
exit

---

### Post by Axx83 on 2009-04-26
that doesn't work, I get those module loaded if I restart.

---

### Post by Axx83 on 2009-04-26
If you do:

```
sudo update-initramfs -u -v
```

after putting those blacklists

they are not loaded anymore

I suggest to backup the initfile in /boot first tough

---

