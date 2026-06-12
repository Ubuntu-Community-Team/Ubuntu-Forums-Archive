---
title: "usb 3 card driver missing for 18.04"
date: 2018-12-24
forum: Hardware
---

### Post by Robbyx on 2018-12-24
This seems to be the link for my board:

[https://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Download&os=Win7]("https://www.asrock.com/mb/AMD/FM2A88X%20Extreme6+/?cat=Download&os=Win7")

I have some USB 3 cards that are not being recognised.  

This topic implies it is due to a missing driver:

[https://linustechtips.com/main/topic/81939-2-usb-30-porst-are-not-working-on-asrock-extreme6-lf-drivers/](https://linustechtips.com/main/topic/81939-2-usb-30-porst-are-not-working-on-asrock-extreme6-lf-drivers/)

The main chip on the card is a VLI (VL805-06)

Does anyone have experience of getting this card to work with Ubuntu on the ASROCK board.

---

### Post by CatKiller on 2018-12-24
You'll need to make sure that your BIOS is set to XHCI rather than EHCI.

---

### Post by Robbyx on 2018-12-26
Do you know how I can check if the bios is set to xhci?

ASROCK offers a UEFI setup utility. I have been through its manual. There is no reference to either xhci or ecci.  

this is an extract from the manual:

**USB 2.0 Controller**
Use this item to enable or disable the use of USB 2.0 controller.
**A88X USB 3.0 Controller**
Use this item to enable or disable the use of USB 3.0 controller.
**Legacy USB Support**
Use this option to select legacy support for USB devices. There are four
confi guration options: [Enabled], [Auto], [Disabled] and [UEFI Setup Only].
The default value is [Enabled]. Please refer to below descriptions for the
details of these four options:
[Enabled] - Enables support for legacy USB.
[Auto] - Enables legacy support if USB devices are connected.
[Disabled] - USB devices are not allowed to use under legacy OS and
UEFI setup when [Disabled] is selected. If you have USB compatibility is-
sue, it is recommended to select [Disabled] to enter OS.
[UEFI Setup Only] - USB devices are allowed to use only under UEFI
setup and Windows / Linux OS.
**Legacy USB 3.0 Support**
Use this option to enable or disable legacy support for USB 3.0 devices.
The default value is [Enabled].

---

### Post by CatKiller on 2018-12-26
Ugh. It's horrible when the settings are obfuscated by marketing speak. I can't find a straightforward reference to that setting, either. 

However, I have now seen lots of reports that those ports on that chip will only work with IOMMU disabled in the BIOS and iommu=soft set as a kernel parameter in /etc/default/grub.

---

### Post by Robbyx on 2018-12-26
Thank you for checking your sources. 

Following your suggestion to put a kernel parameter into the grub, I am not sure how to  adjust my grub for this change? This is it as currently 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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

### Post by CatKiller on 2018-12-26
> **Robbyx said:**
> Following your suggestion to put a kernel parameter into the grub, I am not sure how to  adjust my grub for this change? This is it as currently 

You'd change ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft"
``` and then run ```
sudo update-grub
```

---

### Post by Robbyx on 2018-12-26
I have made the changes to the Grub, I tested the cards using usb 2 and 3. They were not being recognised. I checked via LSUSB and the devices plug in to the cards were not appearing. 

I also switched the USB settings in the UEFI to auto compatibility and the same test as above was negative. 

What else can I do?

---

### Post by CatKiller on 2018-12-26
Did you disable IOMMU in the BIOS?

---

### Post by Robbyx on 2018-12-26
Yes. I disabled IOMMU

---

### Post by CatKiller on 2018-12-26
That's a shame. That was the one consistent fix I'd found for that issue. Hopefully someone will come by with something else.

In the meantime, there might be something in dmesg that might shed some light on another approach.

---

### Post by Robbyx on 2018-12-31
I saw nothing in dmesg that seemed relevant. What would you suggest I search on using:

dmesg | grep ????

---

