---
title: "Installing Ubuntu on USB Stick (Done But With Problems)"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by edh649 on 2009-07-29
ok,
I have so far installed Ubuntu to a USB stick but the problem is is that when I unplug the usb stick I want to load windows vista but it just comes up with grub error 17.
I think whats happened is ive got grub stage 2 on the usb stick so when I unplug the USB stick it  doesn't work. 

thanks,
edh649

---

### Post by stlsaint on 2009-07-29
well lets start from the begining...did u split your partitions correctly for dual booting! if you just installed ubuntu over windows than you probably did the dual boot wrong...list step by step instructions on exactly what your intent was and what you did to get to where you are now!!

---

### Post by ajgreeny on 2009-07-29
It sounds as if you need to put grub on the usb drive, restore the windows MBR with the windows install CD, or if you don't have one with supergrub, and then set the machine to boot first from the usb drive and second from the hard drive.  Now if the usb is attached, grub will appear and allow you to boot to either windows or ubuntu, but if it isn't, the hard disk will go straight to windows.

@ stlsaint-  Note the OP has ubuntu on a usb drive, not a hard drive partition, so the partitioning is probably irrelevant.

---

### Post by presence1960 on 2009-07-29
> **ajgreeny said:**
> It sounds as if you need to put grub on the usb drive, restore the windows MBR with the windows install CD, or if you don't have one with supergrub, and then set the machine to boot first from the usb drive and second from the hard drive.  Now if the usb is attached, grub will appear and allow you to boot to either windows or ubuntu, but if it isn't, the hard disk will go straight to windows.

@ stlsaint-  Note the OP has ubuntu on a usb drive, not a hard drive partition, so the partitioning is probably irrelevant.

+1

Right on the $$ ajgreeny. If GRUB is on the MBR of the internal disk it is going to look to the ubuntu install on USB drive for menu.lst. Since it isn't connected it can't find it. 

I would restore windows bootloader to MBR of internal disk, [see here]("http://ubuntuforums.org/showthread.php?t=1014708").

Then plug in the USB drive and restore GRUB to MBR of the USB drive like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hdx)", where x is the number of the USB drive to install GRUB to MBR.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.



```

The final thing you need to do is set your BIOS to boot from USB or Removable first, then CD, then hard disk. This way when your flash drive is plugged in when you boot it will boot GRUB from the flash drive instead of windows bootloader from the internal disk. If your flash drive is unplugged when you boot windows will boot right up.

---

### Post by edh649 on 2009-07-31
ok thanks - ill try that
but if i plug it in to another computer and on BIOS set it to load from the usb on another machine will linux load on that machine??
basically i want to make a portable USB drive Linux
thanks,
ed

edit-
ok,
ive just tried all of what you said and windows works but when i load the USB stick it comes up with: "Error 17: Cannot load selected Partition"

---

