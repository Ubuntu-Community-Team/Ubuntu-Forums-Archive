---
title: "[URGENT] dual boot and mounting Windows partitions"
date: 2008-09-15
forum: Hardware
---

### Post by kakyoism on 2008-09-15
I dual boot WinXP (two partitions) and Hardy (one partition) on a AMDx2 destop machine with a 400GB harddrive).

There was a power-outage the other day and when my machine was back on,
I can't boot into WinXP anymore, nor can I mount the two NTFS partions under Hardy.
The error message I got when trying to mount them is:
```
$LogFile indicates unclean shutdown (0, 0) Failed to mount ./dev/sda1': 
Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: 
Choice 1: if you have Windows then disconnect the external devices 
by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar 
then shutdown Windows cleanly. 
Choice 2: If you don't have Windows then you can use the 'force' option 
for your own responsibility. For example type on the command line: mount 
-t ntfs -3g /dev/sda1 /mediadisk -o force, or add the option to the 
relevant row in the /etc/fstab file: /dev/sda1 /media/disk ntfs -3g force 
0 0

```

Any idea how I can get my Windows partitions back??
I have important work on them!
Thanks a bunch!

---

### Post by briantipton on 2008-09-15
I have had problems with NTFS partitions getting messed up before.  The only solution is to boot into windows and clean them up and then go back to Linux and work.  It sounds like you cannot boot into Windows though.  

What error do you receive when you try to boot into XP?

---

### Post by kakyoism on 2008-09-15
When booting into Windows, I can see the "Windows XP" screen, but shortly after that, it showed the screen for choosing Safe Mode, etc. When I chose "The last correct configuration" something, the machine just went back to the initial boot-up and ask me to choose OS again, hasn't tried Safe Mode though...

---

### Post by briantipton on 2008-09-15
Can you get to a C: prompt and view the contents of your boot.ini?

---

### Post by physicusman on 2008-09-16
Can you possibly hookup your hd to another windows pc and do a checkdisk scan? That has been the easiest way that I have done it. I dual boot as well on my laptop, but this method should work for you. You may also want to do a defrag as well on the windows partition to get things rolling.

---

