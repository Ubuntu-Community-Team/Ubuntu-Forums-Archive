---
title: "Nvidia 460 GTX works on one computer, but doesn't on another."
date: 2017-08-05
forum: Hardware
---

### Post by stormwaker on 2017-08-05
Hello,

I've got 2 PCs like this:

**PC1**
CPU: i5-4690K
MOBO: MSI Z97 GAMING 3
RAM: 8 GB
GPU: Nvidia 460 GTX
OS: Ubuntu 16.04 LTS/Windows 7 64 bit

**PC2**
CPU: AMD Phenom x4 955
MOBO: ASUS M4A77TD
RAM: 6 GB
GPU: Nvidia 560 Ti
OS: Ubuntu 16.04 LTS/Windows 7 64 bit

I wanted to switch GPUs in those PCs, but after the change I lose signal on monitor on PC2 during Ubuntu boot (few seconds after grub). I'm 100% certain that everything is connected correctly, switched cards back and forth and this issue is always present with 460 GTX in PC2. 460 GTX is working correctly under both OS on PC1, but works only under Windows 7 on PC2. Also I've tested like 3 different Nvidia 460 drivers for Ubuntu on PC1 and it worked under all of them. Things I've tried that didn't solve this issue:
[LIST]
[*]installing Debian 9 without desktop enviorment on PC2 (couldn't boot it, but at least was able to install it through gui interface)
[*]using different ports on GPU like VGA, DVI1, DVI2, HDMI
[*]connected monitor from PC1 to PC2
[*]Ubuntu-Live USB (issue appears straight after loading data from USB drive)
[*]upgrading PC2 BIOS
[/LIST]

I'm very confused about what is causing this problem. Any comments on this issue will be appreciated.

---

### Post by Bashing-om on 2017-08-05
stormwaker; Hello; Welcome to the forum .

Let's look at this as a graphic's driver issue .
Get a quick overview of what might not be taking place.
At the login screen key combo ctl+alt+F1 to gain a console interface.
Log in here with your credentials . when pass word is entered there is no respsonse to the screen. Enter pass word blind and hit the enter key.
Now what shows from terminal command:
```

sudo lshw -C display

```
Compare your result to mine:
> 
sysop@x1604:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display               
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:fc000000-fc07ffff
sysop@x1604:~$ 

where of interest here is if the card is identified ( product: GK208 [GeForce GT 710B] ; and a driver loaded (  configuration: driver=nvidia latency=0) .
Then we see where we go from here .
Mind you that I can accept that a kernel boot parameter  (nomodeset) "may" be required to get the kernel to boot up .

we do this in small steps and easy stages .

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stormwaker on 2017-08-07
I'm not even able to see the login screen :<

---

### Post by Bashing-om on 2017-08-07
stormwaker; Well =

The plot thickens

> **stormwaker said:**
> I'm not even able to see the login screen :<
What release are we working with ?  Makes a difference whether upstart or systemd.

Can you boot to the grub boot menu and here -> advanced options -> recovery kernel ? We do need to get to a terminal somehow.

Background info: I too switched to a later generation nvidia card . Lo and behold I found in 14.04 there is no open source support for my card . I have to boot "nomodeset" as on that install I choose not to install the proprietary graphic's driver .

We find out what is not going on, and what our options are.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

