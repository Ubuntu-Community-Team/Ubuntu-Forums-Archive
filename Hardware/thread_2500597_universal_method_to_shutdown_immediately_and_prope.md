---
title: "universal method to shutdown immediately and properly poweroff.target"
date: 2024-09-06
forum: Hardware
---

### Post by rupesh3 on 2024-09-06
Hi I am Rupesh from India and I brought a new pc with AMD Ryzen zen3 5500GT APU and Asus prime b450 motherboard. I installed Ubuntu Linux successfully and everything is working fine except I can't shutdown immediately.

When I press power button while the system is running it must shutdown immediately and properly without any questions but this is not happening.

Actually I am in a place where there are frequent power fluctuations and so I have followed a small trick to halt immediately and safely. 

I created a symbolic link as follows 

ln  -sf /usr/lib/systemd/system/poweroff.target /etc/systemd/system/alt-ctrl-del.target 

As I created symbolic link when I press the buttons alt ctrl del in console mode ie., command line the system must halt immediately and properly without any questions or confirmation but this is not happening.

From the past two years I am using the same technique to shutdown the other Linux systems immediately and safely.

At present I installed Fedora 40 and Arch Linux operating systems and created symbolic link same as above and when I press alt ctrl del in console mode they are halting safely and immediately.

Even in desktop environments like mate and xfce when I press power button it is asking for confirmation.

I have created a new shortcut in cinnamon desktop with name poweroff and assigned the buttons Ctrl Alt p with command poweroff. After that in cinnamon desktop when I press Ctrl Alt p the system is halted properly and safely.

In mate and xfce desktop environments I have created the same shortcut with buttons Ctrl Alt p. In mate and xfce desktop environments when I press Ctrl Alt p the system is not being halted and it is asking for confirmation.

I am the fan of Linux and its desktop environments and so I have installed Ubuntu with various desktop environments and window managers like afteratep, awesome etc.,.

When I press power button in the pc cabinet some desktop environments are asking for confirmation do you want to shutdown. Some desktop environments or window managers are doing nothing I mean neither halting or logout.

My requirement is when I press some key combination like Ctrl Alt p or power button in pc cabinet the system must shutdown or halt immediately without any confirmation.

Kindly try to suggest how to shutdown immediately and safely without any confirmation and also try to suggest why the above symbolic link is not working.

Regards,
Rupesh.

---

### Post by TheFu on 2024-09-06
Get a UPS!  Don't allow power interruptions, ever.

I use 
```
sudo shutdown now
```
Most of the time, it requires 30-90 seconds to cleanly stop all the running processes and power off the system.  The power buttons on my systems are seldom used. Only pre-boot, like if I'm trying to get into the BIOS and missed it.  Besides that, I use the command above.  This is an alias for whatever systemd prefers this release.

I don't shutdown very often, so I don't really remember if any questions are asked or not. Generally, I reboot, 
```
sudo shutdown -r now
```

My computers are all on a UPS. We have some heavy lightning storms here from time to time. Generally, power is stable, though it does flicker a few times every year.  Just a few days ago, it was a nice, sunny, day and the power flickered enough to reset all the digital clocks around the house, but not so much as to make the UPSes even "chirp" like they do to warn of a power issue.

---

### Post by rupesh3 on 2024-09-06
Hi I am using UPS for my system and in rare cases there are power fluctuations.

At any cost I don't want to damage my system and hardware.

When I normally use my system I click on shutdown button present in the menu and at rare cases when there's a power fluctuation I can't open menu and click on shutdown button because I have not connected my monitor to UPS.

In such cases I want to shutdown my system immediately and safely without any confirmation with a shortcut like Ctrl Alt p.

In other linux distributions I have created a symbolic link to poweroff.target and it is working fine but under the current Ubuntu this is not working.

---

### Post by rupesh3 on 2024-09-06
Any operating system like windows Fedora Debian Arch Linux etc., shutdown immediately when we press shutdown button present in the cabinet.

This is not happening in the current Ubuntu Linux. It is asking for confirmation.

---

### Post by Yellow Pasque on 2024-09-06
Did you try?
```
gsettings set org.gnome.SessionManager logout-prompt false
```

---

### Post by rupesh3 on 2024-09-06
Ok I will try.

Is there any universal method to shutdown the system immediately and safely without any confirmation.

Universal means I am may be working in any desktop environment like lxde or window manager like blackbox. When I press power button or shortcut key like Ctrl Alt p the system must shutdown immediately and safely without any confirmation.

---

### Post by Yellow Pasque on 2024-09-06
Is this what you are asking for?
```
sudo shutdown now
```

---

### Post by TheFu on 2024-09-06
> **rupesh3 said:**
> Any operating system like windows Fedora Debian Arch Linux etc., shutdown immediately when we press shutdown button present in the cabinet.

This is not happening in the current Ubuntu Linux. It is asking for confirmation.

So, there's no way for a shutdown to be clean is it happens immediately. I can only guess those other systems are really doing the equivalent of "shutdown -h now", which isn't a clean shutdown.  At best, it might sync the files and close the file systems. It certainly isn't cleanly shutting down the hundreds of little processes that Ubuntu desktop's run.   Have you timed "immediately"?  If it is under 10 seconds, I have doubts.  The amount of processes and the number and types of added hardware (internal and external) will lengthen the time required.

BTW, I have a similar system.  
```
$ inxi -bz
System:    Kernel: 5.15.0-119-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8 Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX **B450**-F GAMING v: Rev 1.xx serial: <filter> 
           UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD **Ryzen 5 5600G** with Radeon Graphics type: MT MCP speed: 4200 MHz min/max: 1400/4200 MHz 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: amdgpu v: kernel 
           Display: server: X.Org 1.20.13 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-119-generic LLVM 12.0.0) v: 4.6 Mesa 21.2.6 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
Drives:    **Local Storage: total: 19.10** TiB used: 3.36 TiB (17.6%) 
Info:      Processes: 444 **Uptime: 12d 23h 01m** Memory: 30.71 GiB used: 7.63 GiB (24.8%) Shell: bash inxi: 3.0.38

# Not using lots of RAM currently, 
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       6.7Gi       7.7Gi        71Mi        16Gi        23Gi
Swap:         4.1Gi       1.3Gi       2.8Gi

But a very busy computer right now for a 6-CPU system:
$ uptime
 10:51:46 up 12 days, 23:02,  4 users,  _**load average: 13.69, 14.49, 14.46**_
 
```

As you can see, I have lots of connected storage. It is all internal, using SATA connections on the motherboard. No USB involved at all.

Anyway, it needs to be rebooted (I've put that off since Saturday), so I'll do that when some long-running processes can be cleanly cancelled in the next hour and post the time to shutdown. Can't do it now, or I'll lose to much of the work that's already been done.  Looks like 38 minutes will be a good time to shutdown.

I hope I'm wrong for how long it takes to shutdown.  Most people worry about startup times, not shutdown.  We are always seeing startup times.
```
$ systemd-analyze 
Startup finished in 13.524s (firmware) + 2.459s (loader) + 6.349s (kernel) + 14.855s (userspace) = 37.189s 
graphical.target reached after 14.513s in userspace
```
Before you ask, on the same system, it is about 40 seconds. Most of that is related to periodic fscks on 16 different file systems it uses. I force an fsck every 30 days - well, the boot after 30 days, so it isn't exactly 30 days.  I tend to reboot about every 2-4 weeks, depending on the patches applied.

---

### Post by rupesh3 on 2024-09-06
I am not talking about time it takes to shutdown the system but the method to invoke the shutdown procedure while working on any desktop environment or window manager.

When the system is turned on and while performing any work when I press the shortcut key like Ctrl-Alt-p or power button in pc cabinet the system must shutdown without any confirmation.

Previously I used immediately in the sense shutdown without any confirmation.

---

### Post by rupesh3 on 2024-09-06
Here the actual problem is not all the desktop environments and window managers have the same shutdown procedure.

Some ask for confirmation and others not.

Another issue is some have shutdown shortcut with Ctrl Alt Del and the same shortcut is used to logout in other desktop environment.

---

### Post by TheFu on 2024-09-06
So, I just tested the shutdown on that computer.
It took 1:39.
I used 
```
sudo shutdown now
```
There weren't any prompts.  The delay was related to NFS and all the local file systems to be umounted.  I'd guess about 80% of the time to shutdown was from those.
BTW, 
```
$ uptime 
 11:47:14 up 4 min,  4 users,  load average: 0.63, 0.59, 0.28
```

So, I think you have the answer now. Use the command above for a safe shutdown.

---

