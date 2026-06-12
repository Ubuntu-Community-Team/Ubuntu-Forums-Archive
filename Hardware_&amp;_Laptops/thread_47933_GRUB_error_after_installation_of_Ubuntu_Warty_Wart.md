---
title: "GRUB error after installation of Ubuntu Warty Warthog 4.10"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by GeertVc on 2005-07-10
Hi,

I'm completely new to the Ubuntu Linux distribution, but I definitively want to give it a try.

I'm trying to install Ubuntu on one of my 'old' PC's, with the following (most important items of) specs:

[list]
[*]PentuimI - 133MHz
[*]Maxtor Harddisk 2F040L0 - 40GB
[*]98MB RAM
[/list]

The harddisk has been low-level formatted before installation, with the PowerMax (from Maxtor) disk analyser program.  All tests have run and the harddisk has been succesfully past all tests.

When finalising the Ubuntu installation, it reboots (so far, everything seems to be installed fine, didn't get any error at all).

I'm rebooting with the following sequence:  first CD-rom, then Harddisk.

I get the following error, _immediately after rebooting for the first time_:
[list]
[*]Boot failure from CD-rom => [COLOR=Blue]**normal, since I had to remove the CD-rom to rebooting after the Ubuntu installation**[/COLOR].
[*]GRUB Hard Disk Error => [COLOR=Red]**this one, I don't know why...**[/COLOR]
[*]system hangs...  [-X 
[/list]

When changing the boot order (so, first harddisk, then CD-rom), I get some other errors:

[list]
[*]GRUB loading stage 1.5 => [COLOR=Blue]**seems OK**[/COLOR]
[*]GRUB loading, pleas wait => [COLOR=Blue]**OK, why not?**[/COLOR]
[*]Error 18 => [COLOR=Red]**what does this mean?  what's causing this?**[/COLOR]
[*]system hangs...  [-X 
[/list]

Hope someone can help me in this matter...  ](*,) 

Best rgds,

--Geert

---

### Post by GTvulse on 2005-07-10
[QUOTE=GeertVc]Hi,

When changing the boot order (so, first harddisk, then CD-rom), I get some other errors:

[list]
[*]GRUB loading stage 1.5 => [COLOR=Blue]**seems OK**[/COLOR]
[*]GRUB loading, pleas wait => [COLOR=Blue]**OK, why not?**[/COLOR]
[*]Error 18 => [COLOR=Red]**what does this mean?  what's causing this?**[/COLOR]
[*]system hangs...  [-X 
[/list]

--Geert[/QUOTE]

You probably created a boot partition ** at the end of the disk** or **after** the first 7 Gb and yet, you didn't activate LBA mode in your BIOS (32 bit access mode usually activates LBA mode in most modern BIOS setups). Or the BIOS is old... See [this thread in the Gentoo forums](http://forums.gentoo.org/viewtopic-t-122656.html) for documentation and comments on this issue.

I would suggest you reinstall Ubuntu, making sure that the boot partition is the first one in the disk.

---

### Post by GeertVc on 2005-07-10
[QUOTE=dradul]You probably created a boot partition ** at the end of the disk** or **after** the first 7 Gb and yet, you didn't activate LBA mode in your BIOS (32 bit access mode usually activates LBA mode in most modern BIOS setups). Or the BIOS is old... See [this thread in the Gentoo forums](http://forums.gentoo.org/viewtopic-t-122656.html) for documentation and comments on this issue.

I would suggest you reinstall Ubuntu, making sure that the boot partition is the first one in the disk.[/QUOTE]
Well Alejo...  

I was a bit misleaded by the BIOS in the PC!   :roll: 
When I performed an auto detection for the HDD whilst in BIOS mode, there was a sentence at the bottom of the screen saying that SCO-Unix systems needed the normal mode iso the LBA mode.  Since I thought Ubuntu was "UNIX-alike", I changed it to normal mode in the BIOS.

I'll change it again to LBA and see what it does...

You also told me to make sure the boot partition is the first one on the disk.  Should the Ubuntu installation CD not take care of this?  I hoped it did, but I'm apparently wrong.

*Can you tell me what to do to get the boot partition the first one on the disk?*

Best rgds,

--Geert

---

### Post by GTvulse on 2005-07-11
[QUOTE=GeertVc]Well Alejo...  

[snip]

You also told me to make sure the boot partition is the first one on the disk.  Should the Ubuntu installation CD not take care of this?  I hoped it did, but I'm apparently wrong.

*Can you tell me what to do to get the boot partition the first one on the disk?*

Best rgds,

--Geert[/QUOTE]

Hi Geert,

The problem with LBA has to do with the PC BIOS and the bootloader, not really with Linux itself. I myself have been very happy since GRUB showed up because lilo always gave me grief...

On the boot partition being the first on the disk, this is really a matter of practicallity as your first message implied you were using the whole disk to install Ubuntu. To make a long story short (because I got to run just now :-)) If you leave the installer choose the partitioning for you, it will create only two primary partitions, the first will have the OS and the user directories, the second will be a swap partition. If that is the case, you should be fine; although I would recommend that you split that first partition into two, the first for the OS (3 GB are to be enough) and a second partition with the rest to store your user directories. If you have a problem and need to reinstall, you won't lose you data (unless you inadevertenly reformat that second partition). If you want to repartition your disk in finer slices, make sure that the boot partition is the first and that it is a primary partition, not a logical one, else the boot loader won't be able to initialize the system (the really important bit is that the boot partition be one of the four possible primary partitions, if you are using msdos disklabels which is most probably the case).

Cheers

---

### Post by GeertVc on 2005-07-11
Hi Alejo,

Thanks for your extensive explanation.  I see some light in the tunnel now...

I changed the mode of the harddisk to LBA in the BIOS setup, to start with.  

Then, I re-installed the whole stuff (in fact, still busy now) with the following partition settings:

[list]
[*]#1 mount to: /boot ==> 2GB primary (didn´t read your email yet at the time I started the re-installation...  :???: )
[*]#6 mount to: / ==> 38,8GB logical
[*]#5 swap ==> 509MB logical
[/list]

I also let the system reformatting the whole HDD.

It migh be important to know that Linux is the **only** OS on that HD and that HD is the **only** one in my old (9 years...) Pentium-I PC.

Does this seem a correct choice?

Best rgds,

--Geert

---

### Post by JaM on 2005-07-11
2 GB is a bit much for a boot partition, 128 MB will do fine

---

### Post by GTvulse on 2005-07-11
As JaM points out, 128 Mb is more than enough, my remark about 3 or 4 Gb was for the root (/) partiton. As you are in the process of getting your feet wet, and perhaps won't mind doing it again one more time.... Here are my suggestions:

[list]
[*] /dev/hda1 /boot 128Mb (primary)
[*] /dev/hda2  swap 1 Gb (primary)
[*] /dev/hda5 /     5 Gb  (logical) ( I use 5 Gb in mine and I'm at 60 % use with some extra big apps including R, Octave and Grass)
[*] /dev/hda6 /home the rest (logical)
[/list]

If one can manage it, it is always a good idea having the swap in the first part of the disk, particularly when one has RAM limitations. That's another reason for setting a swap partition so big, it will allow you to use some demanding applications such as the Gimp (even if it will be slow as a snail :-)). As well, an excellent way to save up RAM is to compile your own kernel stripped down to the minimum (see [this thread](http://ubuntuforums.org/showthread.php?t=43065)  for instructions).

---

