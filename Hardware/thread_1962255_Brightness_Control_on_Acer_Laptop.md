---
title: "Brightness Control on Acer Laptop"
date: 2012-04-20
forum: Hardware
---

### Post by chantaspell on 2012-04-20
Hi

I have just installed xubuntu on my laptop and I am unable to adjust the brightness of the screen....at the moment it is very bright!!!

The laptop is an Acer 5755G core i7 nvidia gt540m

The function keys (FN+arrows) bring up the image of the sun and the slider moves, but the screen brightness doesn't actually change. Other function key shortcuts, for volume, wireless, touchpad etc work fine. 

I have done some research on this forum and elsewhere, and I have a solution of sorts:

> echo 65 | sudo tee /sys/class/backlight/intel_backlight/brightness
but I would like to have an easier way of controlling this.  

I have tried:

adding 

> Option "RegistryDwords" "EnableBrightnessControl=1"to xorg.conf but with no success.

The output of 
> lspci | grep VGAis

> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)
tried 

> sudo setpci -s 01:00.0 F4.B=0
sudo setpci -s 01:00.0 F4.B=7F
sudo setpci -s 01:00.0 F4.B=FFto no avail.

the output of 

> ls /sys/class/backlightis

> acpi_video0  intel_backlightAny ideas where to go from here? Would really appreciate any help....am loving xubuntu but this is driving me crazy...

thanks!

---

### Post by Toz on 2012-04-20
Have you tried adding the **acpi_backlight=vendor** kernel parameter? I'm not sure it will work, but it might be worth a try.

There is also an active bug report for this device. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925690]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925690").

Barring that, you could create a workaround script to manage the brightness (since "echo 65 | sudo tee /sys/class/backlight/intel_backlight/brightness" works) and assign it to the brightness keys.

---

### Post by chantaspell on 2012-04-20
Hi thanks for ideas...I can't quite work out how to add a kernel parameter...should it look like:


> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor

or am i missing something....also, i am too much of a noob to know how to make a workaround script...wldnt know where to begin....but many thanks for the help!!

:)

---

### Post by chantaspell on 2012-04-20
Nope, of course the correct syntax is 

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor 			 		

and......it worked!!!

Thanks for the help!

---

### Post by timzak on 2012-05-03
Thanks, this helped me get the brightness control working on my Acer 7736Z.  Just a small correction on quote placements:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" 
```

Also, a separate problem on my laptop, the touchpad on/off button would turn the touchpad off, but not back on.  This addition to the above fixes the touchpad button too:
```
GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux quiet splash acpi_backlight=vendor"
```

---

### Post by chantaspell on 2012-05-04
Yes! I recognised my mistake when I tried it first, and then managed to post exactly the same error here! Thanks for correcting that....will try my touchpad and see if i have the same problem :)

---

### Post by kid1000002000 on 2012-06-08
Thanks- I was having the same problem and this fixed it. :KS

---

### Post by espinozaluis on 2012-08-04
Hi Chantaspell, I follow the thread and tried to do so, but could not get it yet. I have an Acer laptop 5755g-6823 I5-2430M Nvidia geforce GT540M. My grub file after I modified it is like this: (see below) what should I change? thanks a lot. -Luis :)
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

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
sudo upgrade-grub

---

### Post by Toz on 2012-08-04
> **espinozaluis said:**
> Hi Chantaspell, I follow the thread and tried to do so, but could not get it yet. I have an Acer laptop 5755g-6823 I5-2430M Nvidia geforce GT540M. My grub file after I modified it is like this: (see below) what should I change? thanks a lot. -Luis :)
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

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
sudo upgrade-grub

Hi espinozaluis and welcome to the forums.

Remove the last line (sudo update-grub) from your grub file - it doesn't belong there. Save the file, then run:
```
sudo update-grub
```
...to commit the changes.

---

