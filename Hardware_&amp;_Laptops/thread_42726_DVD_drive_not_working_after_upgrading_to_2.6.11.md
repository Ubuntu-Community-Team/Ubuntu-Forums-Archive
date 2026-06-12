---
title: "DVD drive not working after upgrading to 2.6.11"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Pausanias on 2005-06-19
Hi

I upgraded to the 2.6.11 because the nvidia driver is a lot more stable there (I was getting daily crashes with 2.6.10, none with 2.6.11 for over two weeks).

Unfortunately, I can't get my DVD-RW detected (it doesn't show up at all in dmesg, so no /dev/scd0 is created).

Did lots of searching---no solution. I am attaching my dmesg from the 2.6.10 bootup (cdrom is detected) and the 2.6.11 bootup (cdrom is not detected).

Thanks for your help!

P

Edit: Oh, and my kernel boot line is


/boot/vmlinuz-2.6.11-1-686 root=/dev/sda6 ro quiet splash i8042.noacpi noinotify

the i8042.noacpi is to get the keyboard working, noinotify is to get GNOME not to crash. Neither of these should affect cdrom detection, should they?

---

### Post by zonak on 2005-06-19
I have the same problem, I had to upgrade to kernel 2.6.11 because of SATA problems, and now canot use my DVD-ROM. I hope there is a sollution to this problem. ](*,)

---

### Post by berserker on 2005-06-19
Attached is my /usr/src/linux/.config file for 2.6.11.  Compare it to yours to ensure you've enabled everything (as a module or built in) for your kernel.  My DVD+RW works fine in 2.6.11 and 2.6.12 as well (downloaded from kernel.org).

---

### Post by zonak on 2005-06-19
I think the problems is not with a driver or kernel module.

In dmesg i see the following error:

PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1

and there is no info about any of the devices (DVD-ROM and DVD-RW) listed there.

---

### Post by berserker on 2005-06-19
Check the IDE/PCI settings in your config file.  I could not boot the 2.6.11 kernel until I enabled support to be built in.  The default settings did not work for me.  Compare my config file closely to yours and see if their are any differences that could affect your IDE/PCI settings.

---

### Post by zonak on 2005-06-19
I am using the kernel version installed through synaptic, I will do an oldconfig to see what is set up, thank you ...

---

### Post by zonak on 2005-06-19
OK,

Problem solved.

First of all THANK YOU very much berserker, you made my day  \\:D/ 

I compared your config with the one from the standard kernel that I am using, and all I had to do is load the following modules:

ide_generic
ide_cd

in order to make the changes permanent I just added this modules in /etc/modules

Pausanias, I hope this will help you too.

---

### Post by Pausanias on 2005-06-20
[QUOTE=berserker]Check the IDE/PCI settings in your config file.  I could not boot the 2.6.11 kernel until I enabled support to be built in.  The default settings did not work for me.  Compare my config file closely to yours and see if their are any differences that could affect your IDE/PCI settings.[/QUOTE]
 Hi berserker

I tried what you said. I recompiled the 2.6.11 kernel with some of your IDE functions turned on. This caused the DVDRW to be detected, but it comes in as /dev/hdc. It worked, but for some reason, dma is disabled on it (I cannot turn it on) and CDs can only be read at very slow speeds. It easily was ten times faster when I ran it under 2.6.10.

If you look at my dmesg.2.6.10.txt posted above (my fully working setup), the DVDRW was being detected by ata_piix and installed under scsi1 and /dev/scd0 using SCSI emulation. Comparing with dmesg.2.6.11.txt, it seems that the line beginning with scs1 is still there, but no DVDRW drive comes up.

In short---anybody know of a way to get the cd rom drive working in 2.6.11 using the scsi emulation that worked so well in 2.6.10, and which made it come up as /dev/scd0?

---

### Post by berserker on 2005-06-20
zonak, you're welcome!  :) 

I had to add "hdc=ide-scsi" to my /boot/grub/menu.lst like so:

title		Ubuntu, kernel 2.6.11 
root		(hd0,4)
kernel		/vmlinuz-2.6.11 root=/dev/hda7 ro quiet splash hdc=ide-scsi
savedefault
boot

and also add "ide-scsi" to /etc/modules in place of "ide-cd" in order to enable SCSI emulation for my DVDRW drive.  You'll have to reboot in order for these changes to take effect.

hdparm only works with "hd" devices so if you enable SCSI emulation then you won't be able to enable DMA on that drive (at least with hdparm).

So, without SCSI emulation, you should have "ide-cd", "ide-generic" and "ide-disk" in your /etc/modules and an entry in /etc/hdparm.conf like this:

/dev/hdc {
        dma = on
}

to enable DMA for your DVDRW.

Do a "lsmod | grep piix" to see if you have piix loaded as a module.  In my case I included it in the kernel and checked this by doing a search for PIIX in my kernel config file.

Hope (some of) this helps!

---

### Post by Pausanias on 2005-06-20
I fixed the problem by installing the 2.6.12 kernel via the breezy apt sources. Now everything works just fine. No need to recompile the kernel at all or change any options to get the DVDRW working. Note that if you are using the nvidia driver, you will also need to upgrade to gcc-3.4 and all dependencies, because you will need the kernel sources to compile nvidia.
After I did that, I reverted to hoary and all seems well.

berserker: I belive ide-scsi is deprecated in the 2.6 series kernels... it may not be supported in the future. 2.6.12 should detect your drive without the need to recompile the kernel.

zonak: hmm, I couldn't get any ide detection going in 2.6.11 by adding those modules to /etc/modules. I had to recompile the 2.6.11 kernel with ide on, and then my CD ROM would be detected (but would show up as hdc *without* any ability to control dma and hence get it working at a higher speed).

---

### Post by berserker on 2005-06-20
[QUOTE=Pausanias]Note that if you are using the nvidia driver, you will also need to upgrade to gcc-3.4 and all dependencies, because you will need the kernel sources to compile nvidia.[/QUOTE]

Interesting.  I'm using 2.6.12 and recompiled the Nvidia driver using gcc-3.3.5 without any problems.  

Perhaps because I'm using a stock 2.6.12 from kernel.org?

---

### Post by Pausanias on 2005-06-20
[QUOTE=berserker]Interesting.  I'm using 2.6.12 and recompiled the Nvidia driver using gcc-3.3.5 without any problems.  

Perhaps because I'm using a stock 2.6.12 from kernel.org?[/QUOTE]
 I think you're right. The Ubuntu kernel source Makefile came in requiring gcc-3.4, and I didn't want to change anything there. I haven't noticed any adverse effects of upgrading to gcc-3.4 (and dependencies, including newer libc).

---

### Post by zonak on 2005-06-20
I have enabled the DVD-ROM and the DVD-RW as hda and hdb respectivly, so obviously i am not using the SCSI emulation, but I was also unable to turn the DMA on. So next step: I am trying the advice from berserker, I'll let you know what happens.

I tried the instructions from berserker, and a strange thing happened. The first time I inserted a dvd in the dvd-rom I got 8 devices mounted and my mtab looks like this:

/dev/scd1 /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=zonak 0 0
/dev/scd2 /media/cdrom-1 iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0
/dev/scd3 /media/cdrom-2 iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0
/dev/scd4 /media/cdrom-3 iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0
/dev/scd5 /media/cdrom-4 iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0
/dev/scd6 /media/cdrom-5 iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0
/dev/scd7 /media/cdrecorder iso9660 ro,nosuid,nodev,sync,uid=1000,gid=1000 0 0

I don't know what happened  :roll: 

After that only one device got displayed on the desktop, but the mtab remained the same ...

I gues I'll deal with it tomorrow ...

---

