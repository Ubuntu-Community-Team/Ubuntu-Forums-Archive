---
title: "Acer Aspire One (AO751h) freezes at startup (UNE 10.04)"
date: 2010-08-31
forum: Hardware
---

### Post by pirx82 on 2010-08-31
Hi everyone,

I've installed Ubuntu Netbook Edition 10.04.1 on my Acer Aspire One (AO751h) and after updates, I have two different kernels to choose from:

**Ubuntu, with Linux 2.6.32-24-gerenic**
This was available right after installation. If I select this option, the HDD makes a noise for a second and then everything stalls. I'm left with a blinking "cursor" on the LCD monitor and AFAIK, the system is frozen.
[B]
Ubuntu, with Linux 2.6.32-24-gerenic (recovery mode)[/B]
This option sometimes runs the machine, but it freezes at a random line, but 90% of the time it freezes at this line:

[ 1.253353] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[ 1.253356] ata2: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 15

If I get lucky, I can sometimes get to the "**Recovery Menu**". I can choose there "**resume normal startup**" and sometimes it gets me to the GUI. From time to time I also choose the "**resume with fail safe graphic mode**" option, but then I have to login myself through the console and use the "startx" command.
[B]
Ubuntu, with Linux 2.6.32-21-gerenic[/B]
This option got available after applying all of the available updates. Most of the time (8 out of 10) it does the same as the .32-24-generic. But if it gets through the first few critical seconds, it always gets me to the normal GUI.

**Ubuntu, with Linux 2.6.32-21-gerenic** **(recovery mode)**
It acts the same as the .32-24-generic (recovery)

***

Because this machine features a GMA500 chipset, I needed to install the "Poulsbo" update ([https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)). 

I've got the latest BIOS update too and I don't think it's a hardware issue. I'm dual booting the machine with licensed Win 7 Ultimate and it works normally (it never freezes at boot and it never freezes while working).

I would be very grateful for any kind of help with diagnosing the issue. I love Ubuntu Netbook Edition, because it's 10 times faster as Win 7 and it makes my netbook actually usable again (when it works). :)

---

### Post by al3ssandr000 on 2010-09-01
i've the same problem with the same Acer netbook....
PLEASE HELP US!!!! :(

Thank you.

---

### Post by al3ssandr000 on 2010-09-01
Hey... anyone can help us?

---

### Post by al3ssandr000 on 2010-09-01
I think i've SOLVED the problem!
The problem is related to the B43 wireless card drivers... it seems they don't work with this netbook, causing freeze at startup.
I've selected other drivers automatically proposed by Ubuntu (STA drivers) and the problem is solved.

I hope will be the same for you Pirx82.
Tell me if you'll solve too.

Bye.

---

### Post by pirx82 on 2010-09-02
> **al3ssandr000 said:**
> I think i've SOLVED the problem!
The problem is related to the B43 wireless card drivers... it seems they don't work with this netbook, causing freeze at startup.
I've selected other drivers automatically proposed by Ubuntu (STA drivers) and the problem is solved.

I hope will be the same for you Pirx82.
Tell me if you'll solve too.

Bye.

Hey, al3ssandr000! 

Thanks for joining in. :) I already thought I'm the only one with this problem since I didn't find any related posts to this one.

I've tried your suggestion and I hope this will solve the problem for good! Today, even before reading this post, I managed to get it up and running either with the older or the newer kernel. If the first one did not want to work, I've selected the second and vice versa.

Anyway, thank you very much for sharing your experience and I well get back to you in a few days, just to acknowledge, if everything is OK!

---

### Post by pirx82 on 2010-09-05
> **al3ssandr000 said:**
> I think i've SOLVED the problem!
The problem is related to the B43 wireless card drivers... it seems they don't work with this netbook, causing freeze at startup.
I've selected other drivers automatically proposed by Ubuntu (STA drivers) and the problem is solved.

I hope will be the same for you Pirx82.
Tell me if you'll solve too.

Bye.

Hi again, al3ssandr000!

What you have suggested, definitely works!!! =) Thank you so much. I'm going to mark this thread as SOLVED.

Thanks again and have fun using Ubuntu on your netbook! :)

Best regards.

---

