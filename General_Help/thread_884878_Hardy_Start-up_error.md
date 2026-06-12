---
title: "Hardy: Start-up error"
date: 2008-08-09
forum: General Help
---

### Post by Comhra on 2008-08-09
I'm seeing the following error at start-up:

[B][17.349375] ACPI:EC: acpi_ec wait timeout, status=0, expect_event=1

[17.349424] ACPI: EC: read timeout, command=128
[/B]

I wonder is there a way of addressing this problem?

My only recourse is to power the machine off and start again.

It's happened 3 times in 24 hours.

How do I solve this problem?

Thanking you in anticipation.

---

### Post by Comhra on 2008-08-09
My feeling is that it's something to do with the Grub Menu, but I'm just not knowledgeable enough to edit the Grub file.  I feel it's something small and that it might just be a case of adding or subtracting or otherwise modifying the /boot/grub/.

---

### Post by Comhra on 2008-08-09
I'm using a laptop and that's probably related to the problem.

---

### Post by Sycron on 2008-08-09
Post your /boot/grub/menu.lst file here. Happened to me once where i was using Ubuntu 32bit on a 64bit computer.

---

### Post by Comhra on 2008-08-09
I found the very bug but I don't know if it will help me much.

It's called Bug # 191137

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137)



The following was posted in Launchpad/Bugs on the 12/4/2008:

Right, I know what is causing this now. We have a complex interaction of three things:

1. Early EC initialisation introduced by commit c04209a7948b95e8c52084e8595e74e9428653d3
2. Timing (especially on multiprocessor / multitasking systems)
3. Possible 'problem' with ACPI DSDT embedded controller logic

When the EC is initialised before the rest of the ACPI namespace, any references in the EC _REG() method to other node names will fail since they're not yet known. In the case of the PCs being affected by this bug, there is a Notify(BAT0, 0x81) or similar. BAT0 is not yet known but the notify causes a general purpose event (GPE) to be fired which goes unhandled and times out.

When boot option "quiet" is enabled there are very few kernel messages being logged so everything executes faster. When "quiet" is removed, or debugging of any kind is enabled, the additional time taken to log messages gives enough breathing space for the ACPI namespace to be scanned and the other objects created before the timeout occurs.

The _REG(RegionSpace, 1) control method is used to notify AML that an operation region is available. It is not clear from the ACPI specification whether _REG() is allowed to Notify() other nodes. If the namespace is fully scanned it shouldn't be an issue, but when the EC is started early via an ECDT or by virtue of the commit here (intended to provide the ECDT equivalent for BIOSes without it), then it can cause a failure.

I edited the EC's _REG() method and disabled the Notify(BAT0...) call and then installed the revised DSDT in an initrd image. I kept the original initrd with a different name and added an additional boot entry into the GRUB menu. I then tested both initrd images. The one containing the modified DSDT with Notify() disabled starts correctly. The original DSDT causes it to fail.

$ sudo acpidump -b -t DSDT -o DSDT.aml
$ iasl -d DSDT.aml
$ gedit DSDT.dsl

Device (EC)
...

 Method (_REG, 2, NotSerialized)
 {
  If (LEqual (Arg0, 0x03))
  {
   Store (Arg1, ECON)
   Store (BATP, BNUM)
   Store (RSCL, B0SC)
   Store (RPWR, PWRS)
   /* Notify (BAT0, 0x81) not allowed for early-init ECs */
   PNOT ()
   If (LEqual (PRCP, One))
   {
    Notify (DOCK, Zero)
   }

   If (LEqual (WKSR, 0x02))
   {
    Notify (DOCK, One)
   }
  }
 }

I rebuilt the DSDT:

$ iasl DSDT.dsl
$ sudo cp DSDT.aml /etc/initramfs-tools/
$ sudo mv /boot/initrd.img-2.6.24-16-generic /boot/initrd.img-2.6.24-16-generic-ec-bug
$ sudo update-initramfs -u ALL
$ sudo mv /boot/initrd.img-2.6.24-16-generic /boot/initrd.img-2.6.24-16-generic-ec-fix

Now edit /boot/grub/menu.lst, edit the initrd name and add another menu option:

title Ubuntu Hardy 64-bit, kernel 2.6.24-16-generic EC fix
root (hd0,4)
kernel /vmlinuz-2.6.24-16-generic root=UUID=bb2c3a14-1588-4fb9-8411-71f114b568b4 ro quiet
initrd /initrd.img-2.6.24-16-generic-ec-fix
quiet

title Ubuntu Hardy 64-bit, kernel 2.6.24-16-generic EC bug
root (hd0,4)
kernel /vmlinuz-2.6.24-16-generic root=UUID=bb2c3a14-1588-4fb9-8411-71f114b568b4 ro quiet
initrd /initrd.img-2.6.24-16-generic-ec-bug
quiet

------

I have a large collection of DSDTs from across the Vaio range as part of my SNC research. I ran an analysis script on them all to see how many have a Notify() call in the EC _REG() control method (listed as model-BIOS_version):

VGN-AR31S-R0200J6, VGN-AR370E-R0200J6, VGN-C140G-R0030J4, VGN-C1S, VGN-C1ZB-R0034J4, VGN-C22GH-R0080J4, VGN-C240E-R0080J4, VGN-C2S-R0080J4, VGN-C2Z-R0080J4, VGN-FE11H-R0072J3, VGN-FE11H-R0074J3, VGN-FE11M-R0172J3, VGN-FE11M-R0174J3, VGN-FE21H-R0100J3, VGN-FE21M-R0130J3, VGN-FE31M, VGN-FE31M-R0170J3, VGN-FE41E-R0190J3, VGN-FE41M-R0190J3, VGN-FE41Z-R0200J3, VGN-FE45G-R0190J3, VGN-FE550G-R0074J3, VGN-FE590P-R0072J3, VGN-FE660G-R0133J3, VGN-FE670G-R0130J3, VGN-FE690-R0172J3, VGN-FE770G-R0173J3, VGN-FE830, VGN-FE870E-R0190J3, VGN-FE880EH-R0200J3, VGN-FS115M-R0104J0, VGN-FS215B-R0040J1, VGN-FS215E-R0040J1, VGN-FS285H-R0040J1, VGN-FS315E-R0084J1, VGN-FS315H-R0080J1, VGN-FS315S-R0084J1, VGN-FS660W-R0044J1, VGN-FS730W-R0080J1, VGN-FS740W-R0080J1, VGN-FS760W-R0080J1, VGN-FS965F-R0044J2, VGN-FS980-R0044J2, VGN-FZ11M-R0050J7, VGN-N130G-R0020J4, VGN-N230E-R0070J4, VGN-N31Z-R0100J4

This issue could end up impacting a *lot* of users not just of Vaios but other brands too. I've seen at least 3 others mentioned in bug reports in the kernel.org bugzilla. What is worrying is that the kernel ACPI guys seem to be sticking with the early EC initialisation and telling users to create a custom DSDT.

---

### Post by Comhra on 2008-08-09
**I think this is the right one**  **Incidentally, I'm running on a Sony Vaio as well, wouldn't you know.**

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
# kopt=root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Comhra on 2008-08-09
Maybe this is the section that's causing the trouble.
At least this is what I'm thinking.

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro **quiet splash**
initrd /boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by Comhra on 2008-08-09
You sure learn a lot about computers using Linux, I love it.

:lolflag:

---

### Post by Comhra on 2008-08-09
This is what it boils down to:

[B][Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet'
option is enabled
[/B]

Now that's the problem, how do I work around this?

That's what I need to know.

---

### Post by Comhra on 2008-08-09
Oh, I sould mention that this laptop is devoted solely to Ubuntu, I do not have a Windows partition and no, I am **not** going back to XP!

---

### Post by Comhra on 2008-08-09
This is it here:


additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
#** defoptions=quiet splash**

---

### Post by Comhra on 2008-08-09
This is it, I'm pretty sure, it can't be in the last message I posted because the 'quiet splash' is commented out and Ubuntu would just ignore it, right?

So it has to be this one:

Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
**kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2eb240ba-d51e-42d4-97a4-683494a3c5e2 ro quiet splash**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


What if I comment it out?

This is where I need help.

I realise that taking this course of action may have knock-on effects.

---

### Post by Comhra on 2008-08-09
Fingers crossed, I think I found the answer, it's a testament to the community that there is so much information available.  This is my third Hardy install and it was disappointing to find the same, familiar bug awaiting me today.  I think it's fixed, so hopefully I won't be going back to Gutsy.

---

### Post by Comhra on 2008-08-09
If it crops up again I'll be trying the dark art of Kernel compilation, hope I can avoid that.

---

### Post by mrvaio on 2008-10-18
> **Comhra said:**
> This is what it boils down to:

[B][Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet'
option is enabled
[/B]

Now that's the problem, how do I work around this?

That's what I need to know.

The solution is press the F6 button at the start up menu and add at the end of the parameters this little string: **acpi=off**

Regards
Mr Vaio

---

