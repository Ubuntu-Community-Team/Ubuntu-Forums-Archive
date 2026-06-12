---
title: "3 OS's - now i want to remove windows..."
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by pedrocortez on 2009-07-05
Hi 

I'm very happily converted to Linux and have a multiboot system with Ubuntu Hardy for home tasks, / Ubuntu Studio 8.04-rt for my hobby music composition / and Win XP

I now want to remove XP and replace it with the 32-bit edition of 64Studio to try that out in comparison to Ubuntu Studio. 

I want to make sure my Hardy and UStudio installs stay intact, but use the win partition for 64Studio. 

I have the iso DVD ready to install 64 Studio

I'm guessing it will ask me for a target partition to install , and I'm hoping that when its complete i will be able to see Hardy/Ustudio and 64Studio as the 3 boot choices in Grub. 

i THINK i have Grub installed already as part of the Ubuntu installs. 
At the moment , when i boot i get black screen , with my boot choices ( and i see some words about Grub flash by just before hand. )

Assuming I do have Grub installed, and I'm not relying on Windows MBR will i be OK just to install 64 STudio over the existing XP partition ? 
How can i check the Grub install ? 

The win partition is 90Gig - so lots of available space. 
Anything special about swap partitions etc ? 

Any thoughts/help on this multi-boot set up ? 

Cheers
Pete

---

### Post by presence1960 on 2009-07-05
I would use Gparted from the Ubuntu live CD or gparted Live CD to remove the windows partition and format it to the filesystem you will use with the new install. Then choose "manual" option when you get to the partitioner window of the install process. Highlight the former windows partition and set parameters for that partition. You should really install GRUB to the partition and chainload it off which ever GRUB menu is currently in your MBR. I'll show you an example from my menu.lst. I chainload Windows 7 RC and Sabayon 4.1:
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title          Microsoft Windows 7 RC
rootnoverify   (hd1,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title          Sabayon 4.1
rootnoverify   (hd0,4)
chainloader    +1
```

when I pick sabayon at boot it points to Sabayon's GRUB which is installed in it's partition which then gives me Sabayon's GRUB menu.

The advantage of chainloading over entering manual entries is that when the chainloaded OS updates it's kernels you have to do no editing to boot the new kernels because they are already updated in the chainloaded OS's menu.lst only. If you boot from another menu.lst you must manually edit that menu,lst to get the new kernels to boot.

---

### Post by presence1960 on 2009-07-05
BTW here is where you choose where to install GRUB from the install process. Yours may look a little different, but every linux distro gives the option where to install GRUB. Click the advanced button and choose the install partition (ex. sda4- yours will match your set up)

---

### Post by pedrocortez on 2009-07-05
Hi P1960 !

many thanks for your help. 

I need to digest what you advised and then I'll go ahead. 

Much appreciated

Pete C

---

