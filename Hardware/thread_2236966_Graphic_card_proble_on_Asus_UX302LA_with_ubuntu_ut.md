---
title: "Graphic card proble on Asus UX302LA with ubuntu utopic"
date: 2014-07-29
forum: Hardware
---

### Post by Fabrice_EDON on 2014-07-29
Hello,

When I run the graphic test of "System testing", I got an error. ```

 ------------- VIDEO DRIVER INFORMATION ------------- 
------------- HYBRID GRAPHICS CHECK ---------------- 
Graphics Chipset: Intel (8086:0a16) 
Loaded DDX Drivers: intel, modesetting, fbdev, vesa 
Hybrid Graphics: no 
ERROR: No video driver loaded! Possibly in failsafe mode! 


```
```

 Not software rendered: no 
Compiz supported: no 


```

My grub file ```

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
GRUB_CMDLINE_LINUX="i915.modeset=0"

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
Video also are really slow.

I'm trying to make the graphic card work with my computer. First I tried Linux Mint but I wasn't able to fix it. Here is the post telling what I tried :
[http://forum.linuxmint.com/viewtopic.php?f=59&t=172149&p=884910](http://forum.linuxmint.com/viewtopic.php?f=59&t=172149&p=884910)

The final idea was to go on a more recent kernel which I did by installing ubuntu utopic, krenel version 3.16.
It's still not working. 

Do you have any idea what should I tried now?

Thank you,
Fabrice

---

### Post by QIII on 2014-07-29
Hello!

Are you aware that Utopic is still in development and has not been finally released yet?

Are you testing?

---

### Post by Fabrice_EDON on 2014-07-30
No. I just want to use the latest kernel in order to get the driver and utopic is the only release I've found with 3.16.

---

### Post by Fabrice_EDON on 2014-07-31
Any ideas ? Should I go back to the latest release ?

---

### Post by Fabrice_EDON on 2014-08-09
Still no ideas? :s

---

### Post by Yellow Pasque on 2014-08-10
> GRUB_CMDLINE_LINUX="i915.modeset=0"
Is there a reason you're turning off kernel modesetting? That's probably the cause of your issue.

---

