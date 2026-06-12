---
title: "i have a problem when setting up a dual boot"
date: 2008-09-06
forum: General Help
---

### Post by washable mist on 2008-09-06
well this is going to be my second machine that i will use to dual boot Ubuntu and windows xp, first time i did this it went without a problem but this time i have found a problem from the start.

using a online guide on how to dual boot the two operating systems on "http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm"

i open tirminal an type in sudo gedit /boot/grub/menu.1st to make a backup of grub bootloader, but when i open the file it is empty, there is nothing written in there what so ever.

can anyone help me with this and maybe tell me if i'm doing something wrong

---

### Post by pbotros1234 on 2008-09-06
Its /boot/grub/menu.lst, not menu.1st :)

---

### Post by G-Dub on 2008-09-06
not quite sure what you did wrong... but i always found it easier to install windows first, then linux. This video is a pretty good tutorial: [http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by washable mist on 2008-09-06
> **pbotros1234 said:**
> Its /boot/grub/menu.lst, not menu.1st :)

"bangs head on table"

thank you very much it works now

---

### Post by cybrsaylr on 2008-09-06
> **G-Dub said:**
> not quite sure what you did wrong... but i always found it easier to install windows first, then linux. This video is a pretty good tutorial: [http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

Nice tutorial.
It gives out some useful info for those wondering about linux.
When I dual booted all I used was the instructions on the Live CD which can be confusing if you never used linux before.

---

### Post by cybrsaylr on 2008-09-06
Came across this tutorial which is pretty nice and more in line with what I did installing my dual boot systems:
[http://video.google.com/videoplay?docid=-2369893842637434537&hl=en](http://video.google.com/videoplay?docid=-2369893842637434537&hl=en)

---

