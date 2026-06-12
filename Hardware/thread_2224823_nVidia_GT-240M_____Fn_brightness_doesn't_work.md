---
title: "nVidia GT-240M     Fn brightness doesn't work"
date: 2014-05-18
forum: Hardware
---

### Post by heian on 2014-05-18
Hi,

My Lenovo Ideapad Y450 laptop got this videocard:  nVidia GT-240M

In Ubuntu 12.04 it was possible to get the Fn brightness working due to this 'trick':

Open a terminal window and type:
sudo gedit /etc/X11/xorg.conf
On the “DEVICE” section append the following line:
Option "RegistryDwords" "EnableBrightnessControl=1"


After a fresh install of Ubuntu 14.04, it seems this is not working anymore.

Is there anybody who got this working, and how did you do that?

---

### Post by jeremy31 on 2014-05-18
Have you tried editing the grub to include acpi_backlight=vendor or video.use_native_backlight=1

The video.use_native_backlight=1 was just included in the 3.13 kernel that Ubuntu 14.04 uses

You can try an edit when the grub screen comes up doing boot
[IMG]http://www.dedoimedo.com/images/computers_new_2/grub2-dual-boot-in-grub2.png[/IMG]

Yours will probably say Ubuntu 14.04 3.13 something
press 'e' to edit, scroll down to the line that starts with linux and then scroll right so you are after quiet splash or $vt_handoff and then use whichever entry you want but just try one at a time.  When you have finished the edit press F10 to boot

---

### Post by heian on 2014-05-18
Hi Jeremy31,

I don't see the screen as your picture, it just boot fast till i need to put my root password.
However i found my grub file and copy paste it to here. (im a noob about this kind of stuff, just like to work with ubuntu)
This is my Grub, what do you advice me to change?

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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

---

### Post by jeremy31 on 2014-05-18
> **heian said:**
> Hi Jeremy31,

I don't see the screen as your picture, it just boot fast till i need to put my root password.
However i found my grub file and copy paste it to here. (im a noob about this kind of stuff, just like to work with ubuntu)
This is my Grub, what do you advice me to change?

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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

I don't like doing tests this way, but I would change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#000000] video.use_native_backlight=1[/COLOR]"

To actually edit you will have to use gksudo gedit /etc/default/grub in the terminal, enter password, make changes, save, exit program, and then in terminal sudo update-grub and restart

---

### Post by heian on 2014-05-19
I had made the change in Grub,  but it doesn't work so far.
There was a message in the terminal, while updating Grub:

:~$ sudo update-grub
[sudo] password for heian: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

Is that the reason it doesn't work, and is there something i can do about it or trying something?

---

### Post by jeremy31 on 2014-05-19
Edit grub again, delete the video.use_native_backlight and try acpi_backlight=vendor 
Save and sudo update-grub and reboot

---

### Post by heian on 2014-05-19
I made the change to acpi_backlight=vendor, but still the 
brightness doesn't change. 

~$ gksudo gedit /etc/default/grub
(gedit:2691): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: 
The name org.gnome.SessionManager was not provided by any .service files

during the grub update i got the same message as earlier.

Is there something that i can try, and does it matter if an other driver is installed for the videocard?

---

### Post by heian on 2014-05-19
trying to add a screenshot

---

### Post by heian on 2014-05-20
finally got it working !    :)

using the X.orgX server - Nouveau display driver  or the  Nvidia binary driver - version 331.38   driver.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1" is in my Grub.

Thanks for setting me on the right track!

---

### Post by jeremy31 on 2014-05-20
Good to hear, I thought I recommended the 331 driver but it didn't show up here, must have been a different forum.  The 337 driver is supposed to be good for the 3.15rc kernel

---

