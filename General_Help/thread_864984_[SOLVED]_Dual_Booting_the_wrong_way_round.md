---
title: "[SOLVED] Dual Booting the wrong way round"
date: 2008-07-20
forum: General Help
---

### Post by tez1982 on 2008-07-20
I've unfortunately got to install windows as I have to use some custom software for work which, despite many efforts, will not run on ubuntu.

I've already got ubuntu on my desktop and laptop PC and am very happy with it.

I've found many tutorials for dual booting but they all start by installing windows first. Is it possible to do it the wrong way round and install windows XP as a dual boot after ubuntu is already installed?

Thanks

Tez

---

### Post by PmDematagoda on 2008-07-20
You can install Windows again, but you would need to reinstall GRUB to the MBR again since the Windows installer will overwrite GRUB, you can easily reinstall GRUB back onto the MBR with the help of the [Super GRUB Disc]("http://forjamari.linex.org/frs/download.php/987/super_grub_disk_0.9726.iso"), after installing Windows and then reinstalling GRUB to the MBR, you can then setup GRUB to dual-boot both Ubuntu and Windows.

---

### Post by scragar on 2008-07-20
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

hardest part is rebuilding grub afterwards, but it's still not too hard.

---

### Post by tez1982 on 2008-07-20
Thanks guys, appreciate the help!

---

### Post by fsmithred on 2008-07-20
Yeah, there are a bunch of ways to do it. Is this going to be on the desktop or the laptop? Same hard drive or a second hard drive? 

Here are some options:

1. Install vmware or virtualbox, then install XP inside a virtual machine. This is not really dual-boot, since you'll be able to run windows without stopping linux.

2. Disconnect the ubuntu drive, put in a new drive and install XP. Then hook up the XP drive as slave (or second drive) and put the ubuntu drive back in. Edit /boot/grub/menu.list to remap the windows drive and boot it. This way is kinda nice, because you don't overwrite the windows bootloader. If the linux drive dies, you just make the windows drive the first hard drive, and it works.

3. Same as 2, but leave the XP drive as the first drive, and the linux drive second. Then you boot a live cd and edit menu.list and fstab to correspond to the new location (probably /dev/sdb) and install grub onto the mbr of the first drive.

4. Repartition and put both linux and windows on the same drive. There are several ways to do this. (looks like someone provided a good link for this while I was typing)

---

