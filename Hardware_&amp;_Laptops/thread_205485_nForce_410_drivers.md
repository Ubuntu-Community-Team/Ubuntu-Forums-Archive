---
title: "nForce 410 drivers"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by ModemManCJ on 2006-06-28
Hello,
  I just got around to installing Ubuntu 6.06 on my new machine that I built, but I've not had any luck with getting the onboard LAN running. I can connect to the Internet fine on my Windows XP partition, but I can't even ping in Ubuntu. It does, however, detect "eth0".

My guess is that I needed to install Linux drivers for my chipset ([nForce 410]("http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html"), which adds support for sound and LAN), but I've run into difficulty with that too. It requests that the kernel source be installed. I've installed a number of packages that I thought it wanted, and I've tried to point to the kernel source path (/usr/src/), but it still refuses to install. Am I installing the wrong packages, or am I totally off on how to get the LAN running?

I confess that I don't know much about Linux, so if anyone needs any diagnostics, please tell me how to go about getting them for you.

My motherboard is a [Biostar GeForce 6100-M9]("http://www.biostar.com.tw/products/mainboard/board.php?name=GeForce%206100-M9").

Any help is much appreciated!
 - C.J.

---

### Post by eqisow on 2006-07-12
I'm having the same problem with aBiostar Tforce 6100-939 (nforce 410 chipset). Any advice would be appreciated.

---

### Post by setakht on 2006-07-12
What I've found that works is totally unplugging the machine (and turning off the ATX power switch) for about 10 seconds before plugging it back in and rebooting in.  Something about the forcedeth driver in Linux doesn't allow it to work correctly after the Windows drivers have been used.  The Wake on Lan function on 410 boards means the ethernet port doesn't reset itself even though the rest of the computer is off because of ATX power going to it.  The Nforce drivers don't have this problem, and I can switch between Windows and Linux without having to pull out the power plug.

---

### Post by rumpa on 2006-09-15
First SOrry for my english!!!

I've got a mainboard based on a nforce410 and the only way to do net working is to execute 
sudo /etc/init.d/networking restart

only first timr you boot ubuntu

---

