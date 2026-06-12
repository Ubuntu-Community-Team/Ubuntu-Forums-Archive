---
title: "Intrepid on Inspiron 1420;  Yet Another Brightness Post"
date: 2008-11-27
forum: Hardware
---

### Post by rpglover64 on 2008-11-27
I know there have been a lot of posts on how to fix brightness.  They worked for me in Hardy, but I decided to upgrade to Intrepid after installing it on a friend's computer.

The problem:  the brightness keys cause my brightness to go from not so bright to very bright (or vice versa, depending on which key) without steps in between, and with some stuttering.

I tried blacklisting video, but it made a mess of things:  the increments were too fine, and after I pressed a brightness change key, it would gradually go to that brightness extreme; I also couldn't open menus.

I played around with /etc/acpi/video_brightnessup.sh and /etc/acpi/video_brightnessdown.sh, but it didn't work.  I noticed that when I pressed the brightness key (Fn+up or Fn+down) it seemed like 2 or 3 things were trying to adjust my brightness at once.  I also noticed that just running the scripts or just running "sudo acpi_fakekey 224" (225 for brightness up) did the right thing.

I deleted the scripts (kept a backup, of course) and restarted my computer.  As far as I know, this means that my brightness keys should do nothing.  Unfortunately, the brightness keys still "work".  This leads me to wonder what else could be receiving their keypresses.

As a final note, until I log in, my brightness keys seem to work fine.

Thanks for any help in advance.

---

### Post by joel_gil on 2009-01-11
same here 
im on a inspiron 6400
blacklist video did the trick since 2 realeases ago i dont know hwat has changed since then
hope someone has the solution soon

---

### Post by almikul on 2009-01-15
I had the same problem on Gateway MT6705 for as long as I had Intrepid: the laptop would not suspend/hibernate and the brightness keys would occasionally not work. However, today I did the update **acpi-support_0.114-0intrepid1**, and it fixed all my ACPI problems! Now, the laptop suspends and hibernates without problem, the brightness keys work, and the network card is functioning properly upon the wake up. I thought this day would never come :)

---

