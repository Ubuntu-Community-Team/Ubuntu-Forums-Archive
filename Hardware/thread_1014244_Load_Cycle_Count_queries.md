---
title: "Load_Cycle_Count queries"
date: 2008-12-17
forum: Hardware
---

### Post by Nico-dk on 2008-12-17
Seems like the [original topic](http://ubuntuforums.org/showthread.php?t=805570) is dead, or at least is rarely visited.

I have a few questions regarding the "Ugly Fix".

**1)**
Shouldn't this start up with the system?

Mine doesn't. My LCC increases until I type this in the terminal
```
pm-powersave false
```
Echo```

**disabled pm for harddisk
**SetLowPower OFF
**sched policy powersave OFF
```
After that LCC increments by 1 every 90 minute or so, and my HDD temp goes no higher than 45 degrees C. Yay.

**2)**
This
```
hdparm -I /dev/sda | grep 'Advanced Power'
```
always returns a * (it doesn't matter if I set powersave to true or false.
Shouldn't this only show when the fix is running?

**3)**
If this isn't supposed to start with the system, how can I ensure it does?
I was thinking something like running a little script that would run the powersave command w/o actually opening the terminal.

**4)**
Someone in the original post said he experienced significantly lower LCCs when playing music. Probably because the HDD is constantly accessed, wouldn't a smarter fix be a small script constantly accessing a file, something simple that runs in the background and writes to a file every 10 seconds, and then deltes the entry every other 10 seconds, of course saving after each action?
This would emulate Win disk access, and shouldn't take any noticable toll on the system.

  ------
 
For reference to questions 1 and 2:
I started my LCC adventure by finding my LCC and measuring incrementation rate. Then setting my apm like this
```
sudo hdparm -B 254 /dev/sda
```

Today I followed [this guide](http://en.opensuse.org/Disk_Power_Management), everything went smoothly, except for the oddities mentioned above.

Sorry for the long einded post, any feedback will be greatly appreciated.

---

### Post by Nico-dk on 2008-12-18
So, any thoughts??

---

### Post by Nico-dk on 2008-12-18
Guess not

---

