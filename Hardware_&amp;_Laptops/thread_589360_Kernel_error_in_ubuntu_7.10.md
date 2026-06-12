---
title: "Kernel error in ubuntu 7.10"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Cameron88 on 2007-10-24
Ok first off i am new so Im not for sure if this is the right place to discuss my error Im getting on start up.
I installed ubuntu 7.10 desktop on my compaq presario v5000 series laptop. Well first tried it out on live cd before i booted it up but for one little error i dident really pay any attention to it because it was my first try with ubuntu. Everthing seemed to work out fine after the error went away got the ubuntu logo with the orange bar loading then got into the desktop. Tested around with it and everthing seemed to work out great just had to install restricted drivers for the laptop for the ati card and the firmware for the wireless. So i installed it finished with no errors when i rested the laptop to boot into ubuntu I got the same error posted below. When that went away i dident get the ubuntu logo with the orange bar telling me its loading up all i got was an black screen. Then my laptops fan started to   speed up faster and getting hot. I let it waite awhile till i was able to get into the log in screen. I at least waited 2 minutes to get into the log in screen to.                              

Here is the error:
PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0

PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0

My system Specs:
Amd Turion 64 Ml-32
1.5gb of ram
Ati radeon xpress 200m
BCM4318 [AirForce One 54g] 802.11g built in wlan

Not being an linux expert but i belive the error is coming from the ati card or the broadcom wlan.
Hopefully if someone can figure this out for me because i hate wating 2 minutes to use my laptop:(.  Also i forgot to mention that once im able to get into the desktop everthing works the wireless and the ati card.

---

### Post by jpmontalbo on 2007-10-24
Try this and let me know if it works. When you first boot up your laptop it will ask you to press ESC to access grub. 

1. Press esc and the grub menu should open up.

2. select the first line, not the one that says recovery mode and press "e" which will open the line up for editing.

3. go to the very end of the line and enter this text in:

   noapic irqpoll irqdebug

4. once completed hit enter to accept, and press "b" to boot while the line you edited is highlighted.

Let me know how it goes. Cheers.

---

### Post by Cameron88 on 2007-10-24
Ok i did what you said but dident work still got the long boot process of 2 mins. Being noob as i am with linux just check me if i did what you said correctly

Restarted the pc hold down the esc got into the grub menu choosed the first one hit the e button
Got an list with the following order Root Kernel initrd quiet so i hit the o button to add an new line hit the e button to edit the new line added the noapic irqpoll irqdebug hit enter it was on the bottom of the list now after quiet. Was also highlighted and hit the b for boot.

Any other ways to fix this problem?

---

### Post by jpmontalbo on 2007-10-27
> **Cameron88 said:**
> Ok i did what you said but dident work still got the long boot process of 2 mins. Being noob as i am with linux just check me if i did what you said correctly

Restarted the pc hold down the esc got into the grub menu choosed the first one hit the e button
Got an list with the following order Root Kernel initrd quiet so i hit the o button to add an new line hit the e button to edit the new line added the noapic irqpoll irqdebug hit enter it was on the bottom of the list now after quiet. Was also highlighted and hit the b for boot.

Any other ways to fix this problem?

sorry for the delayed response, but when you get to the part where a list is displayed, go to the line that says kernel not root. I'm sorry I didn't specify.

Also, you may want to check out this thread [http://ubuntuforums.org/showthread.php?t=579568](http://ubuntuforums.org/showthread.php?t=579568)

I think you aren't the only one having this issue. Good luck!

---

