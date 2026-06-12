---
title: "Effective RAM size not recognized"
date: 2011-12-14
forum: Hardware
---

### Post by manolomanolo on 2011-12-14
Hi to all.

I just added a further 2GB RAM bar to my Acer Aspire 5730z.
The previously installed bar was 2GB too. The new bar has been taken from another Acer Aspire 5730z. So, compatibility is assured. *Also, it seems that laptop supports until 8GB (max 4gb per slot)*. **[EDIT: it seems the maximum extension is up to 4GB (2 per slot) and not to 8GB. Sorry]**

Unfortunately, the only software recognizing my 4GiB RAM is ```
lshw-gtk
``` (Hardware Lister GUI). Command line programs, such as ```
free -m
``` and ```
cat /proc/meminfo
``` and also ```
lshw
``` (command line version of lshw-gui) tell me the RAM size is always 2956MiB.
Also Gnome System Manager and KDE System Manager tells I just have 2.9GiB.

What's wrong with my system?
Thanks.
Regards.

---

### Post by manolomanolo on 2011-12-14
More infos.
Following free -m, the size of each bar is 1944 megabytes when installed stand alone.

I've also tried all the possible combinations of installing the bars into the only 2 available slots: each bar has been installed stand alone subsequently on each slot. I've also tried to change slot for each bar, when both installed.
The result is always the same. When installed alone, each bar size is 1944. When both installed at the same time, the size is less than 3000.

What's wrong?
Thanks

---

### Post by mastablasta on 2011-12-14
are you using the 64 bit version of the OS?
 
If not, did you install PAE kernel?

---

### Post by manolomanolo on 2011-12-14
I have 32bit OS installed, not PAE one.
So, should I install PAE?
Also, which package in this case?

Thanks

---

### Post by trundlenut on 2011-12-14
> **manolomanolo said:**
> I have 32bit OS installed, not PAE one.
So, should I install PAE?
Also, which package in this case?

Thanks

32 bit kernel without PAE can only access 3GB of ram.

So I would install either a PAE kernel or reinstall with the 64bit version of ubuntu.

---

### Post by manolomanolo on 2011-12-14
I installed the PAE kernel but it still sees almost the same (just 1 MegaB less than before). I installed the linux-generic-pae and startup-manager confirms I'm using that pae kernel now.

---

### Post by manolomanolo on 2011-12-15
I've also just run the Kubuntu 11.10 64bit LiveCD, but nothing changes.
Any suggestion, please?

---

### Post by trundlenut on 2011-12-15
> **manolomanolo said:**
> I've also just run the Kubuntu 11.10 64bit LiveCD, but nothing changes.
Any suggestion, please?

Is the 4gb of memory recognised in the BIOS OK?

---

### Post by wolfen69 on 2011-12-15
> **manolomanolo said:**
> So, compatibility is assured.

*Nothing* in computers is assured. ;) I would also take a live cd and run MemTest just for good measure.

---

### Post by manolomanolo on 2011-12-16
> **trundlenut said:**
> Is the 4gb of memory recognised in the BIOS OK?

**From the BIOS:**
System Memory: 632 kB
Extended Memory: **4029 MB**
Video Memory: 64 MB

---

### Post by wolfen69 on 2011-12-16
> **manolomanolo said:**
> **From the BIOS:**
System Memory: 632 kB
Extended Memory: **4029 MB**
Video Memory: 64 MB

Just because the BIOS gives the right info, does not mean there are no errors with the memory. (an example would be a bad hard drive, the BIOS sees it, but it does not work right) I still think you should rum MemTest.

---

### Post by N00b-un-2 on 2011-12-16
sounds like the RAM is either incompatible or you got a bad stick.

---

### Post by manolomanolo on 2011-12-17
> **N00b-un-2 said:**
> sounds like the RAM is either incompatible or you got a bad stick.

Bad stick. Is it still possible taking into account that each stick is well recognized when installed alone, **[as I said here]("http://ubuntuforums.org/showpost.php?p=11536599&postcount=2")**?

---

### Post by MoreOrLess on 2011-12-18
It's probably not a bad stick. Look in the BIOS for settings related to memory (like remapping).

---

### Post by manolomanolo on 2011-12-19
The current ACER BIOS does not allow so much settings changing. Actually, I think it just allows changing the boot device priority and not much more.
For example, no way to declare how much memory to reserve to video card.

Moreover, I've been experiencing the same problem on another laptop, same model (ACER ASPIRE 5730z). Both Windows 7 (32bit) and Kubuntu 11.10 (64bit) tell me that just 3GB of memory are availeble.
Actually, Windows 7 sais that 4GB are installed, but just 3 are usable.

So, in the end, I will surely exclude it is a Linux issue, since the problem persists on 2 laptops (same model!) with different OS and different RAM stick.

What could it be?
Thanks.

---

### Post by trundlenut on 2011-12-21
My laptop has 4gb of ram, windows 7 (32 bit) reports 4gb present but only 3gb available.  Ubuntu 11.10 (64 bit) can access the 4gb without issue though, all minus what the graphics are using though.

Does the graphics card in the latop use the ram too, if so how much?

---

### Post by manolomanolo on 2011-12-22
> **trundlenut said:**
> My laptop has 4gb of ram, windows 7 (32 bit) reports 4gb present but only 3gb available.  Ubuntu 11.10 (64 bit) can access the 4gb without issue though, all minus what the graphics are using though.

Does the graphics card in the latop use the ram too, if so how much?

I don't understand if you are asking the same question I'm going to ask now.
ACER tech support says that the video card is authomatically absorbing the resting 1GB of RAM, even if I cannot manually set the quantity of RAM I would wish to assign to the video card.

Now, the question is: how to see how much RAM is currently assigned to the video card when the OS is running?

---

### Post by trundlenut on 2011-12-22
> **manolomanolo said:**
> I don't understand if you are asking the same question I'm going to ask now.
ACER tech support says that the video card is authomatically absorbing the resting 1GB of RAM, even if I cannot manually set the quantity of RAM I would wish to assign to the video card.

Now, the question is: how to see how much RAM is currently assigned to the video card when the OS is running?

Yes, that is basically the same question.

I would suspect you can't see how much RAM tis used by the graphics easily as this is controlled by the BIOS.  You may be able to find out though through the graphics card.

---

### Post by manolomanolo on 2011-12-25
> **wolfen69 said:**
> Just because the BIOS gives the right info, does not mean there are no errors with the memory. (an example would be a bad hard drive, the BIOS sees it, but it does not work right) I still think you should rum MemTest.

I haven't still run MemTest but I would exclude the possibility that the sticks are damaged.
In fact, the same problem persist on another laptop (same model) with Windows 7 installed: 4GB are installed, but just about 3GB are available.
However, unlike in Gnu/Linux, I can do explain why it happens in Windows 7: the graphic card result to use minimum 64MB and maximum about 1300MB of the system RAM. So, in a way, I can say that the missing GB is reserved to the video card, even if not currently completely used.

On the other hand, I cannot tel for sure my k/ubuntu installation is doing the same. In fact, **[as shown here]("http://ubuntuforums.org/showpost.php?p=11558082&postcount=3")**, just 256MB seem to be used by the video card. Actually I cannot even distinguish whether those are 256MB of memory installed on the video card or it is 256MB of shared RAM. However, more that 700MB would be missing.

So, the question is: how is Linux treating the "missing" RAM?

---

### Post by manolomanolo on 2011-12-25
> **trundlenut said:**
> Yes, that is basically the same question.

I would suspect you can't see how much RAM tis used by the graphics easily as this is controlled by the BIOS.  You may be able to find out though through the graphics card.

trundlenut, i think the previous post answers to you too.
In other words, do you know alternative ways to discover how much RAM is reserved for the video card?

---

### Post by Stephan1864 on 2011-12-25
Try adding this to your boot iommu=memaper=3

---

### Post by manolomanolo on 2012-01-03
> **Stephan1864 said:**
> Try adding this to your boot iommu=memaper=3

This is my /boot/grub/grub.cfg

Where do you think I should add those lines?
Thanks.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
  set locale_dir=($root)/boot/grub/locale
  set lang=it_IT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, con Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux	/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro splash acpi_osi=Linux  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, con Linux 3.0.0-14-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	echo	'Caricamento Linux 3.0.0-14-generic-pae...'
	linux	/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro recovery nomodeset splash acpi_osi=Linux
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-3.0.0-14-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro splash acpi_osi=Linux  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-14-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	echo	'Caricamento Linux 3.0.0-14-generic...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro recovery nomodeset splash acpi_osi=Linux
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro splash acpi_osi=Linux  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-13-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	echo	'Caricamento Linux 3.0.0-13-generic...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro recovery nomodeset splash acpi_osi=Linux
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro splash acpi_osi=Linux  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-12-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	echo	'Caricamento Linux 3.0.0-12-generic...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=243dc9f9-1d3b-4042-8d5e-bee7480a9e11 ro recovery nomodeset splash acpi_osi=Linux
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 243dc9f9-1d3b-4042-8d5e-bee7480a9e11
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by MoreOrLess on 2012-01-03
/etc/default/grub
Add it to the GRUB_CMDLINE_LINUX_DEFAULT string

---

### Post by manolomanolo on 2012-01-04
> **MoreOrLess said:**
> /etc/default/grub
Add it to the GRUB_CMDLINE_LINUX_DEFAULT string

I added that line, but again all those tools go on telling me I just have about 3GB of RAM.

What can I do?
Thanks.
Regards.

---

### Post by MoreOrLess on 2012-01-04
I forgot to tell you to run update-initramfs after editing (and then reboot) :\
```
sudo update-initramfs -u -k all
```

---

### Post by manolomanolo on 2013-02-26
up.

I still suffer the same problem.
Many linux kernels updates have been passed on my installation from then on.
I still cannot understand why I can only use part of my RAM.

Do you have any clue?
Thanks.
Regards.

---

### Post by prodigy_ on 2013-02-26
Why don't you just install a 64-bit OS? This wouid certainly solve the problem.

---

### Post by N00b-un-2 on 2013-02-26
I know that you said your computer supports up to 8GB of RAM, but are you absolutely sure about that?  I am on an IBM Thinkpad T60 right now which has 4GB of RAM installed in it.  It has an i915 chipset and therefor will only address 3GB of the 4GB I have installed.

---

### Post by prodigy_ on 2013-02-26
> **N00b-un-2 said:**
> IBM Thinkpad T60 right now which has 4GB of RAM installed in it.  It has an i915 chipset and therefor will only address 3GB of the 4GB I have installed.
The OP's laptop is based on Pentium T3x00, so it supports 64-bit.

---

### Post by N00b-un-2 on 2013-02-26
](*,)
You are not listening to what I'm saying.  I HAVE A CORE 2 DUO.  My computer is 64 bit as well.  I am running Windows 8 Pro 64 bit, Ubuntu 12.10 64 bit and Mac OS X 10.6.8 which is ALSO 64 bit.  The limitation is not an architecture limitation (the 32 bit 3GB RAM ceiling).  The issue is the north/south bridge controller chipset.  It is a hardware limitation of the chipset of my motherboard that ANY operating system, regardless of whether i386 or x86_64 will ONLY be able to utilize 3GB of RAM.  PERIOD.

What I am suggesting is that perhaps the OP's computer has a similar hardware limitation.  OP stated that his computer supports up to 8GB of memory, but given that it refuses to allocate the full amount of installed memory even using the PAE kernel, it's quite possible that this is hardware limitation like mine.

---

### Post by manolomanolo on 2013-02-26
Actually, I see there is no more that line in /etc/default/grub
So, could you please tell me how to add that string to the GRUB_CMDLINE_LINUX_DEFAULT string?

This is my current /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by manolomanolo on 2013-02-26
> **N00b-un-2 said:**
> I know that **you said your computer supports up to 8GB of RAM**, but are you absolutely sure about that?  I am on an IBM Thinkpad T60 right now which has 4GB of RAM installed in it.  It has an i915 chipset and therefor will only address 3GB of the 4GB I have installed.

Are you referring to me? My motherboard should support 4GB, according to what ACER said.

Also, maybe I misunderstood what you said in another post, but I would not say it is a north/south bridge problem in case you are referring to the 2 memory slots. In fact, as reported in previous posts, no matter the position: if I install just one of the 2 bars exclusively then my computer can clearly see they respectively are 2GB, no matter the slot used.
So, when installed one by one, they result to be 2GB. When installed together the sum results to be less than 3GB. Why?

---

### Post by manolomanolo on 2013-02-27
> **prodigy_ said:**
> Why don't you just install a 64-bit OS? This wouid certainly solve the problem.

As I have been writing at the beginning of this thread, installing a 64 bit machine as well as installing PAE kernel did not solve the problem.

Any other suggestion, please?
Thanks.

---

### Post by Yellow Pasque on 2013-02-27
```
dmesg | grep -i ram
```
The memory from 3GB to 4GB is almost certainly being reserved for the video card and other hardware addressing. The BIOS could probably be more judicious about it, but don't hold your breath for the BIOS to get fixed. I would definitely give it up as a lost cause...

---

### Post by manolomanolo on 2013-02-27
```
dmesg | grep -i ram
``` gives no result :confused:

---

### Post by Yellow Pasque on 2013-02-27
Hmm. Then just look at 
```
dmesg
```

Find the part the looks like so and share it with us:
```
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e2000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cffaffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffbdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cffbe000-0x00000000cffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffe0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: BIOSTAR Group TA890FXE/TA890FXE, BIOS 080015  06/29/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcffaffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcffaffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcffaffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x12fffffff]
[    0.000000]  [mem 0x100000000-0x12fffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x12fffffff @ [mem 0xcffae000-0xcffaffff]
[    0.000000] RAMDISK: [mem 0x367b2000-0x373d0fff]
```

---

### Post by typhoon_tip on 2013-02-27
Just use dmidecode command ! Can you post the output of:
```
sudo dmidecode -t 16
```

---

### Post by manolomanolo on 2013-03-01
sudo dmidecode -t 16

```
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0015, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2
```

---

### Post by manolomanolo on 2013-03-01
Please find my dmesg in attachment. I have been trying to paste it here but I was not able.
However, I did not find what you told me.
Please have a look at the attachment, maybe you will find what you need but expressed in another form.
Thanks.

---

### Post by Yellow Pasque on 2013-03-01
No, that wasn't it...
Just paste output of:
```
dmesg | grep e820
```

---

### Post by manolomanolo on 2013-03-01
```
dmesg | grep e820
``` gives empty result

---

### Post by prodigy_ on 2013-03-03
> **manolomanolo said:**
> As I ha+
ve been writing at the beginning of this thread, installing a 64 bit machine as well as installing PAE kernel did not solve the problem.

In this case you should file a [bug report](https://bugs.launchpad.net/).

Though I'd also try to install some 64-bit version of Windows just to test. If the problem can be reproduced there, something must be wrong with hardware.

---

### Post by manolomanolo on 2013-03-04
Launchpad seems not to work at the moment. However, should I file a bug as "kernel" bug or what?
Any other suggestion, please?
Thanks.
Regards.

---

### Post by manolomanolo on 2013-03-05
> **Stephan1864 said:**
> Try adding this to your boot iommu=memaper=3

Could you please tell me where should I add that line?
Thanks.

---

### Post by manolomanolo on 2013-03-05
Could you please help me? I don't understand what's the right place for that. Could you send me your file?

---

### Post by manolomanolo on 2013-03-14
up

---

### Post by manolomanolo on 2013-05-31
Still experiencing the same problem. Since then I made 3 important things but the problem persists.

1) installed Linux Mint 14 64bit

2) installed Windows XP Professional 64bit

3) contacted ACER support which said that the possible issue is not related to them since the BIOS can fully recognize the 4GB installed. So, firtly they said it is a OS related issue as soon as they noticed I was using Linux, then when I showed them that the problems persists on Windows they said that there is no issue since maybe the systems absorbs the RAM without noticing the user... without giving me detail on the specific usage made by the specific resource.

So, what should I do?
Should I report ACER for fake advertising?

PD: I' was wrong at the beginning, the supported RAM extension on Acer Aspire 5730z is up to 4GB an not to 8GB. Sorry

---

