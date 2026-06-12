---
title: "change my slave into master"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by thedarkend on 2006-02-15
currently have ubuntu installed on the slave drive on my computer. Win98se is on the master. Grub is being used to start up linux...

Basically want to purge the evil from my computer by doing the following.
1) Change jumper settings on my slave to make it the master
2) Make it so that my current ubuntu install starts up on boot up as the newly reassigned master drive
3) Reconnect and change jumper settings on old master so it's the slave and reformat the drive to be used under ubuntu

Basically my question is more regarding step 2. Want to know how to safely make ubuntu start up as the master drive without having to re-install or lose any of the information on the drive.

Much Thanks
thedarkend

---

### Post by o_fortuna on 2006-02-15
[QUOTE=thedarkend]currently have ubuntu installed on the slave drive on my computer. Win98se is on the master. Grub is being used to start up linux...

Basically want to purge the evil from my computer by doing the following.
1) Change jumper settings on my slave to make it the master
2) Make it so that my current ubuntu install starts up on boot up as the newly reassigned master drive
3) Reconnect and change jumper settings on old master so it's the slave and reformat the drive to be used under ubuntu

Basically my question is more regarding step 2. Want to know how to safely make ubuntu start up as the master drive without having to re-install or lose any of the information on the drive.

Much Thanks
thedarkend[/QUOTE]
I don't know if changing the drive to master will make a difference -- it should just be picked up by the BIOS, and everything *should* still work.

Still, it's much better to be safe than sorry. Definitely back up any important information on the drive before you try to handle it. I've made that mistake once before; won't do it again.

---

### Post by thedarkend on 2006-02-15
Already tried doing that prior to the post. 

Swapped the jumper on the slave to master. Loaded up the bios and changed the settings to recognize the new master hdd. But it didn't boot.

I think that there is nothing written to the MBR of the slave drive and that I need possibly to set-up grub on that hdd.

Any thoughts of if this is the right path?

---

### Post by AllenGG on 2006-02-15
HI, AS Fortuna said, set it up with the BIOS.  Try using "cable select" on the HDD's so that the BIOS controls the drive settings.
When you reboot UBUNTU will load, then you have to go into disk partitioning the secondary or "slave".

---

### Post by Ocxic on 2006-02-16
I've read somewhere in these forums that the ubuntu installation hard codes itself to the specific drive it's installed on so changing the drive placment might not work as expected, there is a way to fix/change this but I'm unsure about how. and yes you may have to install grub to the drive wich is reletivly easy using a live cd.

---

