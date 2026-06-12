---
title: "Maximum Memory"
date: 2009-03-23
forum: Hardware
---

### Post by dwall02 on 2009-03-23
Hello, I have upgraded my system with the following:

Mother Board - Gigabyte - Ultra Durable 3 - MA790GP-UD4H
CPU - AMD Phenom II X4 - 3.0 GHz True Quad-Core Design - 8.0 MB Total Cache - Socket AM2+
RAM - OCZ High Performance DDR 2 - 2 X 2 GB - 8 GB (Total RAM)

I re-installed Ubunut 8.10 x64, and when I look at my system, I see that I am using only 2GB of RAM. 

<system name>:~$ free -g
             total       used       free     shared    buffers     cached
Mem:             2          2          0          0          0          1
-/+ buffers/cache:          0          2
Swap:            6          0          6

Everything I have read so far states that the x64 version supports the RAM.  I can't seem to find out why I am only seeing 2GB.

Does anyone have any suggestions?

Thanks,

Dan

---

### Post by jespdj on 2009-03-23
If you go into the BIOS setup when booting the computer, does the BIOS show all of your 8 GB RAM?

Try running the memory test program (memtest86+) by selecting it from the GRUB boot menu. Does memtest86+ see all of your RAM? Does it report any errors after letting it run for a few hours?

Motherboard manufacturers most of the time have a QVL (Qualified Vendors List) that lists which brands and models of RAM modules they have tested their motherboard with. Are your RAM modules on that list?

Are you sure that the RAM modules you bought don't need specific manual voltage or timing settings that you have to set in the BIOS of your computer?

---

### Post by dwall02 on 2009-03-23
Jespdj,

Thank you for the quick reply.  When I get home from work tonight, I will check this out.  It couldn't hurt to go back to the book on this as well.

---

### Post by dwall02 on 2009-03-23
I checked my system, and the BIOS says 8GB. I ran the memory test and the memory test sees 8GB.  I have not ran it for a few hours, but will let it run throughout the night.  I contacted GigaByte and they said that typically the 1066 speed memory is only supposed to have 1 DIMM in 1 slot of each bank, i.e. 1x2 GB in slot 1, and 1x2 GB in slot 3, just to get 4GB.  I guess to get 16 GB (board max), using 1066, I will need  2x8 for thoses slots.  However, since the BIOS recognized it, they said my O/S should too.

---

### Post by dwall02 on 2009-03-25
I'm not sure what happened, but I ran the memory test for 8 hours, and had no errors.  The memory test said I had 8GB.  Then I updated to the Sever Edition and rebooted.  I had 8GB.  Then I decided to try to re-format and install 8.10 from scratch. (Originally, went from 8.4 to 8.10), and the 8.10 shows 8GB.  Thanks for your help

---

