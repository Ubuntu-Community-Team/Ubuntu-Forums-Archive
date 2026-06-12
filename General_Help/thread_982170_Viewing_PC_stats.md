---
title: "Viewing PC stats"
date: 2008-11-14
forum: General Help
---

### Post by Roach360 on 2008-11-14
How can i do this?

I would like to view my processor type and speed, as well as my video device, but i'm new enough to ubuntu that i cannot find it on my system.

---

### Post by chewit on 2008-11-14
Download and install sysinfo from the repos.

---

### Post by Roach360 on 2008-11-14
Thank you much,

Just what i needed.

---

### Post by akelsall on 2008-11-14
I'm not familiar with what sysinfo provides, but here are a few other commands you can use to check out your hardware (it's more than what you're looking for, but might come in handy down the road):

sudo ddcprobe | less -- displays info about your monitor and video card

cat /proc/cpuinfo  -- displays CPU info

lspci -- displays info about all PCI buses in the system and all  
         devices connected to them. 
lspci -v or lspci -vv (to view more detail)

sudo dmidecode | less  -- reports information about your system's hardware as reported by your system BIOS.

lsusb -- dispalys all usb devices
sudo lshw -C dis -- displays all hard disks and CD/DVD drives
iwconfig -&#8211; displays information about wireless networking card

Another tool to display hardware info is hwinfo (if it's not installed, use "sudo apt-get install hwinfo" to install it).

Andy

---

