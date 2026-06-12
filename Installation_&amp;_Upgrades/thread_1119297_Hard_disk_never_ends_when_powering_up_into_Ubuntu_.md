---
title: "Hard disk never ends when powering up into Ubuntu after updated halted by power off."
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by gtccswsv on 2009-04-07
I was updating my laptop from 8.10 to 9.04beta, when I was receiving a long time phone call, my laptop battery drained, and, when I power it up into Ubuntu, no X window, the light for hard disk flashed all the way, so I went to sleep, when I was up the morning, the light is still flasing without any display in screen...

What can I do?

---

### Post by 123456789123456789123456 on 2009-04-07
sounds like it may be hardware related.  Let me get all the information I can.  you said that no window appears, does the screen light up, is anything displayed.  The bios inforamtion for instance.  If so, does GRUB come up, with grub stage 1.5
boot from hd0, so on.

You say that the hard drive light flashes, signifing that it is reading the disk.  Do you hear any sounds from the disk?

Try booting from live cd.
after boot, does the live cd reconize the hard disk

If I had a little more information I could help trace the problem for you.

---

### Post by gtccswsv on 2009-04-08
Thanks for the help,, the ubuntu screen light up, until the progress bar entered its end. The screen flashed several times when GNOME should appear, nothing is displayed, even without terminal screen after pressing ALT+F1, CTRL+ALT+DEL also desn't work. The Kernel displayed in GRUB is still that of 8.10, any kernel/option there will lead to the same black screen. 

The hard disk is running with the black screen there...

I can mount the hard disk for Ubuntu after booting from live CD.

---

### Post by gtccswsv on 2009-04-08
I cannot wait and installed Fedora and Ubuntu on the disks...

So this issue should have an end. 

Thanks go to 123456789123456789123456 for his/her help.

---

