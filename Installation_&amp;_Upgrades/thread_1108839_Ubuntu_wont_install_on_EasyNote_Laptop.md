---
title: "Ubuntu wont install on EasyNote Laptop"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by siabost on 2009-03-28
Hi,
Packard Bell EasyNote Laptop F5280HR
Celleron 2.8Ghz
256Mb Memory Installed (effective memory = 192Mb as rest used for graphics)

I have tried both standard & alternate install disks and failed to get past the initial options menu.

With the standard install disk (Ubuntu 32bit 8.04.2) I get the initial "choose language" screen and when I select "Install Ubuntu" the loading bar gets to about 70% before permanently freezing. The same occurs with all F4 & F6 options.
I realised this option requires about 384Mb of memory so I tried the "alternate" disk. With this I don't even get that far. On selecting to install it briefly flickers some text on the screen which then goes blank and remains so. It doesn't make any difference if I use the F4/F6 options. I have not tried the "install command line system" option as I am not familiar enough with the command line.

I'm loathe to buy extra memory for this laptop (it has a max of 512Mb and it's desktop type memory rather than laptop) until I'm sure it will load Ubuntu. Catch 22, maybe?

Are there any options I can use to get a basic Ubuntu system loaded?

Any help much appreciated.

Thanks in advance.

---

### Post by Mark Phelps on 2009-03-28
You're probably NOT going to be able to install Ubuntu on a machine with such minimum graphics memory.  You should look around for a less-memory intensive Linux such as Puppy Linux.

Go to the distrowatch.com website for a list of Linux's,

---

### Post by siabost on 2009-03-28
Update:
I've upgraded the memory to 512Mb+

The process doesn't get to the partitioning but stops while uploading the initial system at the following 5 lines:

> cat: /var/lib/acpi-support/system-manufacturer:No such file or directory
cat: /var/lib/acpi-support/system-product-name:No such file or directory
cat: /var/lib/acpi-support/system-product-version:No such file or directory
cat: /var/lib/acpi-support/bios-version:No such file or directory
* Saving VESA state...

This is the same whether selecting the F6 acpi-off option or not.

I need to use Ubuntu as I was looking to load up Ubuntustudio.

Ta.

---

### Post by siabost on 2009-03-28
Managed to install Ubuntustudio by adding vga=771 to the boot command using F6.

Now though I have the same problem when booting Ubuntustudio from hard disk - it sticks at about 70% loaded.

I think it must be a screen resolution problem.

Will start new thread re this.
Ta

---

