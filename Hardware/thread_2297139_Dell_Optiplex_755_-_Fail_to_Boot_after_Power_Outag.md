---
title: "Dell Optiplex 755 - Fail to Boot after Power Outages"
date: 2015-10-01
forum: Hardware
---

### Post by fj401971 on 2015-10-01
There were several power outages at my home back to back.  I've got a Dell Optiplex 755 plugged into a surge protector.

After the power was restored, the computer to failed to boot, it would get stuck at the GRUB boot menu and not go any further.  Any action would cause the machine to restart.  I was able to run a RAM test and discover all kinds of errors.  

I shut the machine back down and removed the very first stick of RAM(it had 4 sticks installed).  It booted immediately without problems afterwards. (I even reinstalled the ram stick to make sure that was the problem and it sure was, it would not boot with that RAM stick installed).  

Just wanted to get this posted for other people and to see if anyone else has experienced something like this...

---

### Post by tgalati4 on 2015-10-01
Sudden shutdown leaves stray voltage floating around the motherboard trying to get out.  Sounds like your RAM stick took a hit.  Consider yourself lucky that the motherboard is OK.  There may be other problems, so do some stress testing.  Dell has diagnostic utilities, look for them on the Dell website for your 755.  Run through the set and make sure the rest of the hardware is OK. 

Time to get an UPS.

---

### Post by weatherman2 on 2015-10-01
The cautionary tale here is: buy a UPS (Uninterruptible Power Supply or battery backup) so that you won't have to put your hardware at risk like this due to power outages.  Get a UPS that has a USB port so you can connect it to your computer.  Then the computer will sense it is running on battery when the power goes out and it will shut down safely before the battery has completely drained.

---

