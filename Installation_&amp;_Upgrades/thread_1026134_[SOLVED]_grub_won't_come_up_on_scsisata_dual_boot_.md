---
title: "[SOLVED] grub won't come up on scsi/sata dual boot installation"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by meself on 2008-12-30
i have repetedly installed windows xp on my sata drive and Ubuntu 8.04 on my scsi drive in the same machine.  selecting different choices during installation in the "advanced" screen from the "ready to istall" screen from the istallation sequence.

but i keep getting a windows xp only machine with no grub boot selections coming up at startup.

i have dual boot running successfully on two separate scsi harddrives on my win2k/ubuntu8.04 machine.  and also on two separate sata harddrives on another winxp/ubuntu8.04 machine.  but here, i am using _two different kinds of drives_ and the grub loader doesn't seem to want to work with that.

i also tried using boot magic which is a boot loader that comes with an old copy of partition magic.  but that runs under windows, doesnt see or find my linux scsi drive.

is there a way to get my grub to work with two different kinds of harddrives?  or some other alternate boot loader that does not run under windows that might be able to locate the two installations on two different kinds of drives?

---

### Post by xenolalia on 2008-12-30
So, for example, if the hard drive you were installing to was /dev/sdb, at the last screen during installation when you open the "Advanced" dialog, do you choose to install to /dev/sdb or /dev/sdb1?  In my experience, either usually works fine, but for your special circumstances, you might try whichever one you're not currently doing if you haven't already.

Good luck!
Xenolalia

P.S. I'm kinda'/sorta' new to Linux so you probably ought to take my advice with a grain of salt, but as far as I know, the worst my suggestion could do is nothing at all.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Does it boot right into winblows?

---

### Post by meself on 2008-12-30
yes that's correct.  it boots right into windows xp.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Reboot then hit esc to go into the boot menu and choose the drive with ubuntu on it.

---

### Post by meself on 2008-12-30
no luck so far but thank you both for those last two suggestions.

---

### Post by tad1073 on 2008-12-30
Try this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Bluebell392 on 2008-12-30
It sounds like grub wasn't installed. You have to restore grub using the [super grub disk]("http://supergrubdisk.org").

---

### Post by caljohnsmith on 2008-12-30
If you installed Grub to the MBR of your Ubuntu drive by specifying /dev/sdb (or whichever is the Ubuntu drive) under the "advanced" settings in the installer, then probably all you need to do is change your BIOS to boot the Ubuntu drive first instead of the Windows drive. If that doesn't solve your problem, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by tad1073 on 2008-12-30
deleted

---

### Post by meself on 2008-12-31
yes, caljohnsmith, that worked.  guess it was logical enough i should have tried it.  but yes, changing the bios boot priority to the linux scsi drive where grub resided worked.  i now have a dual boot system.

thank you & best wishes to all who contributed suggestions to my delema!

---

