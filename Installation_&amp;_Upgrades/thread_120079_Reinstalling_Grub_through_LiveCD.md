---
title: "Reinstalling Grub through LiveCD"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by harisund on 2006-01-20
Hello people !

I had a nice setup of Windows XP + Ubuntu dual boot. However, I have kind of messed up my Windows installation, and want to reinstall Windows. 

Of course, doing that, Windows will take over the MBR. 

I really do not want to lose my Ubuntu partition. What I had in mind was I would go ahead and do a Windows reinstall, lose my MBR, boot using Ubuntu LIVE CD and somehow make it identify the existing Ubuntu partition and restore the MBR the way it was before reinstalling Windows. 

I even have a saved copy of the current menu.lst on another machine.

Is this possible? I know I could reinstall Windows and then go ahead reinstall Ubuntu and get it back to where it is right now, but I would prefer not to after all the customizations I have done. 

I know it can be done, because Mepis has a "Restore MBR" feature where it automatically identifies existing operating systems and creates a boot list.

---

### Post by GTvulse on 2006-01-20
It is rather easy. You have already solved the major hurdle, having a bakup of your menu list.  This is how you do it: 

After reinstalling Windows, you boot up the Live CD, open a terminal window and type:
```

sudo su -
mount -t <filesystemtype> /dev/<yourpartition> /mnt
mount -t proc none /mnt/proc
chroot /mnt /bin/bash -l -i
su -
parted /dev/<yourdisk> set <partitionnumber> boot on
grub-install /dev/<yourpartition>
exit
exit
exit

```

Now you have returned to the normal shell prompt in the terminal window. Check thet [font=monospace]/boot/grub/menu.list[/font] is the one with your settings (it should be unless something very wrong happened) else restore from your backup, say from a floppy; something like this:
```

sudo mount -t vfat /dev/fd0 /media/floppy0
sudo cp /media/floppy0/menu.lst /boot/grub/

```

Now reboot your machine. It should come up again with your grub menu, and as you have iinstalled the grub bootloader in the actual ubuntu partition super block and marked that partition as active, the system boots up from that partition instead of the MBR which remains being the MS Windows one (and you can return to it by typing:
```

sudo parted /dev<yourdisk> set 1 boot on

```

Safely assuming that your MS Windows installation is in the first partiton of the disk.

---

