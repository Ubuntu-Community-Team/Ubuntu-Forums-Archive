---
title: "access BIOS after 16.04 install - GB MOBO GA-F2A78M-HD2 rev 3.1"
date: 2016-07-15
forum: Hardware
---

### Post by i-like-linux-83 on 2016-07-15
I was fiddling around in my BIOS to try and install Ubuntu 16.04 and finally managed it but now I can't get into my BIOS.

The motherboard is as it says in the post title, I have tried a full power cycle but still have no luck, I have also tried pressing the appropriate keys over and over at boot up (which worked pre-16.04 install), the options don't appear on the screen at boot up.

Do I need to re-flash my BIOS? if so, how?

Many Thanks.

---

### Post by oldfred on 2016-07-16
Probably UEFI fast boot setting is on. (different than Windows fast start up setting).
UEFI fast boot assumes system has no changes and immediately jumps to booting system. Usually do not have time to press keys to get into UEFI or one time boot key.
Often cold boot, full power down, remove battery if laptop, hold power switch for 10 sec or so should then force UEFI to do the old normal hardware checks which still is faster than old BIOS systems, but gives you a very few seconds to press correct key to into UEFI.

But both Windows & grub have ways to reset boot  to get into UEFI.
With grub it is the last menu setting "System Setup":
```

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```

---

### Post by i-like-linux-83 on 2016-07-16
I can get GRUB up with a cold boot and power cycle but there are only 4 options and 'System Setup' is not one of them, 1. is boot ubuntu 2. is advanced settings 3. is mem test and 4 is mem test (x86)

Not only this but my keyboard is power dead at GRUB - I think I disabled USB devices at boot (stupid I know) but not sure if this affects GRUB or if it's something else, keyboard works fine once at login screen. 

Thank you for your kindness.

---

### Post by oldfred on 2016-07-16
Grub also used to use the BIOS/UEFI driver as no system drivers have been loaded yet. 
So you probably do have to enable USB ports in UEFI.

---

### Post by Yellow Pasque on 2016-07-16
Once you are at the GRUB screen, the system has already booted from a disk and it is too late to get in your EFI/BIOS/System Setup. Did you try the 10 second hold down as suggested? Have you tried to read your mobo manual?

---

### Post by i-like-linux-83 on 2016-07-22
It is a desktop machine and yes I did try that even though oldfred specifically said for laptop, I have now tried :

pressing delete key repeatedly at boot to get into BIOS even though the screen does NOT flash up with the option to do that like it used to.

using boot repair from within UBUNTU which went horribly wrong and now I can't even get into UBUNTU - I had to use the 'nomodeset' option when I installed ubuntu and I'm pretty sure it's the same problem again except this time I can't think of or find a work-around

looking in my MOBO user manual for anything relating to the BIOS but besides setup once in the settings the only other thing is removing the battery from the motherboard and waiting for 1 minute before re-connecting and powering back on - which I have done and still face the same problem

tried 4 different keyboards all from different manufacturers in different USB ports/hubs to get into the BIOS but they are all the same - no power until after GRUB and just before the monitor goes to sleep.

ughf what on earth can I do? would a new HDD be the answer?

---

### Post by oldfred on 2016-07-22
Once you get to purple screen Ubuntu you are long past UEFI/BIOS.
You have to immediately press del, f2 or f12 or whatever is correct key for your system as soon as you turn on power. 

If not laptop normally full power down, unplug system & hold power switch for 10 sec or so resets to defaults. But removing battery on motherboard will reset UEFI/BIOS to vendor defaults. With my systems I have had to make several setting changes in UEFI.

Last night I had power failure (could not understand why system was not working), and the Gigabyte logo immediately came up.

---

### Post by i-like-linux-83 on 2016-07-23
I had tried that many times but it was just not working, the Gigabyte logo and options at the bottom just wern't there like they used to be, however, I did some poking on youtube and found this : [https://www.youtube.com/watch?v=-9RnIj-EcdQ](https://www.youtube.com/watch?v=-9RnIj-EcdQ)

So, I had another look in my MOBO manual and sure enough the 2 'clear cmos' pins were there, WITH THE MACHINE UNPLUGGED AND POWERED OFF I held a flathead screwdriver (metal object) to the two pins (as explained in the manual) for about 15 or 20 seconds till I heard a very quiet 'click', put the side panel back on, plugged it all back in and sure enough when I powered back on I was immediately greeted with 'bios has been reset' with 3 options for continuing and was able to re-install windows. Problem Solved :)

I appreciate your kindness in helping, both of you :)

p.s how can I mark this as solved? can't seem to see the option anywhere

---

### Post by oldfred on 2016-07-23
Thread tools at top of first post.
 Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

