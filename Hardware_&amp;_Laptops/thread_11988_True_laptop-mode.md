---
title: "True laptop-mode"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by Arkainium on 2005-01-20
I notice the laptop-mode script sets a spindown time for the hard disk.  Unfortunately, it never spins down anyway because there's disk access like every 5 seconds.  I've disabled my swap, mounted /tmp as tmpfs.  I also disabled sysklogd, klogd, cron, atd, yet still, my hard disk is being accessed while idle.

I'm guessing it's the kernel saving dirty buffers.  In /proc/sys/vm/ there's a laptop_mode file.  I set it to 1, but it always resets to 0 after a couple seconds.

I don't know what to do, I don't want *any* disk access while I'm idle.  Anyone successfully accomplish this?  Do you think there are any benefits to spinning down the disk rather than constantly saving in case of a crash?  I'm thinking of just turning laptop mode off completely as it doesn't appear to do much.

Also, what else are you doing to save every last bit of power when running on battery?  I'd love to get suspend working, but 'echo 3 > /proc/acpi/sleep' won't work unless I disable USB2 support, and when I do, I have no clue how to come out of sleep.  I'm forced to turn off the laptop.

---

### Post by jerome bettis on 2005-01-21
mine does in fact spin down. 

i wouldn't worry about losing work because of a crash.  at the most, it would be 4 or 5 minutes lost, no big deal.

keep in mind, this is an example of the rent to own problem.  if you have it spin down too often, the energy the drive consumes in spinning itself back up might be greater than the energy it would have used if you would have just left it spinning.

post your config file.  does your acpi work right?  it doesn't sound like it .....

edit: to come out of sleep try ctrl + alt + F7

---

### Post by Arkainium on 2005-01-21
Mine spins down also, but I spins right back up because my disk is constantly being accessed.

Which config file?

I just tried to sleep, ctrl + alt + F7 didn't wake me.  :(

---

### Post by Rxke on 2005-10-02
Bit of a late reply, but this [http://www.ubuntuforums.org/showthread.php?t=36976&highlight=sound+laptop-mode](http://www.ubuntuforums.org/showthread.php?t=36976&highlight=sound+laptop-mode) worked for me.

---

