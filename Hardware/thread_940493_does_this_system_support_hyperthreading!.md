---
title: "does this system support hyperthreading?!"
date: 2008-10-07
forum: Hardware
---

### Post by jaikat on 2008-10-07
this all started with my cpu fan, i feel its working at high speeds even with no heavy load on the machine/system. for example: if i start audacity, open an mp3 file, then export the file in the ogg format, the fan would pick up speed the second conversion starts, and gets quit as soon as the process is finished. maybe this is normal, but the fan also picks up speed when launching firefox and sometimes through browsing..is this considered heavy load on such a machine?!

i also checked the bios for cpu temperature, it at 65C, and it goes to 68 (while i'm still inside the Bios screen) and the fan picks up speed :confused:

its like the cpu is in need of cooling even without a system running(when inside the Bios).

--------------

moving to my second issue..

i have a 3.0 Ghz cpu that is hyperthreading capable. the Bios also shows hyperthreading is enabled. and my system monitor is showing 2 cpu(s)

this is my cat /proc/cpuinfo

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 9
cpu MHz		: 3000.246
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 6007.73
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 9
cpu MHz		: 3000.246
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 6000.68
clflush size	: 64
--------------------------
i didn't feel the machine was different when i edited the grub menu and added ht=on to the line

# kopt=root=UUID=9b6a04b6-10f9-4659-a06a-c77bf589f8a5 ro ht=on (this is exactly what the line looks like..with the hash(#) included)

so, does this mean my ubuntu(Hardy) supports hyperthreading?

any note is appreciated.

MJ

---

### Post by TheLions on 2008-10-07
to answer your question:
Yes, Ubuntu supports hyperthreading, but not by default, to enable it look here: [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

about your fan, get some decant fan, cause Intel 4 got some heating problems and box-one fan is to weak

---

### Post by jaikat on 2008-10-07
ok, this is my grub menu with the "ht=on"..(the edit is in red color)

=================================
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR="Red"]# kopt=root=UUID=9b6a04b6-10f9-4659-a06a-c77bf589f8a5 ro ht=on[/COLOR]

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9b6a04b6-10f9-4659-a06a-c77bf589f8a5 ro ht=on quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9b6a04b6-10f9-4659-a06a-c77bf589f8a5 ro ht=on single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
=============================================

is the "ht=on" placed correctly?

---

### Post by jaikat on 2008-10-10
Anyone?!

---

### Post by TheLions on 2008-10-10
yes it is, do you see 2 CPUs in gnome-system manager?

---

### Post by jaikat on 2008-10-12
Yes i do. and thanks for taking the time to reply.

---

