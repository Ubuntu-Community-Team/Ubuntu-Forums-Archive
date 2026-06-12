---
title: "Error 16 when booting"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by pulseplanet on 2009-05-06
Hello All,

  On a 80GB SATA laptop HDD, I installed Windows first and then installed Ubuntu 9.04. Everything was ok and I could dual boot. Then my company installed Safeguard Easy (whole disk encryption software) and now at the boot screen when I pick ubuntu I get the following error:

**"error 16: inconsistent file system structure"**

I used a Live CD and did a file system check:

```
sudo e2fsck -C0 -p -f -v /dev/hda2
```

my fdisk -l output is:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29bcd914

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        6375    51199155    7  HPFS/NTFS
/dev/sda2            6376        9729    26941005    5  Extended
/dev/sda5            6376        9486    24989076   83  Linux
/dev/sda6            9487        9729     1951866   82  Linux swap
```

and my menu.lst looks like this:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


default		4
timeout		10
#hiddenmenu
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		230eb8b2-2b4b-403e-b4b1-b71825846fa7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=230eb8b2-2b4b-403e-b4b1-b71825846fa7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		230eb8b2-2b4b-403e-b4b1-b71825846fa7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=230eb8b2-2b4b-403e-b4b1-b71825846fa7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		230eb8b2-2b4b-403e-b4b1-b71825846fa7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```


I do not want to reinstall GRUB in a way that modifies the MBR because of the disk encryption - since that renders the Windows boot inoperable (learnt it the hard way from a previous install). I know that the ext3 partitions are not encrypted because I can mount them when using the live CD.

Any idea on how I solve the "Error 16" problem?

Thanks in advance.

---

### Post by mtuu on 2009-07-26
Same problem here. No ideas yet?? 

I already tried the following: 

[LIST=1]
[*] Installed grub on a memory stick, and booted the installed system (Jaunty). 

Works.

:neutral:

[*] Replaced defaultly used UUID's with 'real' names.

Not working.
:(

[*] Booted from HD, and entered the *Grub console*. I can set root (hd0,6 in my case) 
and kernel (boot/vmlinuz-2.6.28-13-generic), **but** if I type

     initrd /boot/initrd.img-2.6.28-13-generic

(Jaunty) I get

Error 16: Inconsistent filesystem structure

Not working.
:confused:

[*] Recreated initrd (mkinitramfs with and without -r option)

Not working.
:mad:

[/LIST] 

Before Safeguard everything was ok. I'm thankful for any ideas!

---

### Post by pulseplanet on 2009-07-27
mtuu,

   Sorry to hear that you also are having troubles. I was never able to find any solutions to that and the laptop still does not boot into Ubuntu.

  Same thing here: before Safeguard, everything was OK.

K

---

### Post by mtuu on 2009-07-28
Sleeplessness and luck saved the day: What's disturbing is that setting the initrd causes the error in grub shell ("initrd /boot/initrd.img-2.6.28-13-generic" directly caused the Error 16). So the idea came up to boot simply without initrd. And that's the lucky part: It works!! I don't really understand the cause for the initrd problem, but the kernel is loaded and the system comes up. Obviously my notebook is "standard" enough and no "essential" driver is needed from initrd. The only thing missing is the framebuffer driver, but that's no problem since it's only needed for text consoles. 

The menu.lst entry for Ubuntu now is the following:
```

title    Ubuntu 9.04 (no initrd)
kernel   /boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro

```The original "splash" option is useless without framebuffer device, and if looking at boot messages, then all (not "quiet") ;)

pulseplanet, I hope you have luck with that as well!

---

### Post by unutbu on 2009-07-28
mtuu, I'm glad you figured out how to restore your boot setup, and thank you for sharing this interesting information. 

Edit: Oops, I didn't see you have already tried mkinitramfs...

[s]
Would you be willing to do an experiment?

If you run [/s]
```

sudo cp /boot/initrd.image-2.6.28-13-generic /boot/initrd.image-2.6.28-13-generic.bak
sudo update-initramfs -u
```
[s]
the machine should generate a new initrd for you:[/s]
```

update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic

```[s]
Then see if you can boot with the regenerated initrd:[/s]
```

gksu gedit /boot/grub/menu.lst
```
[s]
Add another boot stanza:[/s]
```

title    Ubuntu 9.04 (with new initrd)
kernel   /boot/vmlinuz-2.6.28-13-generic root=/dev/sda7 ro
initrd   /initrd.img-2.6.28-13-generic

```

---

### Post by pulseplanet on 2009-07-28
mtuu:
  Many thanks. I can confirm that removing the initrd line works. 

unutbu:
  Making a new initrd and booting with it as you suggest does not work for me. Same error: "Error 16: Inconsistent filesystem Structure"

---

### Post by unutbu on 2009-07-28
Ok, pulseplanet. Thanks for trying the experiment. :)

---

