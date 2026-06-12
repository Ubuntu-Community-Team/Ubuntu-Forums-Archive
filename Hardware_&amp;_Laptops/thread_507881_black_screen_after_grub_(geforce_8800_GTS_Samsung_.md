---
title: "black screen after grub (geforce 8800 GTS Samsung SyncMaster)"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by whoop on 2007-07-23
I had a compu with a Geforce 8800 GTS and an old dell 992 monitor and this setup used to work fine.... After grub the screen would turn black (no splash with progress bar) and then the screen would apear with the login screen. I thought it was a little weird that the screen would turn black for a period but this was not really a big issue.

Now i replaced my old monitor with a Samsung SyncMaster 226BW. And after grub it goes black and it stays black. I ran the livecd to check if it worked from there... same problem.... it goes black and stays black. I checked a livecd of Mandriva and there was no problem. 

I also ran the recovery mode from the grub list and after I got a prompt i typed startx.... X did start, so i reckon it could and should work.

hope someone can help me... cheers.

---

### Post by Circuit99 on 2007-07-24
What you need to do reconfigure your xorg.conf info found here 


[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

If your still stuck post your xorg.conf .

Use Ctrl+Alt+F1 to enter terminal mode after black screen appears. :lolflag:

---

### Post by mont on 2007-07-27
I have the same gfx and a Samsung 226BW too actually:)

Did you find a solution how to get the splash after grub loaded working?
Only way for me not to get a black screen was to disable splash in the grub config.

There must be a workaround to get the splash working, a resolution problem maybe?

---

### Post by whoop on 2007-09-03
resolved the issue:
added vga=0x318 to the kernel line in menu.lst.

No more black screen.

cheers

---

