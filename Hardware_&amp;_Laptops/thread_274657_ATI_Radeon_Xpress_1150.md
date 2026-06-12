---
title: "ATI Radeon Xpress 1150"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by manishk on 2006-10-10
Please note: I'm new to Ubuntu

Hi,
   I am planning to install Ubuntu on my **HP nx6325** laptop-AMD Turion X2 (64-bit dual core). It has an **ATI Radeon Xpress 1150** for the display. And I'm currently using only Win XP Pro on it.

   :confused: It would be nice if you can tell me these-
1. When I start a session with the LIVE CD, how can I fing out if all the devices were detected? Like Wi-LAN card, bluetooth etc.(Is there something like Win's Device Manager)

2. I've (only) read some reviews and seen some screen shots of Ubuntu using XGL with Compiz and it looks awesome...but all the HOWTOs wanted some *fglrx* drivers for that. Is there any for Xpress 1150??

3. The Laptop's Wiki says that nx6325 supports Ubuntu 6.10 'with **noapic** kernel parameter'. Whats that??

Thanks in advance.:D

---

### Post by Kateikyoushi on 2006-10-10
1. There is a device manager in ubuntu as well, Under system >> administration. My wireless adapter did not work from live cd but worked out of the box after the install so even something won't work from the live cd you have a chance that it works after the install without any manual installation.

2. Honestly I do not know, out of curiousity I installed XGL and compiz on an Nvidia machine took me about 10 minutes no real hassle.

3. It means when you boot the live cd you have to add the noapic kernel parameter to be able to boot it.

[QUOTE=T700]APIC stands for Advanced Programmable Interrupt Controller. It was a chip designed to use the timing circut from the computer's silicon quartz clock to coordinate multiple (up to 60, as I recall) processors. It never worked very well and many modern computers don't implement it, so it is not generally accessed by default in Linux.[/QUOTE]

---

### Post by manishk on 2006-10-11
Thanks.

Can you also tell me how do I put this *noapic* parameter and where??

---

### Post by j_baer on 2006-10-11
I have a ASUS system with a Radeon PCIE card. I placed the acpi=off argument at the end of the kernel boot line in the menu.lst file.

sudo gedit /boot/grub/menu.lst

You can also test this with the live cd by adding this argument at boot.

Cheers

---

