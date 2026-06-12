---
title: "Acer Aspire One displays garbage"
date: 2018-03-03
forum: Hardware
---

### Post by francois-laverdure on 2018-03-03
Hi!
I have been running both Ubuntu and Lubuntu on my old (I should say venerable) Acer Aspire One 150 ZG5 without any issue until today.
I just put in a bunch of updates and am having a big problem with the display.
The display shows on ¾ of the screen some gibberish with only the right side showing something reasonable.
I tried booting in safe mode and that seems to fix the problem but it gives me terrible resolution.
I also tried booting using the Linux 4.10.0-42 core that grub offers me and to my surprise that fixes the problem...

So, what can I do to run the latest version of the Linux core and still be able to actually see something?

The computer is an Acer Aspire One 150 ZG5 with 1.5GB of ram. The video card is an Intel GMA945GMS.
I'm running Lubuntu 16.04.2 LTS.
The problematic core seems to be version 4.13.0-36 Generic.
The one that works is 4.10.0-42 Generic
Here is what the screen looks like (sorry but I couldn't do a good screen dump)
[ATTACH=CONFIG]278779[/ATTACH]

---

### Post by mörgæs on 2018-03-04
Hi, welcome to the fora.

Does this help?
[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

---

### Post by francois-laverdure on 2018-03-04
Thanks for pointing me in the right direction!
I just followed a few links and found this solution that works fine for now.

go to etc/default
edit the grub file (make sure you are calling sudo)
add the following line GRUB_GFXPAYLOAD_LINUX=text
save the file
type sudo update-grub
wait for it and reboot.

While the results are not as nice, it seems like it fixes the bug enough to make the computer useful.
Now don't ask me why it works, it just does...
I just hope the next update/upgrade won't screw this up once again...

And now, I can once more play my games using RetroPie :p

Thanks again!

---

### Post by mörgæs on 2018-03-05
Good, please mark the thread 'solved'.

---

