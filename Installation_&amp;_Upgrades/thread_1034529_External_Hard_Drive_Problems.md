---
title: "External Hard Drive Problems"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by Miamiandy on 2009-01-08
I want to boot my old laptop's hard drive as a usb external, so I bought a case for it.  However, I keep getting errors, and can't seem to load it.  I formatted it on a Windows computer computer to see if that was the problem, since it mentioned an unclean log file, but that didn't do anything.  Attached is my error message, "JulianHoffman" is my drive name, in case I ever lose it.  Please help me figure this out!  I'm running Ibex.

$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/JulianHoffman -o force  Or add the option to the relevant row in the /etc/fstab file:  /dev/sdb1 /media/JulianHoffman ntfs-3g force 0 0

I tried Choice 2, but it doesn't do anything that I can tell?  Just describes the mount options for the terminal.  I'm not really good at this yet, as I just made the switch to Ubuntu, so please be as detailed as possible!  I really appreciate it!!

---

### Post by aeronotix on 2009-01-08
Please can you post the output of ```
sudo fdisk -l
```

---

### Post by Miamiandy on 2009-01-08
Got it working!  I don't know what the hell I didn't do before, but I followed the Safely Disconnect Hardware step 10 more times (literally), and I guess that finally fixed the logfile.  Thanks!

---

