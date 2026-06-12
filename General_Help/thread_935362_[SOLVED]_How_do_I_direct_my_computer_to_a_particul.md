---
title: "[SOLVED] How do I direct my computer to a particular menu.lst???"
date: 2008-10-01
forum: General Help
---

### Post by bcn17 on 2008-10-01
I have a dual boot set up with windows and hardy- On another partition that was /partition2 I installed alpha kubuntu 8.10

My computer now uses the new /boot/grub/menu.lst found on the 8.10 partition- I was going to reformat the 8.10 partition back to an empty ext3 because the alpha is really buggy- (i just wanted to take a look) but I got to thinking that may not be such a good idea- How will my computer boot into grub? Where can I go to let my computers initial boot sequence know that it needs to look at my 8.04 menu.lst (on sda2) and not the 8.10 (sda4)? If i just delete sda4 I figure my computer might hiccup at me. 
Thanks-

---

### Post by sisco311 on 2008-10-01
open a terminal and type:
```
sudo grub
```
then in the grub prompt:
```
root (hd0,1)
setup (hd0)
quit

```
reboot the computer.

---

### Post by bcn17 on 2008-10-01
This worked perfect- Thank you very much. Before I did it though I checked my 8.04 menu.lst and made sure it was (hd0,1) and not (hd0,0) or something. However it was (hd0,1). I'm assuming this was because I told you I had windows so you knew that as long as windows was installed first that windows was (hd0,0) and 8.04 was (hd0,1)? Or is their some other element to your logic? Anyway, this is SOLVED. :)

---

### Post by sisco311 on 2008-10-02
the first partition on the first disk is
sda1 = hd0,0
the second partition is
sda2 = hd0,1
...

sdb1 = hd1,0
sdb2 = hd1,1

etc...

---

