---
title: "[SOLVED] Gutsy won't recognize any USB memory devices."
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by mtaggart on 2007-12-14
I am running Gutsy on an IBM Thinkpad T41.  Last week Ubuntu suddenly stopped recognizing my USB memory devices (an Imation thumb drive, a Samsung YP-U2 mp3 player, a TrekStor hard drive, a SanDisk flash card reader).  My other USB devices (Logitech trackball mouse, Epson printer) DO work.  

I have tried these fixes (all gleaned from posts in Ubuntu Forums):
1.  Re-launching gnome-volume-manager

2.  Re-installing gnome-volume-manager (and restarting the computer)

3.  Removing the "usefree" setting from gconf-editor /system/storage/default_options/vfat/mount_options

Mounting the devices from the terminal also doesn't work, because the machine doesn't detect the devices at all.  ALL devices previously worked fine, and would auto-mount.

A very frustrating situation-- any advice would be much appreciated.  Thanks in advance for your help!

---

### Post by ebe0 on 2007-12-14
It seem your auto-mount option for USB storage devices is disabled  (I could be wrong). To know whether Ubuntu detects your USB storage devices at all, plug-in them and try this in terminal -- ***[COLOR="Red"]lsusb[/COLOR]***. Like this :

user@user:~$ [COLOR="Red"]lsusb
[/COLOR]
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. 
  
You should see the name(s) of your USB storage device(s) in the output (sometimes the name on the package may not appear in the output so run the command before plugging in the device and after, and compare the outputs).If you see some extra lines in the output then there is nothing wrong with the device and ubuntu it is detecting then. Now you'll have to manually mount them each time or modify /etc/fstab. Please let me know if it helped.

Or try this [http://ubuntuforums.org/showthread.php?t=639734](http://ubuntuforums.org/showthread.php?t=639734)

---

### Post by mtaggart on 2007-12-14
Yeah, unfortunately that's part of the problem.  Output for lsusb:
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

So the machine can't see the device (in this case the mp3 player, which always showed up with the Samsung specs before)-- therefore manually mounting it doesn't work either.  Output for sudo mount /dev/sda1 /home/username/Public:
(sadly, nothing)

Good ideas, though-- thank you for your reply!  I'll keep monkeying with it.

---

### Post by mtaggart on 2007-12-16
In desperation (I have to travel this week & had to have a fully operational machine), I backed up and re-installed Gutsy, thinking maybe a recent update had screwed things up.  Still no luck, so I re-installed again, this time with Feisty.  Again, no luck.

But I happened upon this thread:
[http://ubuntuforums.org/showthread.php?t=311816](http://ubuntuforums.org/showthread.php?t=311816)

& went through the very thorough & systematic troubleshooting provided by bapoumba line by line.  I discovered a very odd thing:  from a brand-new install & update, hal was loaded, but pmount was NOT.  Installed pmount using Synaptic, and everything works perfectly again. 

A very weird configuration error, to say the least-- if anyone has any info about why that happens, please share.  But for now, thanks to the ever-supportive Ubuntu Forum members, the problem is...

SOLVED!
:)

---

