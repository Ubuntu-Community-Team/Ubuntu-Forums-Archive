---
title: "kernel update problems..."
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by timmytron on 2007-05-30
first off, after the latest kernel update with my Ubuntu Studio 7.04 (fiesty), my swap partition became corrupt, and i had to reformat it. then i had to edit fstab to make it auto load on boot.

now, my suspend and hibernate features do not work... properly
i.e.: it appears to go into suspend, but when i try to "wake" the LEDs come on, but nothing else, the screen doesn't blink or anything :: when i try to hibernate, it does all the normal stuff, but as i turn back on, it just reboots.

i'm using a Sony VAIO PCG-5B5P laptop (slightly old school and from Sonyindia.com

any suggestions would be greatly appreciated, since there's no point in having a laptop that has to reboot any time it turns on...

---

### Post by Bredymer on 2007-05-31
Hi, I'm using a Sony Vaio VGN-S90S and I also had alot of problems with hibernate after I updated to the newest kernel.

It turns out that I had installed the "hibernate 1.94-2" community supported module. This fixed my original suspen/sleep problems on the old kernel. After removing these it appears that I can safely sleep/hibernate again.

Now, if I could only get my Wifi working....

---

