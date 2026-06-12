---
title: "dual-boot with two hdd problem.."
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by stunet on 2008-12-08
hi,

i have ubuntu dual-booted on another machine and it works just fine.

however on my main machine i really can't spare space to dualboot with the one hdd so i bought a second hdd and installed ubuntu on it.

went to restart and only windows loaded up. I used easyBCD to create the new entry so ubuntu will show up, but now I'm at a corner that I cant get out of.

it'll now list both OS'es but when i try to load ubuntu i get a command prompt that looks like:

grub >

now never done such a thing I'm totally stuck here and hope someone can assist on what I do next.

I really appreciate any help on this.

---

### Post by caljohnsmith on 2008-12-08
OK, how about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And please identify your partitions. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will help clarify what your setup is like. Lastly, would you be OK with Using Grub as your boot loader for both Ubuntu and Vista, or do you especially want to stick with Vista's boot loader and try and get Ubuntu working with EasyBCD?

---

### Post by stunet on 2008-12-08
either one works for me honestly, just need both OS'es to get detected :)

I'll try what you posted and will post back.

---

### Post by stunet on 2008-12-08
here is what came out:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00032c80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a791a79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   312578047   156288000    7  HPFS/NTFS
```

thinking on this, if i can go with using vista as the bootloader, that would be best since that drive is setup as the primary drive.

not sure if its worth mentioning, but both drives are SATA.

EDIT:
something of interest, when using the lie CD to look in the grub folder there wasn't a MENU.LST file to be found. should i just re-install ubuntu or is this still fixable?

---

### Post by caljohnsmith on 2008-12-08
Since your Ubuntu is a new installation, I would go ahead and reinstall it to your sda drive, and in the last step of the installation process, click the "advanced" button and specify /dev/sda as the drive to install Grub to. Once you get through the installation successfully, reboot, but set your BIOS to boot your Ubuntu drive. Then you should get the Grub menu OK and be able to boot Ubuntu. Once you can do that, adding an entry in the Grub menu for Vista should be easy. But let me know if you can get this far first, or if you run into problems.

---

### Post by stunet on 2008-12-08
hi,

i want to say that everything is running perfectly :D

grub found vista, ubuntu and vista both load and thats all I care about.

basically I just have the linux HDD as the drive to load first(had to adjust this in the BIOS)

thank you a lot caljohnsmith for all your help :)

---

### Post by caljohnsmith on 2008-12-08
Glad to hear that worked; cheers and have fun with Ubuntu and Vista. :)

---

