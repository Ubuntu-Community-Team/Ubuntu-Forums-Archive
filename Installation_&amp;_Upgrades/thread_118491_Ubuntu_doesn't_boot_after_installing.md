---
title: "Ubuntu doesn't boot after installing"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by stefanv on 2006-01-17
Hello again,

I've managed to install Ubuntu on an old Compaq Proliant 2500 but now it doesn't boot. After POST, the bootloader (GRUB) is loading but he can not start Ubuntu. I get an error that he can't find root and is droping me to a shell. I need to mention that the system has 5 SCSI hdd's thar are put in 1 logical drive. On that drive I have 2 FAT16 partitions with the server configuration (they are made by the program that configures the BIOS) and 2 partitions for Ubuntu (one primary partition for root that has the boot flag on, and one logical for swap). Can someone help me to solve this problem?

[edit]when I installed Ubuntu, I could't choose where to install the bootloader (the installer didn't asked me)[/edit]

Thanks,
Stefan

---

### Post by Sef on 2006-01-17
> when I installed Ubuntu, I could't choose where to install the bootloader (the installer didn't asked me

If you do the default partition, GRUB is just installed automatically.  If you partition, then you get the choice of where to put the boot loader.

>  2 partitions for Ubuntu (one primary partition for root that has the boot flag on, and one logical for swap

Question:

I see you have root partition and a swap, but where did you put Ubuntu?

---

### Post by gravediggers on 2006-01-17
[QUOTE=Sef]I see you have root partition and a swap, but where did you put Ubuntu?[/QUOTE]

I'm guessing he meant all under / !

---

### Post by stefanv on 2006-01-17
Yes! One partition is for / and the other for swap. I don't think that the place where the bootloader was installed is the problem 'cose Grub is loading and is trying to start Ubuntu... The problem is that he can't find the root partition. I need to solve this problem very quick and I don't know what to do :(

---

### Post by stefanv on 2006-01-17
Nobody can help me? I think that Ubuntu it's on my hdd but he doesn't know how to start :). Please, tell me how to teach him!

---

### Post by gravediggers on 2006-01-17
Your system is setup a little different to most that I'm used to, so it is hard to understand your problem. GRUB is most likely on the MBR of the first drive in your array, as this is usually the default, and as BIOS is able to hook into it. The installer should have set GRUB up to load the kernel from where it is located. So I am having trouble seeing what the problem is!
 
Have you got a Ubuntu live CD (or even Knoppix) that you can boot to so you can do some diagnostics. A listing of your partitions and their types/size/bootable info, for a start, may help us to help you.

---

### Post by Sef on 2006-01-17
When you get your Live CD up, go to the terminal and type this:

sudo fdisk -l   that will give you a listing of your partitions types, their sizes, and bootable info.

---

### Post by gravediggers on 2006-01-17
Also could you post the exact GRUB error message that you get, including any error codes.

---

### Post by stefanv on 2006-01-18
Typing sudo fdisk -l in knoopix konsole dosen't show anything... I've even tried fdisk /dev/ida/c0d0 -l and fdisk KNOPPIX/dev/ida/c0d0 -l but I get the message "Cannot open ............" I've started QTPArted and there I have the following: device detected /KNOPPIX/dev/ida/c0d0 and 5 partitions. The first two are primary fat16 and are made by the setup CD that comes with the server (qtparted shows as /KNOPPIX/dev/ida/c0d03 and /KNOPPIX/dev/ida/c0d04). The third is a primary ext3 partition that is set to ACTIVE and has the "/" label. This is my root artition made by Ubuntu setup and qtparted shows this as /KNOPPIX/dev/ida/c0d01. Then, as /KNOPPIX/dev/ida/c0d02 and /KNOPPIX/dev/ida/c0d05 I have an extended partition (c0d02) and a logical partition for swap (c0d05). As qtparted shows this last two partitions, it seems that c0d02 is the parent of c0d05.
In my GRUB list, I have something with /dev/ida/c0d0p1 and I edited that row and put /c0d01 instead of /c0d0p1 but I still get the same error... He can't find the partition and is droping me to a shell

---

### Post by gravediggers on 2006-01-18
Sound like you are doing things right. I strongly suggest you check that the BIOS is the latest for that mobo, and if not, update it. GRUB is a powerful bootloader but is also very fussy when it comes to disk support. If the BIOS tells it crap, then it throws a wobbly, where as some other boot loaders just leave it for the OS to work out.

This  [GRUB Manual]("http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents") link may be of some help (particularly sections 14 & 15). You could also check out [GNU Grub]("http://www.gnu.org/software/grub/").

---

