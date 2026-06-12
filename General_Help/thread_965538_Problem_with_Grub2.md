---
title: "Problem with Grub2"
date: 2008-10-31
forum: General Help
---

### Post by axelman on 2008-10-31
Hello, everyone.

Since I updated Grub 0.96 to grub 1.96 I can't boot my WinXP 64-bit HDD. It seems to chainload, but then it starts beeping and stalls. Also I've noticed grub2 doesn't support the 'map' command, so I don't know if that's no problem for Grub2 or it really is and I've to find a workaround.

Anyway, my configuration is:

* 2 HDDs (/dev/sda and /dev/sdb), each with four partitions: one for boot (sda1, sdb1 is unused), one for / in RAID0 (in both disks), one for swap (also in RAID0), and one formatted in NTFS for media in each disk.

* 1HDD (/dev/sdc) with one partition, where i've got Windoze installed.


I also tried installing (grub-setup) grub in /dev/sdc and swapping disks in the BIOS, but then it stalls in grub stage 1.5.


fdisk -l shows this (it's in spanish):

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x169d44b7

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2           59806       60801     8000370   fd  Linux raid autodetect
/dev/sda3             123       30395   243167872+  fd  Linux raid autodetect
/dev/sda4           30396       59805   236235825    7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x169d44b6

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         122      979933+  83  Linux
/dev/sdb2           59806       60801     8000370   fd  Linux raid autodetect
/dev/sdb3             123       30400   243208035   fd  Linux raid autodetect
/dev/sdb4           30401       59805   236195662+   7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdc: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3bc03bbf

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1       24319   195342336    7  HPFS/NTFS
Nota: el tamaño del sector es 2048 (no 512)



and my /boot/grub/grub.cfg (only the relevant part) is:

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.27-7-generic" {
	linux	(hd0,1)/vmlinuz-2.6.27-7-generic root=/dev/md2 ro quiet splash 
	initrd	(hd0,1)/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
	linux	(hd0,1)/vmlinuz-2.6.27-7-generic root=/dev/md2 ro single
	initrd	(hd0,1)/initrd.img-2.6.27-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	(hd0,1)/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional x64 Edition (on /dev/sdc1)" {
	set root=(hd2,1)
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


I've tried so many thinks I don't know what else to do. Does aybody have any clue?

Thanks.

---

### Post by fjgaude on 2008-10-31
Consider where your MBR might be, which drive. Then consider using these commands to get the system to point to the right .cfg file to boot from:

```
# sudo grub
grub> find /boot/grub/stage1
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
```

Then if necessary, out of grub and onto another command line:

```
sudo grub-install /dev/sda
```

Of course use the drive lettering for your setup.

---

### Post by axelman on 2008-11-01
Thanks a lot for answering so fast.

It seems I overwrote by mistake the /dev/sdc boot sector somewhere in the process of installing grub, since I changed several times the order of the disks in the BIOS, so it couldn't boot at all.

I just swapped /dev/sdc and /dev/sda and run the fixboot command from the Windoze install disk and it boots fine now.

The problem is I want the windoze HD back at /dev/sdc (grub's HD2) and boot it by chainloading from grub2, but I can't find the way to map the HDs as in legacy grub, and winoze won't boot unless it thinks it is installed at HD0.

Any ideas?

Thanks in advance.

PS: Also, I'd like to point out that information regarding grub2 is quite sparse and I haven't been able to find a decent manual so far. May anyone give me a link?

---

### Post by phidia on 2008-11-01
There are links to the mailing list and wiki from [here]("http://www.gnu.org/software/grub/grub-2.en.html").

AFAIK grub2 is still beta-that's why it isn't available from the repos.

---

### Post by caljohnsmith on 2008-11-01
I was looking over the [command list comparison between legacy Grub and Grub2]("http://grub.enbug.org/CommandList"), and unfortunately it looks like you're right about there not being an equivalent map command in Grub2. As a workaround, you could modify the "boot.ini" file in the Windows root directory to use a different "rdisk(0)". Since you have 3 HDDs, you could try "rdisk(1)" or "rdisk(2)", and I think one of those should work when you chain load Windows from Grub. In other words:
```
[boot loader]
timeout=30
default=multi(0)disk(0)[COLOR="Blue"]rdisk(1)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(1)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

```
If you decide to give it a shot, let me know how it goes. :)

---

### Post by axelman on 2008-11-01
> **caljohnsmith said:**
> I was looking over the [command list comparison between legacy Grub and Grub2]("http://grub.enbug.org/CommandList"), and unfortunately it looks like you're right about there not being an equivalent map command in Grub2. As a workaround, you could modify the "boot.ini" file in the Windows root directory to use a different "rdisk(0)". Since you have 3 HDDs, you could try "rdisk(1)" or "rdisk(2)", and I think one of those should work when you chain load Windows from Grub. In other words:
```
[boot loader]
timeout=30
default=multi(0)disk(0)[COLOR="Blue"]rdisk(1)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(1)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

```
If you decide to give it a shot, let me know how it goes. :)


Thanks a lot, but it didn't work. After chainloading there's just a black screen and a flashing cursor. If it tried to boot, I'd see a message telling me the bootloader can't find the win kernel or something.

---

### Post by caljohnsmith on 2008-11-01
So did you try both "rdisk(1)" and "rdisk(2)", and neither worked? Could be your RAID setup is the issue. I must ask though, why do you want to use Grub2 at this point? As you can all ready see, it doesn't even support all the features of legacy Grub. What is your particular reason for using Grub2? 

If you really want to get Grub2 to boot your Windows, you might need to play with the "disk(X)" parameter also in the boot.ini file. You can read more about it here:

[http://support.microsoft.com/kb/314081](http://support.microsoft.com/kb/314081)

Anyway, good luck.

---

### Post by axelman on 2008-11-01
> **caljohnsmith said:**
> So did you try both "rdisk(1)" and "rdisk(2)", and neither worked? Could be your RAID setup is the issue. I must ask though, why do you want to use Grub2 at this point? As you can all ready see, it doesn't even support all the features of legacy Grub. What is your particular reason for using Grub2? 

If you really want to get Grub2 to boot your Windows, you might need to play with the "disk(X)" parameter also in the boot.ini file. You can read more about it here:

[http://support.microsoft.com/kb/314081](http://support.microsoft.com/kb/314081)

Anyway, good luck.


Well, win HD/partition is not in RAID, is in a separate (sdc) disk. I tried changing 'rdisk' and 'disk' parameters, but neither worked. The main point for trying grub2 is that it supports linux soft RAID filesystem, and I'm sick of having such complex partitioning schemes just for needing a separate (and fixed size) /boot partition, so I just wanted to give it a try. I guess I'll have to wait until there's a stable and well-tested branch.

Thanks a lot.

---

