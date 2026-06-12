---
title: "Beeps when restarting or to turn off"
date: 2008-08-13
forum: Hardware
---

### Post by RafaelCapati on 2008-08-13
Hello personal, 

Recently I installed Ubuntu 8.04 and the times when I restart the system, I hear several beeps, the times it is only an and the times he restarts or it turns off without problem.

My configuration:

AMD ATHLON 64 X2 6000+ AM2
ASUS M2N32 SLI Deluxe Wireless
MB KINGSTON DDR2 2GB 800mhz
NVidia GForce 8600 GT 256 MB
Hd Maxtor 160 Gb 7200 Rpm Sata
Font 460w Cooler Master Extreme Power Plus
Cooler Zalman 9700NT

I already researched and I didn't find anything that solves.

At once, I thank.

---

### Post by tangibleorange on 2008-08-13
Sorry, I don't quite understand.

Are you saying that the system always shuts down successfully and the beeping is simply annoying, or does it sometimes beep and not shut down at all?

---

### Post by OutOfReach on 2008-08-13
Try this, goto System>Preferences>Sound, now goto into the System Beep tab, and disable System Beep.

---

### Post by RafaelCapati on 2008-08-13
> **tangibleorange said:**
> Sorry, I don't quite understand.

Are you saying that the system always shuts down successfully and the beeping is simply annoying, or does it sometimes beep and not shut down at all?

The system restarts or it turns off following by several beeps, that happens only the times. The system not of the any problem, and only to restart or to turn off that a console screen exhibits messages of "Failed" following by several beeps. After the beeps he usually restarts / shutdown.

[QUOTE=OutOfReach]Try this, goto System>Preferences>Sound, now goto into the System Beep tab, and disable System Beep.[/QUOTE]

Already try that, but it doesn't solve.

---

### Post by tangibleorange on 2008-08-13
OK well to disable the beeps you can try these two commands (one after the other):

```
sudo rmmod pcspkr
```

and then this:

```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist
```

Hopefully you will now be beep-free! If your system fails to shutdown, another way to shut down is to run this command:

```
sudo shutdown -h now
```

Make sure you save any work BEFORE using that command, as it will immediately begin the shutdown process.

Good luck!

---

### Post by RafaelCapati on 2008-08-14
TThanks **tangibleorange**, ended with the beeps.

But now I wanted to solve the problem to be failing. The console displays four lines, something like:

```
networkmanager (md_bus signal device ...
```

Do you have any idea of what can be?

---

### Post by tangibleorange on 2008-08-14
could you post the output of your /boot/grub/menu.lst?
```
cat /boot/grub/menu.lst
```

---

### Post by RafaelCapati on 2008-08-14
Yes, see:

```
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
# kopt=root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash locale=pt_BR

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro quiet splash locale=pt_BR
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by tangibleorange on 2008-08-14
OK. When you reboot and you get the menu showing you the operating systems, press 'e'. then scroll down to the line that begins with kernel and press 'e' again. at the end of the line that's displayed, type:
```
acpi=off
```
it should now look like this:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro quiet splash locale=pt_BR acpi=off
```
then press enter, and then 'b' to boot. If it now hangs, don't worry, simply turn it off and reboot, it will be back to normal. If it does boot however, try shutting down and see what happens.

---

### Post by RafaelCapati on 2008-08-14
As I said but not resolved.

I took the photo of the screen, the lines are exactly that:

```
NetworkManager Debug [1218745476.716998] nm_pr_ int_open_socks(): Open Sockets
List Done.

Network Manager: (NARM) nm_hal_deinit(): libhal shutdown failed - Connection is Closed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
```

---

### Post by tangibleorange on 2008-08-14
ok try adding more options using the same technique as above:
```
acpi=off noapic nolapic
```
so it looks like:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro quiet splash locale=pt_BR acpi=off noapic nolapic
```

---

### Post by RafaelCapati on 2008-08-14
When I was editing again, the line acpi=off was not more, it is normal ?

Added the new commands, started the system and restarted using:

```
sudo shutdown -r now
```

Messages of failure are the same. But when restart without using command, I do not know whether it is coincidence, but the messages are not displayed.

---

### Post by tangibleorange on 2008-08-15
so does it shutdown normally?

---

### Post by RafaelCapati on 2008-08-16
Well, apparently this should all normal, Only when using the command to shutdown that the message is displayed.

---

