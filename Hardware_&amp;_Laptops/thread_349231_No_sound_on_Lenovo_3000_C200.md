---
title: "No sound on Lenovo 3000 C200"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by jgb2185 on 2007-01-29
I know there have been a pile of posts on this topic... but I am a relative newcomer to Linux hardware troubleshooting, and could use some guidance. I've searched these forums and Googled for the solution to this issue, and have not had much luck.

I have installed Ubuntu 6.10 Edgy, and noted no errors during the install. **lshw** says:
```
*-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:e000-e0ff ioport:e400-e43f iomemory:ec181000-ec1811ff iomemory:ec182000-ec1820ff irq:209
```
I added
```
# Enable sound output
options snd-hda-intel model=laptop-eap
```
to **/etc/modprobe.d/options** with no effect after a reboot.

Starting and stopping ALSA also fails:
```
# sudo /etc/init.d/alsa-utils stop
# sudo /etc/init.d/alsabase stop
# modprobe snd-hda-intel
```

I have attempted to follow the procedures listed in the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") document:
```
root@lenovo3000:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@lenovo3000:~# lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 3802
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)
```
So it appears that the audio controller is definitely an Intel HDA device. I tried **alsamixer**, found the PCM turned all the way down, turned it up to 100% -- no joy. 

I started an attempt at compiling the ALSA drivers afresh...
```
root@lenovo3000:~# apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
E: Couldn't find package module-assistant
```
Hmmm. Wherefore art thou, **module-assistant**?

That's where I stand now. [Deepsa's post]("http://ubuntuforums.org/showpost.php?p=1975260&postcount=2") describes a procedure that looks similar to the ALSA recompile in the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") document, but it also requires module-assistant. I note that Deepsa is using Fiesty. I am wondering if I should wipe the Linux partitions (it's a brand new install, no data worth saving) and install Fiesty in place of Edgy. Would that give me a better chance of success?

Is there a known fix for this problem under Edgy? Failing that, can someone suggest the most promising next step?

Many thanks for any suggestions...

JGB

---

### Post by jgb2185 on 2007-01-30
Addendum: I am simultaneously researching the problem of getting the Broadcom wifi card in the Lenovo to function, and at least [one post I have found]("http://ubuntuforums.org/showthread.php?t=201902") indicates that this is not possible under Fiesty. Thus, a solution for the sound problem under Edgy would be preferable... unless there is more recent news about Fiesty that I have missed.

JGB

---

### Post by jgb2185 on 2007-02-01
[apoloco has provided the solution]("https://answers.launchpad.net/ubuntu/+ticket/3416"):

> I've the same laptop and problem. Just set at boot options: acpi=ht and works fine ;).

And indeed, it does work fine. There does seem to be a problem with the laptop powering off automatically at shutdown, but I'll take that trade.

Many thanks, apoloco!

---

### Post by Fred_C on 2007-02-14
I'm pretty new to Ubuntu... how do I set the boot options to acpi=ht ?

---

### Post by drs305 on 2007-02-26
> **Fred_C said:**
> I'm pretty new to Ubuntu... how do I set the boot options to acpi=ht ?

Same question for me. Still looking for a sound solution for the Lenovo. (Modem enabling did not solve it - willing to try any sane solution suggestion.

---

### Post by norby_cz on 2007-03-24
> **jgb2185 said:**
> [apoloco has provided the solution]("https://answers.launchpad.net/ubuntu/+ticket/3416"):



And indeed, it does work fine. There does seem to be a problem with the laptop powering off automatically at shutdown, but I'll take that trade.
w
Many thanks, apoloco!

acpi=ht is causing this problem, you don't need it, because sound is working fine without it, but only from headphones, not from internal speakers which are crap anyway

---

### Post by shabri on 2007-04-22
Hi, sorry to re-ignite an old thread but I have this problem and I don't know how to "set the boot options to acpi=ht " - i can't find an easy to follow explanation anywhere.

This is my first linux experience, just loaded fiesty and am starting to get things to work, so assume total ignorance :)

---

### Post by Coombabah on 2007-04-22
I have a Lenovo 3000 C200 this link worked for me :)

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

Setting the boot options to acpi=ht didn't work for me but the above did and I can shut the computer down normally  :)

Edit. It worked after I rebooted which resulted it waking up the household.
I'd turned everything on full including the mic settings. 
There was a feedback howl as the mic was also on full. The dog started barking, everyone came out to see what was wrong.
Next question.
How do you shut it up when that happens besides turning the power off?

---

### Post by jgb2185 on 2007-04-22
Shabri: 

You will need to edit the [FONT="Courier New"]**/boot/grub/menu.lst**[/FONT] file to add this option to the end of the [FONT="Courier New"]**kernel**[/FONT] line that boots Ubuntu. A [good grub tutorial]("http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/") will help you work through this. Be certain to back up the existing [FONT="Courier New"]**menu.lst**[/FONT] file.

JGB

---

### Post by shabri on 2007-04-22
That's great - many thanks!

---

### Post by shabri on 2007-04-22
OK: beginning to feel dumb now!

I tried the recommended fixes and couldn't get them to work.

I read the tutorial and learnt a bit more about grub, but still can't see what I'm supposed to do.  Also, the menu I get is somewhat different form the one the article describes,

Here's what I get, where exactly do i write in acpi=ht ?

Again, many, many thanks!

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=2b2a854e-2dd7-4e69-81e1-e21f67787b10 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2b2a854e-2dd7-4e69-81e1-e21f67787b10 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2b2a854e-2dd7-4e69-81e1-e21f67787b10 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows NT/2000/XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.04 (7.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 
savedefault
boot

---

### Post by Coombabah on 2007-04-23
The LaptopTestingTeam has addressed the important issues for the Lenovo 3000 C200 for us. :)

See this page for details.

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

You don't need to interfere with acpi by passing the kernel parameter acpi=ht to get sound working now.

It explains the issues step by step but you can just cut and paste the code into a terminal.

It also lists other gotchas like needing the internal modem being enabled in bios.

---

### Post by bmt on 2007-04-24
You might also want to watch the events on the [ALSA buglist]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725"), where modifications are still being made to get the last few details corrected.

---

