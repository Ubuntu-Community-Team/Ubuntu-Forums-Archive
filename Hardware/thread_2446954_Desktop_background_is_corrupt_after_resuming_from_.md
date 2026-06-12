---
title: "Desktop background is corrupt after resuming from sleep - nVidia 8600GT"
date: 2020-07-09
forum: Hardware
---

### Post by madbrain on 2020-07-09
I recently installed Ubuntu on some pretty old hardware :
- Gigabyte GA-990FXA-UD3 motherboard
- AMD FX-8120 CPU
- 12GB DDR3 RAM
- nVidia 8600GT 256MB PCI (not PCIe) GPU
- Corsair M4 128GB SSD
- Aquantia AQN-107 10 Gbase-T NIC

When I put the system to sleep, and then resume, either by pressing the power button or through WOL, the desktop background is corrupt . I can switch to another background and then all is fine. This seems to be purely a cosmetic problem, but nevertheless is annoying.

Has anyone else seen anything like this ? Should I file a bug and if so where ?

FYI, I tried to switch to the open-source Nouveau driver. In this case, the system hangs with a black screen when suspending with "systemctl suspend". The machine never powers off. But it can no longer be ping'ed. The only fix is a hard reset. I had to revert to the closed-source nVidia driver for this reason.

---

### Post by mastablasta on 2020-07-10
they still have nvidia driver for this old chip? wow i though they end support sooner. hmm maybe i should have taken the nvidia laptop.

anyway is only the background corrupt? does everything else work -  e.g. GPU acceleration?

i actually remember seeing something similar on a very old PC back in the 90's and windows95. but it was a desktop, so i just turned off some of the power management.

---

### Post by madbrain on 2020-07-10
> **mastablasta said:**
> they still have nvidia driver for this old chip? wow i though they end support sooner. hmm maybe i should have taken the nvidia laptop.

anyway is only the background corrupt? does everything else work -  e.g. GPU acceleration?

i actually remember seeing something similar on a very old PC back in the 90's and windows95. but it was a desktop, so i just turned off some of the power management.

This is a desktop computer, not a laptop.

I haven't checked if GPU acceleration works, not sure know. Gnome seems pretty fast, though.
The background corruption on resume is the only thing I have noticed.

I tried changing some of the BIOS power management settings, but nothing has helped so far.
There are some other oddities on resume - sometimes the CPU fan goes to 0rpm when the machine is idle. I had an alarm in the BIOS set for that which I had to shut off. Oddly the CPU fan stays on until the first suspend/resume. I left the alarm on for CPU temp in the BIOS still.
None of the tuning I did in the BIOS fixed this problem with CPU fan going to 0rpm. The issue does not happen in Windows 10 with suspend/resume.
The graphics in Win10 are fine also, with some very old nVidia drivers.

---

### Post by mastablasta on 2020-07-11
well, looks like the issue is either nvidia drivers or drivers for motherboard (in kernel). i would say it is likely the motherboard linux drivers that are causing the issue. the problem you describe (fans etc) point to that. what is the motherbaord by the way? is BIOS updated to latest version?

i would use nvidia drivers (since they actually work). what you could do is try power management software such as tlp or some other power management software. here is some Arch Linux documentation on that: [https://wiki.archlinux.org/index.php/Power_management](https://wiki.archlinux.org/index.php/Power_management)
 It's a different linux but their documentation is good (if nothing else just to get some ideas on what to look for). 

before you do that, check logs for any errors. and start the troubleshoot from there.

---

### Post by madbrain on 2020-07-11
> **mastablasta said:**
> well, looks like the issue is either nvidia drivers or drivers for motherboard (in kernel). i would say it is likely the motherboard linux drivers that are causing the issue. the problem you describe (fans etc) point to that. what is the motherbaord by the way? is BIOS updated to latest version?


Mobo is a GA-990FXA-UD3 rev 1.1 . BIOS is the latest F10e release for that revision board.

> 
i would use nvidia drivers (since they actually work). what you could do is try power management software such as tlp or some other power management software. here is some Arch Linux documentation on that: [https://wiki.archlinux.org/index.php/Power_management](https://wiki.archlinux.org/index.php/Power_management)
 It's a different linux but their documentation is good (if nothing else just to get some ideas on what to look for). 

before you do that, check logs for any errors. and start the troubleshoot from there.

Thanks for the link. Which logs would you suggest I check ?

---

### Post by mastablasta on 2020-07-11
probably kernel log. there should a log viewer installed. in KDE  (kubuntu) it's KSystemlog. they have all the main logs colour coded. 

more logs are in /var/log

---

### Post by madbrain on 2020-07-11
> **mastablasta said:**
> probably kernel log. there should a log   viewer installed. in KDE  (kubuntu) it's KSystemlog. they have all the   main logs colour coded. 

more logs are in /var/log

It's Gnome from Ubuntu 20.04 . The Logs tool isn't color coded.

dmesg on the command-line is. 

There is a ton of information. The forum web UI apparently won't let me  paste the log into my post. It complains about a security token issue  unless I delete the output.

I'm not seeing anything in it that could explain the graphics corruption issue.
I'm guessing it's a video driver issue, but I'm not sure what other driver to try besides the nVidia proprietary and Nouveau.

Is  there a way to switch to a generic VGA/VESA non-accelerated video   driver ? That would help, at least for the purpose of testing.

---

### Post by mastablasta on 2020-07-12
logs will have to go to pastebin as it looks like they are too big for forums: [https://paste.ubuntu.com/](https://paste.ubuntu.com/)
then post link in forums.

Also journald (systemd logs) - here is how to view if you don't have it in log viewer: [https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs](https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs) 

the generic software acceleration driver is used if you use nomodeset boot parameter.
Ubuntu boot parameters:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by madbrain on 2020-07-13
> **mastablasta said:**
> logs will have to go to pastebin as it looks like they are too big for forums: [https://paste.ubuntu.com/](https://paste.ubuntu.com/)
then post link in forums.

Also journald (systemd logs) - here is how to view if you don't have it in log viewer: [https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs](https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs) 

the generic software acceleration driver is used if you use nomodeset boot parameter.
Ubuntu boot parameters:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Thanks. I added nomodeset to /etc/default/grub on the following line : 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

I also run update_grub .

It doesn't appear to have had any effect, as far as I can tell, though. After rebooting, the graphics are still plenty fast, which tells me the accelerated driver is still in use.

lspci -k shows :
03:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia

glxinfo | grep -i vendor shows :

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

The issue with background corruption is still present on suspend, unfortunately, but that's not surprising since nomodeset seems to have failed.

---

### Post by mastablasta on 2020-07-13
if you check the logs you will probably see that driver will do "modesetting" or "setting mode" or something like that. you owuld have to remove it i believe and then use the parameter. maybe someone knows more about this.

---

