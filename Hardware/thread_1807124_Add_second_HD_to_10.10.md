---
title: "Add second HD to 10.10"
date: 2011-07-18
forum: Hardware
---

### Post by claven123 on 2011-07-18
I need to add a second HD to my dual boot Ubuntu 10.10 install.  A friend is going to give me a clean new 500Gb HD.  

What happens when I turn on the computer (booting into Linux) with the added HD?

Do I have to format it a special way, do I have to partition it.....  I only want to use it with linux, so don't need to mess with windows.

Or, can someone direct me to a wiki or tutorial on how to do this?

Thanks,

Dennis

---

### Post by kherring7383 on 2011-07-18
If the hard drive is new and hasn't been formatted, Ubuntu will detect it. However,if you plan to use this drive exclusively with Ubuntu then you will need to use Gparted to create a new partition and format it to ext4. If however the drive will be used as a shared drive in a dual boot system, then you should format it to NTFS which can be accessed by both Ubuntu and Windows. The reason I suggest this is that this scenario has worked rather well for me. While I don't dual boot with a single drive I choose to use separate O/S drives and a second one for data for both Windows and Ubuntu.

---

### Post by jerrrys on 2011-07-19
more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+hdd+hard+drives&sa=Search&cof=FORID:9#1031](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+hdd+hard+drives&sa=Search&cof=FORID:9#1031)

---

