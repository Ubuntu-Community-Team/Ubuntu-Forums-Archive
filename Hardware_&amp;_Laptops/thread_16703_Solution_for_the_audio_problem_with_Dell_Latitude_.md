---
title: "Solution for the audio problem with Dell Latitude D505"
date: 2005-02-23
forum: Hardware &amp; Laptops
---

### Post by papageno on 2005-02-23
Hi,
i found the solution at my problem!!!
At the URL: [http://www.shahidhussain.com/wordpress/index.php?p=30](http://www.shahidhussain.com/wordpress/index.php?p=30) is illustred the solution:
Open up your .lst file by typing this:
sudo nano /boot/grub/menu.lst
Then find this line:
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash
And insert an option to force the IRQ:
kernel /boot/vmlinuz-2.6.8.1-3-386 acpi_irq_isa=7 root=/dev/hda4 ro quiet splash
Then reboot the machine to reload the kernel with the new option.

Papageno.  :grin:

---

