---
title: "Screen Flicker Using Nvidia Graphics Card"
date: 2011-05-01
forum: Hardware
---

### Post by teegs on 2011-05-01
Hi guys,

I'm new to Ubuntu but I just took a course in Unix so I know a little bit about command line.

I'm running Ubuntu 11.04 and there is a screen flicker that occurs on various sections of the screen at random times roughly spaced a couple minutes apart. I think it could be an issue with the graphics driver. 

The Additional Drivers utility tells me that NVIDIA accelerated graphics driver (version current) is activated but not currently in use. I'm using a GeForce Go 7950 GTX.

Any help would be greatly appreciated. Please let me know if I should post any log files or additional information.

Thank you

---

### Post by teegs on 2011-05-01
bump for help :(

---

### Post by crys on 2011-05-02
Same here with a nvidia Quadro NVS 295.

---

### Post by teegs on 2011-05-03
Does anyone know if there is a tutorial I could use to install the binary driver from NVIDIA without going through Ubuntu?

I tried doing it myself but I ended up breaking x and had to reinstall Ubuntu.

---

### Post by teegs on 2011-05-08
Found this somewhere on the forums and it worked:

1. Downloaded nvidia driver from [nvidia.com]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and mv it to root:
```
mv NV* /
```2. Did blacklisting - [Howto install nVIDIA drivers manually on Ubuntu 10.04 (Lucid Lynx)]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
```
gsudo gedit /etc/modprobe.d/blacklist.conf
 
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv                      
```                                                 
          
3. Then purged any nvidia drivers remaining:
```
sudo apt-get --purge remove nvidia-*                      
```4. Make sure you have the latest headers:
```
sudo apt-get install linux-headers-`uname -r`                      
```5. Reboot and choose to boot in recovery mode from GRUB
```
GRUB -> Choose (recovery mode)                      
```6. In the selection menu -> *_drop to root shell_* then
```
init 3
```7. Install the driver with
```
sudo sh /NV* 
```8. Enjoy

---

### Post by teegs on 2011-05-09
Never mind didn't fully fix the problem.

---

