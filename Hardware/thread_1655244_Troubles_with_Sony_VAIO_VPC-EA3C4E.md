---
title: "Troubles with Sony VAIO VPC-EA3C4E"
date: 2010-12-29
forum: Hardware
---

### Post by Vinyadan on 2010-12-29
Good day everyone!
 I recently bought a Sony VAIO VPC-EA3C4E, with Windows 7 preinstalled.  My previous portable computer was an Acer Aspire One which came with  Linpus. Since I felt it to be rather limited, I tried various other  Linux distributions to make the netbook more flexible without becoming  too slow. At lenght I discovered the Linux4One version, which I then  used for a long time. Now that I have a more powerful computer, I  immediately thought of installing Ubuntu on it, since it had been a good  operating system on the very limited Acer,
I installed Ubuntu through usb key, and right now it is the 11.04  version (I'm not sure which version it was when I installed it).
The OS substantially works fine, programs run well, wireless connections  don't show any problem, and so on. However, there are two problems:
1. The touchpad doesn't work
2. The screen shows some strange colors while surfing the Net with  Mozilla Firefox: orange becomes green and, in the Ubuntu starting page,  the Google logo shows these colors: purple, blue, green, purple, orange,  blue. I used Firefox on many other computers and never had this  problem. On the other hand, Opera works fine.

I run the application to find available drivers, but it didn't help. I  tried to fix the touchpad problem (the touchpad works fine with Windows)  following the instructions contained in this thread:
[http://ubuntuforums.org/showthread.php?t=1565548](http://ubuntuforums.org/showthread.php?t=1565548)
Unfortunately I had no good result. The only change is that now, when  Ubuntu loads, instead of showing the purple page it shows text  describing the system loading. Also, I never did such a thing before and  I probably misunderstood some parts. My Grub right now looks like this:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"
GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"Did I do something wrong with the Grub? Is there any way to solve these problems?

Thank you in advance!

---

