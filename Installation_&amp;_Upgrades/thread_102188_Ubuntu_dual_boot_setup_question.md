---
title: "Ubuntu dual boot setup question"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by firefly2442 on 2005-12-11
So I have one IDE hard drive with Ubuntu installed right now.  I'm getting another SATA hard drive for Christmas.  I would like to install windows on that drive so I can dual boot.  What do I need to do to ensure the MBR doesn't get messed up so I can still boot into either operating system?  Thanks! :)

---

### Post by taurus on 2005-12-11
When you install windows on that new SATA, it will wipe out GRUB on MBR and installs it own crappy bootloader.  Therefore, you need to use a LiveCD and boot it.  Mount your Ubuntu, modify /boot/grub/menu.lst and ad an entry for XP, and re-install GRUB on MBR again...

---

### Post by JoshHendo on 2005-12-11
Ok.
1. Install windows first :P. I have always found this easier becuase then grun will add windows to the dual boot when installing ubuntu, you don't have to do it manaully.
2. Make sure the second HDD is a master drive too. If that can't be done, split the first one into 2 for just the operating systems, and the second one you can use for storage (that is what I had to do).
3. Go ahead, try it out. As long as you have a bootable floopy with fdisk, you can fis *anything* (IE. To fix the MBR, type in "fdisk /mbr" (no quotes) and it will restore the windows MBR).
4. Make sure you have access to the internet on another computer so you have access to these forums. 5. Make sure you have backups of all your data. Hmm, I think that is all you need to know :P :)

-Josh

---

### Post by nolan- on 2005-12-13
Hi,
I'd suggest disconnecting the IDE drive and then installing windows on SATA, then just shutdown and plug the IDE back in when windows has installed.
Set the bios to boot off the IDE and edit /boot/grub/menu.lst to add windows in ubuntu.
I think it will be :-
```

title           Windows
root            (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader     +1

```

I have a similar setup, and if it's windows xp that you are going to install in my experience it has problems installing on SATA if IDE is connected so you may HAVE to disconnect the IDE anyhows.

Good luck!

---

### Post by charles nicholls on 2006-09-16
Nolans way is definatly the way to go.
Unplug your Ubuntu drive and install windows, plug the drive back in and in bio's boot from ubuntu, edit reboot and press esc to choose Os.
Thanks Nolan.
My vista rc1 menu with vista on Sata, 

# should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title              Windows vista
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by nolan- on 2006-09-16
> **charles nicholls said:**
> Nolans way is definatly the way to go.
Unplug your Ubuntu drive and install windows, plug the drive back in and in bio's boot from ubuntu, edit reboot and press esc to choose Os.
Thanks Nolan.


Pleasure to help anyone out!

This doesn't seem to be an Ubuntu problem, more of a M$ problem O:)

---

