---
title: "USB not working? Things to try/do before posting..."
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by ender42 on 2007-03-14
So, I've been noticing a lot of people posting varying issues with USB in Ubuntu (primarily, because I've got issues with that, and those messages pop out at me).



Of course you should list in your post what version of Ubuntu you're running.

The next thing to do is remove your USB item, plug it in, and open a console to capture the output of 'lsusb' (or 'lsusb -v') and 'dmesg | tail'. 

Get info from 'lspci' and  'sudo fdisk -l'


According to:
[http://ubuntuforums.org/showthread.php?t=384134](http://ubuntuforums.org/showthread.php?t=384134)
'sudo udevmonitor' should also be monitoring events - ie: If you're running that command when you pull out and replug in your usb item, events should show up.


Other possible diagnostics

'cat /proc/scsi/scsi' should show devices on your machine (I believe)
'sudo lshw | less' should show if your OS is detecting your hardware (I believe)


Check the man pages on these commands:

'sudo lsmod | grep -i usb'



And you could try:
'sudo locate usb_storage'
'sudo modprobe usb-storage'



You can also try:
'pmount /dev/sd*whatever*'



Something else to check/try:
Add irqpoll to grub

'sudo gedit /boot/grub/menu.lst'
# defoptions=quiet splash noapic **irqpoll**
'sudo update-grub'




And I think that's a summary of everything I've been able to discover on what things you might try, and what output might help others diagnose your problem.  Please feel free to add other ideas below, I could use some :D

Of course the only solution I've found (ie: the one suggestion I got (irqpoll) didn't help) is to revert to an older version of Ubuntu that works....

---

