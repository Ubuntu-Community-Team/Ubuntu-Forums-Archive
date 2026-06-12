---
title: "Might as well do a clean install"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by xtalgrwr on 2009-02-12
Hello,
I'm a newbie. I made a few mistakes and long story short might as well do a clean install. No problem. I downloaded the UBCD and the System Rescue CD but I haven't found my way to solving it.
Seagates SW comes with windows options only!?! fdisk wants to do a FAT format.
I would like to reformat to a linux format and install ubuntu and forget windows XP. It was corrupted and I don't have the distro CD. So might as well leave it just linux.
I bought linux magazine with the DVD but the articles don't cover detail of my royal mess ups.
It ran beautifully from the live CD.
Any good ideas where I can download the right s/w to reformat to linux? I want the whole drive for linux 160MB.

---

### Post by Fenris_rising on 2009-02-12
Hi there

If your using a live CD then you should find, when its up and running, an install icon on the desktop. Once you start the process you will answer a series of questions and along the way you will see a page to do with formatting and partition sizing. You should see a 'use the entire drive' option. hope that helps.

regards

Fenris

---

### Post by xtalgrwr on 2009-02-12
Fenris,

Thank you for that quick reply. 

And, yes I got that right the last time. And so I am all happy and giddy and reboot and it comes back with no OS?! 

It is in there but probably not in the right spot. I got it to boot with the system rescue CD but it won't do it all on its own.

Maybe grub? MBR? I'm not sure anymore. That is why I thought of just doing it all clean again.

Thnx.

---

### Post by Gramps on 2009-02-12
Might be some problem with the CD that was with the magazine. Try downloading this iso image and burn it to a Cd then try doing a fresh install again and see what the results are.

Download URL:[ http://www.gtlib.gatech.edu/pub/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso]( http://www.gtlib.gatech.edu/pub/ubuntu-releases/intrepid/ubuntu-8.10-desktop-i386.iso)
Ubuntu Edition: Ubuntu 8.10 desktop
Computer Platform: i386

This will download the latest stable version

Hope this helps

---

### Post by xtalgrwr on 2009-02-12
Gramps,

Thnx for that input. I'll do that. This CD has a self checker.
And I ran it. It took a while but reported no errors.

Let me down load that meanwhile.

Thnx.

---

### Post by xtalgrwr on 2009-02-12
Gramps,
I did as you suggested. Downloaded, burned, installed.
8.10 has a lot better graphic in the guided all drive setup page.
But when i rebooted it came up with missing boot.
I used the rescuecd told it to boot from disk1. That invoked grub and it booted. I guess I'm very close but still missing
a smidging.
Thank you.

---

### Post by Gramps on 2009-02-12
During the install when you got to the partition the HD part did you choose the "Guided use entire disk" option. This would not have been the default choice.

---

### Post by xtalgrwr on 2009-02-12
Gramps,

That's correct. I did that.

---

### Post by Gramps on 2009-02-12
Might want to post the error message that you get when you try to boot up.

This might help too.  [http://ubuntuforums.org/showthread.php?t=1030911](http://ubuntuforums.org/showthread.php?t=1030911)

---

### Post by xtalgrwr on 2009-02-13
Gramps,

Hi. The diag says:

"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

Seems like a DOS diag with all capitalized text.

Many thanks.

---

### Post by xtalgrwr on 2009-02-13
Gramps,

That link you sent me with the last answer seems to have done it.

I can't believe I so stupid! I forgot to change over the BIOS settings. Its booting right now.

Many thanks for you patience and support.

---

### Post by Gramps on 2009-02-13
I had this happen when the HD which I had installed Ubuntu had it's jumper set to master when in fact it was the only HD on the IDE chain. Moved the jumper to single and the system when then dual boot as it was suppose to. So check your the jumper on your HD.

---

