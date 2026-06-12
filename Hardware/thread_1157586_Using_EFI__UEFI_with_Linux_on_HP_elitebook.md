---
title: "Using EFI / UEFI with Linux on HP elitebook"
date: 2009-05-12
forum: Hardware
---

### Post by HunterThomson on 2009-05-12
Aloha, I have created this thread to help others and myself use EFI with Linux on HP elitebook or other EFI Intel based HP systems.

I have been reading up on EFI/UEFI and have found the help to be vary scattered. Most of it dealing with Mac's. I hope this thread will become a practical, usefull, consolidated resource & "How To"s for people wanting to use EFI/UEFI BIOS with Linux on a HP computer.

Any knolage you may have about EFI/UEFI or any help you may give HP/elitebook EFI/UEFI users would be greatly appreciated.

Also, I have a "How To" thread for this laptop you can check it out here

**_HP elitebook 8530w w/ FireGL 5700 "Ubuntu Compatibility"_**
[http://ubuntuforums.org/showthread.php?p=7324922#post7324922](http://ubuntuforums.org/showthread.php?p=7324922#post7324922)

_[SIZE="2"][COLOR="Blue"]Usefull Links>>>[/COLOR][/SIZE]_

**_EFI File System Commands_**
[http://www.docs.hp.com/en/B9106-90003/ch04s01.html](http://www.docs.hp.com/en/B9106-90003/ch04s01.html)

**_Command Reference for EFI Shell Commands_**
[http://www.docs.hp.com/en/5991-1247B_ed2/ch04s13.html](http://www.docs.hp.com/en/5991-1247B_ed2/ch04s13.html)

**_"rEFIt" GUI EFI Bootloader_**
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

**_"elilo" EFI Linux Bootloader_**
[http://elilo.sourceforge.net/cgi-bin/blosxom](http://elilo.sourceforge.net/cgi-bin/blosxom)

---

### Post by HunterThomson on 2009-05-12
I will setup my elitebook 8530w and then post what I found and did. Realy I'll be happy just to be able to set my own BIOS Logo. I'm thinking I'll make it a big pic like this.

[CENTER]
(( Archlinux Logo or Hak5 Logo Here))
Trust Your Technolust

[/CENTER]

_
If you have not seen Hak5 you got to check them out they Rock :)
[http://www.hak5.org/](http://www.hak5.org/)

I think I should be able to install Linux with GRUB on the MBR. Then set up elilo on the EFI partition. That way when I go into CMOS, if I turn off EFI it will boot with GRUB from the MBR 'or' if I turn it On it will boot with elilo form the EFI partition.

---

### Post by DanaG on 2009-05-13
I've already set up my EliteBook 8530w with the ability to UEFI-boot -- but I ended up disabling it, because there's no way to do the equivalent of Grub's "savedefault" with any of the UEFI boot utilities.  
I've also found that both Windows and Linux tend to get some breakage: in Linux, it breaks the VESA framebuffer, so you either have screwed-up text consoles or have to use uvesafb; in Windows, the wifi driver won't start.  
Interestingly enough, fglrx works fine with UEFI, once I fixed this kernel-panic issue that happens even when MBR-booting:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600)


Check here for the grub2.efi I used -- it has to be a 64-bit only EFI file, not a "Fat" binary as Apple likes.
[http://ubuntuforums.org/showthread.php?t=995704&page=77&highlight=uefi](http://ubuntuforums.org/showthread.php?t=995704&page=77&highlight=uefi)
I'll have to dig up my grub.cfg some time this evening.  

Another note: before you can use efibootmgr to add Ubuntu to the EFI boot menu (might wanna' enable the Express Boot menu, by the way)... you have to manually load grub.efi once via F9.

Edit: Note that I actually had to customize my laptop to order, because I specifically wanted ATI and 1920x1200 -- they didn't offer this in any preconfigured models.

Edit: another note: if you want an EFI shell, you'll have to download the TianoCore EFI toolkit and use the precompiled binaries from it.

Edit: dug up my grub.cfg.
```
### BEGIN /etc/grub.d/00_header ###
set default=10
set timeout=5
terminal console
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,6)
search --fs-uuid --set 94e4cd39-b8fd-4b33-bcd1-1539317dd4dd
menuentry "Ubuntu" {
	linux	/vmlinuz root=UUID=94e4cd39-b8fd-4b33-bcd1-1539317dd4dd ro console=ttyS0,115200 console=tty0 video=uvesafb:mode_option=1024x768-32,scroll=ywrap,blank=1 splash
	initrd	/initrd.img
}
menuentry "Ubuntu (recovery mode)" {
	linux	/boot/vmlinuz root=UUID=94e4cd39-b8fd-4b33-bcd1-1539317dd4dd ro single console=ttyS0,115200 console=tty0
	initrd	/initrd.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

```

---

### Post by HunterThomson on 2009-05-14
Nice :) thaks for the input.

I am not at that stage yet. I just got the thing to boot after 14hr's strate. I guess my box dosn't boot off of an extended partition. At leest not on my SSD.

---

### Post by DanaG on 2009-05-15
Hmm, I've never had issues with logical/extended partitions, myself... I just had to have grub in the MBR, of course.

---

### Post by HunterThomson on 2009-05-15
HOE, you have the ati card like me... off topic but could you tell me how to get it working i'v read and done everything all day. How do you install the catalyst?

---

### Post by DanaG on 2009-05-15
It's actually not too hard, now that somebody found the aticonfig workaround.
What I've done:
1.  Download ATI 9.4 driver installer.
2.  run: sh ati-driver-installer-whatever.sh --buildpkg Ubuntu/jaunty    (it will request the installation of a few development header packages; once you do so, rerun the buildpkg.)
3.  Install the generated debs.  Don't reboot!
4.  Make sure your xorg.conf uses fglrx -- perhaps sudo aticonfig --initial
5.  run this command: sudo aticonfig --acpi-services=off (this will avoid the panic.)
Now you should be able to reboot; also note that adding "text" to kernel command line will allow you to boot to everything-but-GDM.

---

### Post by HunterThomson on 2009-05-16
What driver did you use? Could you provide a link. 
I never did do that acpi=off line. Thoug when I tried to run other commands simler

sudo aticonfig --initial -f 
sudo aticonfig --input=/etc/X11/xorg.conf


I know the first one told me know device not found. But I think it let the other command go though. Well shoot you have the same laptop with the Mobility FireGL 5700 right? So, I guess I'll try it. I was just going to give up and wate for it to get fixed.

---

### Post by DanaG on 2009-05-16
Here's what I have in my xorg.conf, with the exception of the large comment header at the top:
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "DPMS" "true"
	#	Option	    "VendorName" "ATI Proprietary Driver"
	#	Option	    "ModelName" "Generic Autodetecting Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	"UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "ServerFlags"
	Option	    "DontZap" "false"
EndSection

```

Note that setting DontZap to false re-enables the ctrl-alt-backspace "zap" shortcut.

I think by "no Device found", the installer probably meant that there was no "Device" section in your existing xorg.conf.
Unfortunately, AMD doesn't allow direct driver linking, at least last time I tried.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
I went to Linux x86_64 (because I use 64-bit) -> Radeon -> Radeon HD3xxx Series.  If you use 32-bit ubuntu, just go to Linux x86 -> Radeon -> Radeon HD3xxx Series.

Exact filename was "ati-driver-installer-9-4-x86.x86_64.run".

Afer installing this (with the buildpkg way) and putting xorg.conf in place, you'll then want to run the aticonfig --acpi-services=off command.

---

### Post by HunterThomson on 2009-05-16
**[color="red"][size="3"]holy cow !!!! I love you !!![/size][/color]**

all about that acpi=off. I even got it working in Archlinux now.

---

### Post by krazyd on 2010-04-18
hi HunterThomson, how is the uefi support in ubuntu these days? is it supported in the installer?

i'm getting an hp notebook with uefi soon and want to know how i can get lucid on it without rEFIt.

---

### Post by DanaG on 2010-04-18
The Ubuntu installer still doesn't support UEFI, but you should be able to install Ubuntu with the legacy boot mode, and then add grub-efi later.  This also has the advantage that if you do as I do, and keep both methods usable (grub-pc on ext4 partition and grub-efi on the HP_TOOLS paritition), you can use one method to boot when the other is broken (such as when Windows tramples on Grub.)

I've also concluded that the UEFI implementation in the EliteBook xx30p/w notebooks is broken... it has non-working wifi in Windows, and non-working EFI frame-buffer both in Windows and Linux.  Hopefully the new EliteBook xx40p/w models have a correct UEFI implementation.

To install Windows in UEFI boot mode, by the way, you must use GPT partitioning -- you may want to test that with a new install on a spare drive, before investing any time in setting up UEFI on Linux.  It is possible to add UEFI-boot to a MBR-installed Windows, by the way -- you have to copy the EFI/Microsoft stuff from a UEFI install.

---

### Post by krazyd on 2010-04-18
Thanks for the info!

So grub must be installed on 'HP_TOOLS', rather than a partition actually named 'EFI'?

Can the notebook automatically boot the grub.efi image, or does it have to be manually selected every boot?

Also, have you tried using the alternative installer for ubuntu to create a GPT? I'm hoping to have this notebook ubuntu-only.

Sorry about the interrogation, but any help you can provide would be great :)

---

### Post by HunterThomson on 2010-05-19
Hum sorry, I never did try the UEFI stuff. I read about it and it sounded super cool but then DanaG told me that in the end it just brakes a bunch of stuff. In any case DanaG is the one to talk to.

---

