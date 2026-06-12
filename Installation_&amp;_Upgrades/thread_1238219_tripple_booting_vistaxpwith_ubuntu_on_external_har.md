---
title: "tripple booting vista/xp/with ubuntu on external harddrive"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by newbuntu9.04 on 2009-08-12
i just managed to install ubuntu on my external ubs harddrive and my asus laptop wich is dualbooted with vista/xp is reading it .i can boot into ubuntu fine and i can boot into vista/ xp through the bootloader i saved when installing ubuntu but the way it is setup if i unplug ubuntu from the usb i cant load into nothing. i would like vista /xp to be my main os because they are on my internal drive. i dont plan on plugging ubuntu up to another computer so having the bootloader on the externaldrive  dosnt matter. im wondering if there is a way to put the bootloader on vista to decect ubuntu when it is plugged up because right now ubuntu is my main bootloader then i have to click on vista bootloader then it takes me to vista/xp load screen .  i have tried easy bcd beta2.0 but wasnt successful
im sorry if im not making sense i have only got like 2 hours experience with ubuntu but looking forward to getting the kinks worked out.
 if im not providing enough or not the right info just let me know and i will try to be more accurate any advise would be appreciated  thankyou
](*,)

---

### Post by Mark Phelps on 2009-08-12
It's not clear what the problem is now.  First, you say you can't boot into nothing, implying that you can't boot at all.  Then, you say that you installed easyBCD, implying that you CAN boot into your MS Windows OSs.

So, I'm going to guess that what you did was install GRUB to the MBR of your internal drive such that when you boot now, it looks for the menu.lst file on your external drive -- and not finding that, you get a blinking cursor or the word "GRUB" but nothing else. Right?

When you installed EasyBCD, did you first repair your internal drive MBR so that you could boot directly into MS Windows again?  I'm guessing you didn't, and if you do that, it's very likely that EasyBCD WILL then work.

---

