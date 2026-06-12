---
title: "HDD spins down randomly in the middle of processes"
date: 2008-12-17
forum: Hardware
---

### Post by Awfulwaffle on 2008-12-17
Hey,
Like the title says, I'm having a problem with what seems to be my hard drive spinning down randomly when it shouldn't. The drive is a 120GB 5400 RPM drive in a Compaq F750US dual booting Intrepid Ibex and WinXP. I also had Hardy Heron installed for a brief period before, and the same problem occurred. 

I first noticed the issue when booting into Hardy the third or fourth time. The progress bar would move back and forth, and then all of a sudden just stop. When the progress bar stopped, so did the blinking HDD light on the front of the laptop. I thought this was weird, but I let it sit for a while. 10 minutes later, and still nothing. I thought it had frozen up during boot, but when I pressed a key on my keyboard, I saw the progress bar budge a little and the HDD light blink. When I pressed and held down another key, the drive spun up again and continued boot as usual. I rebooted just to make sure that this wasn't a random glitch, and it happened again. This also happened when test-running a few Windows games thru Wine in Intrepid. Both games froze up during load. They were loading fine, and all of a sudden the HDD light stopped blinking and they both became unresponsive. One responded a few times (slowly) to key presses, and the other became entirely unresponsive and had to be force-quit. 

I also noticed this issue when I was trying out a live-boot version of Intrepid from a flash drive a while back. I would be booting, the light on the flash drive would just go out. If I hit some keys, it would become responsive again and finish the load. 

This problem doesn't occur when running WinXP. 

I'm absolutely stumped at this point. I thought it may be because Ubuntu runs the drive a lot less than Windows and the firmware is enabling some sort of power management, but then why would the drive suddenly spin down right in the middle of loading something?

Any help is appreciated guys.

Thanks in advance

---

### Post by gianluca.pettinello on 2008-12-17
Tried
sudo hdparm -B 255 /dev/sda ?

Gianluca

---

### Post by Awfulwaffle on 2008-12-17
Alright, will do and I'll see if it fixes the problem. Also, I noticed a sister-laptop to mine was on a list of computers suffering from the load-unload cycle issue, and sure enough, mine is too. Currently I'm around 160-200 cycles an hour. Could this have anything to do with it?

---

### Post by Awfulwaffle on 2008-12-17
Just disable apm, and after reboot I got the same drive issue. The drive just randomly spun down during boot, and the progress bar froze until I hit a key.

---

### Post by Awfulwaffle on 2008-12-19
Bump

---

### Post by Awfulwaffle on 2009-01-30
Still nothing? This is the only thing that's keeping me from switching to ubuntu :(

---

