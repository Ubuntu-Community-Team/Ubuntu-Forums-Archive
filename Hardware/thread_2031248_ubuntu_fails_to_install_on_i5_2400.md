---
title: "ubuntu fails to install on i5 2400"
date: 2012-07-21
forum: Hardware
---

### Post by iurobpn on 2012-07-21
Let me lead with the hardware:
Processor:i5 2400
Motherboard: asus P8H61-M LX3
RAM: 4 gB ddr3 1300 MHz
Video: nVidia geforce gtx 460
hd 1 TB - samsung

I'm trying to install ubuntu 12.04 64 bits and the installation freezes on right after the start of the boot on a black screen with the cursor blinking on the top left corner. I also tried to install linux mint and opensuse, so I think it's hardware related. I tried to change something on the BIOS(it's EFI BIOS, it's different than I'm used to) and nothing. In the ark.intel.com, says that the architecture it's intel 64 bits, there is a different 64 bits architecture from intel now? The windows 7 installation works fine, but I need a distro to work, preferable ubuntu. Any Help?

thanks,

Iuro

---

### Post by Vakman on 2012-07-21
Has anything happened already, as in does it actually begin to boot from the disc or does this happen as you are trying to boot from the disc and stay on the "blinking line/black screen"?

Sorry, I am just trying to determine if it has actually begun booting from the disc at all.
If it has, EDIT: Do as the post below says.

---

### Post by efflandt on 2012-07-21
When you see the first purple screen with keyboard and round symbol at bottom, press any key.  After confirming your language and you get to text menu hit **F6** and select **nomodeset** (spacebar to X it) then **Esc**.

The **nomodeset** kernel boot parameter seems to be needed for 12.04 install with nvidia graphics, but you should not need that once it is installed.

---

### Post by iurobpn on 2012-07-21
I managed to install through alternate cd. Ubuntu stopped in a black screen again, every time I tried to inicialize. I entered in the safe mode, installed the package nvidia-current and runned dist-upgrade via apt.

The p&#341;oblem was probably the lack of a geforce module in the kernel.

Thank's for the replies,

Iuro

---

