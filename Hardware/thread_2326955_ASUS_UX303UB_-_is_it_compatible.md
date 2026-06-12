---
title: "ASUS UX303UB - is it compatible?"
date: 2016-06-06
forum: Hardware
---

### Post by g-rodola on 2016-06-06
Is there anyone having this laptop that can tell me how good it works on Ubuntu? External monitor? Wi-fi? Touchpad?

---

### Post by christiaan3 on 2016-06-07
I have installed ubuntu on an ASUS laptop before, not your exact type. In my experience Ubuntu pretty much works perfectly with all systems. I think you are safe to install ubuntu on your laptop without it causing any issues.

Christiaan

---

### Post by howefield on 2016-06-07
> **g-rodola said:**
> Is there anyone having this laptop that can tell me how good it works on Ubuntu? External monitor? Wi-fi? Touchpad?

Try a search for "ASUS UX303UB ubuntu" and you'll get a few hits, here is a recent thread from these forums..

[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)

There will be others :)

> **christiaan3 said:**
> I have installed ubuntu on an ASUS laptop before, not your exact type. In my experience Ubuntu pretty much works perfectly with all systems. I think you are safe to install ubuntu on your laptop without it causing any issues.

Interesting concept, install Ubuntu successfully on one random Asus laptop, so it must work on all laptops. I'd like to live on your planet.

---

### Post by shaan2 on 2016-06-09
Hi there, everything works out of the box, except keyboard backlight and screen brightness control, to solve these issue, 

Add acpi_backlight=none acpi_osi= 
to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and you are good to go.......

Your grub file will be like this....



# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=none acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

Dont forget to update grub after adding the kernel parameter, to do that
 
run command update-grub in terminal........


Hope it helps...

---

