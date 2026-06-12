---
title: "Intel graphics puzzle, 11.04"
date: 2011-05-28
forum: Hardware
---

### Post by rokob on 2011-05-28
I have a Lenovo L420. I was having issues with the graphics under 10.04 so I upgraded to 11.04. The graphics problem persisted. I edited the /etc/default/grub file and removed the i915.modeset=0 part. I then restart the machine and get a screen with alternating black and white vertical bars. There is nothing I can do from this screen.

If I then however hit Fn+F4 which makes the computer suspend, then hit Fn+F4 again to make the computer wake up, the login screen shows up and everything works perfectly. Prior to editing the grub file, the video card was not really recognised as I was in safe mode graphics with only one resolution. I now get full graphics and all available resolutions for my graphics card.

I am not entirely opposed to suspending and waking up my computer each time I start it, but it would be great to get a better solution.


$ uname -a
Linux betty 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

$ lspci -knn
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Lenovo Device [17aa:21dd]
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by rokob on 2011-06-09
Anyone out there know anything about this? Maybe where to beginning looking or what this could possibly be?

---

### Post by belltown on 2011-06-09
Did you type:

```
sudo update-grub
``` after editing /etc/default/grub ?

---

### Post by rokob on 2011-06-10
Yes, after doing so the first time, I restarted the machine and saw the vertical bars. I thought I had screwed everything up. So I started hitting different key combinations and the hibernate one just happened to do the trick.

---

### Post by DecoYserbia on 2011-06-17
I had the same issue till 3 minutes ago. This helped me to solve the problem


Applications->Accessories->Terminal: sudo gedit /etc/default/grub 
add this line into the end and save the file: GRUB_GFXPAYLOAD_LINUX=1024x768x32 here change 1024×768x32 to what you want.

In my case it was GRUB_GFXPAYLOAD_LINUX=1366x768x32


Hope this will help you ;)

---

### Post by rokob on 2011-06-24
I just saw your post, edited the grub file, and it worked perfectly!

Thank you so much for solving this, it has been quite frustrating.

---

### Post by mista_freeze on 2011-10-07
> **DecoYserbia said:**
> 
...
sudo gedit /etc/default/grub 
add this line into the end and save the file: GRUB_GFXPAYLOAD_LINUX=1024x768x32 here change 1024×768x32 to what you want.

In my case it was GRUB_GFXPAYLOAD_LINUX=1366x768x32


Hope this will help you ;)

Just installed ubuntu 11.04 (64 bit) on L420 with i3-2310M CPU and had the same problem as described above. The suggested change fixed it. Thanks a lot!

---

