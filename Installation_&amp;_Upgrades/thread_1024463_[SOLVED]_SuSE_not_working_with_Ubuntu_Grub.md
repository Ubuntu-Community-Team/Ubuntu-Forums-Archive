---
title: "[SOLVED] SuSE not working with Ubuntu Grub"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by brundlelinux on 2008-12-29
I need a little bit of help editing my grub's menu.lst so that it will allow me to boot into OpenSuSE and the OpenSuSE Failsafe from a cold boot.  Here's what I did and how I got to where I am currently:

I started off with Ubuntu loaded.  I then added SuSE alongside of it as a dual boot.  This overwrote the Ubuntu Grub with SuSE's grub.  I prefer to not have graphical eye-candy at boot (SuSE grub has this), so I wanted to revert back to Ubuntu's grub.  I re-assigned Ubuntu's grub to the MBR, and this allowed me to boot in Ubuntu.  Since Stage2 is now the menu.lst from Ubuntu and not SuSE, I need to add the info for SuSE in order to have these options from a cold boot.

Having poked around on both Ubuntu and OpenSuSE forums a bit, I started by trying to add the following to the end of my menu.lst and then rebooting.

```
title Suse Linux
configfile (hd0,9)/boot/grub/menu.lst 

```

(EDIT:  I did change to (hd0,6) when trying the above)

The reboot went straight into Ubuntu without ever pausing or returning a grub menu.  So, instead of trying the configfile method, I decided to try using a 'proper' stanza with UUID and kernel.

The issue I encountered here is that ```
blkid
``` does not list a UUID for my SuSE partition, as seen here.  ```
/dev/sda3: UUID="f466d040-f829-4e6c-a734-8a1ce15e4d6f" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="52fa83f3-1b01-4adc-8d88-08600044c9e0" TYPE="ext3"
/dev/sda6: UUID="804e7ae4-9735-45e9-909c-f73d66083f5e" TYPE="swap"
/dev/loop0: TYPE="squashfs"
```

FYI, sda3 is a partition I set up to hold media, and sda5 is my Ubuntu partition.  My SuSE partition is sda7.

My next step was to mount my SuSE partition under Ubuntu so I could go in and look at the menu.lst on SuSE's grub to retrieve the UUID.  Here's what is listed in SuSE:

```
# Modified by YaST2. Last modification on Mon Dec 29 04:04:41 UTC 2008
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-ST3120023A_3KA1K5FZ-part7 resume=/dev/disk/by-id/ata-ST3120023A_3KA1K5FZ-part6 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-ST3120023A_3KA1K5FZ-part7 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.10, kernel 2.6.27-9-generic (/dev/sda5)###
title Ubuntu 8.10, kernel 2.6.27-9-generic (/dev/sda5)
    root (hd0,4)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1
```

Obviously, not UUIDs.  Still, I did try and add those SuSE stanzas to the Ubuntu Grub menu.lst and reboot.  Again, it went straight to Ubuntu and never paused or returned a grub menu.

I've been trying to find info on what to try next via Google and forums, but being a novice, I'm stumped.  All the stuff I find about chainloading and grub menus leading to secondary grub menus is above my level of comprehension.  

ATM, I cannot boot into SuSE at all.  Anybody care to help out?

---

### Post by kunixos on 2008-12-29
Could you post your complete menu.lst from your Ubuntu GRUB folder?

---

### Post by tommcd on 2008-12-29
> **brundlelinux said:**
> 
Again, it went straight to Ubuntu and never paused or returned a grub menu.


Do you not even see the grub menu when you boot? If that is so, then hit the **Esc** key on your keyboard as your computer boots and you should see the grub menu. To see it every time you boot, edit your menu.lst and put a comment (#) in front of the **hiddenmenu** line.

The configfile method should work *if* you have Suse's grub installed to Suse's root partition and Ubuntu's grub installed to the MBR. That is how I boot Debian from Ubuntu's grub on my laptop.

---

### Post by brundlelinux on 2008-12-29
And THIS is why you don't screw around with Grub when you're tired.  Worked perfectly after I commented out the hiddenmenu.

Thanks guys!!

---

