---
title: "HELP !!!: Ubuntu fails to boot after installing"
date: 2010-08-30
forum: Hardware
---

### Post by ckuru on 2010-08-30
Hi,

I installed Ubuntu netbook version on my HP netbook Mini 110 with Windows 7. After installing Ubuntu the first boot up failed. It hangs with a black screen with a flashing text-mode cursor. After several attempts (just rebooting) it worked. However, about 95% of the time the machine fails to boot - after 3-4 seconds, and without showing anything on the screen (text or graphical), it hangs with a black screen with a flashing text-mode cursor. Pressing Ctrl-Alt-F7 (or any other keys) has no effect.

I also tried booting in recovery mode from the Grub menu I get at start-up. It failed too. The last few lines I get in recovery mode looks like :

ata1: SATA max UDMA/133 abar m1024@0xfe(some numbers)

ata2: DUMMY

ata3: SATA max UDMA/133 abar m1024@0xfe(some numbers)

ata4: DUMMY

After this it get stuck there forever. Can someone help me out on this ? I'm a novice in this area. Any help is greatly appreciated.

Thanks.
CK
****

---

### Post by Fafler on 2010-08-31
Try booting and press ESC as soon as grub loads. That should give you a boot menu. Follow the instructions to edit the boot parameters, and remove the last two words, which should be "quiet splash" or similar. Boot and watch what happen. The last few lines should tell a bit about what went wrong.

Is the system stable when it does boot?

---

### Post by Rubi1200 on 2010-08-31
If you have the most recent version of Ubuntu, you need to use Shift during boot.

Also, what graphics card do you have installed?

If you get in go to the terminal and post the output of ```
lspci | grep VGA 
```

Hope this helps.

---

