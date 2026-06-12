---
title: "Hibernation stopped working"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by michux on 2005-05-29
Hello. I've go a problem with hibernation on my HP Pavilion dv1074ea laptop. It worked great just after installation, but stopped working after I installed another system on the machine (Mandriva 2005 LE) on another partition. 

It seems like Mandriva took away Ubuntu's SWAP partition (I had no swap activated when I booted to Ubuntu). So I tried do do swapon -a - it failed. So I formatted the swap partition using mkswap /dev/hda7.
Now Ubuntu can see the SWAP and apparently activates it on bootup. Still, hibernation does not work.

The case looks like this:
- I select "Hibernate this computer" option from the menu
- The computer does the usual things and turns off after some 1 minute
- When I start the computer again, it thinks a bit, but then goes to the usual bootup procedure instead of wake up freom the hibernation state. Errors on my reiserfs partition are found and repaired and a usual gdm screen appears.

What can be the cause of this? I checked the grub settings - they seem very similar to the default ones, just the upgraded kernel replaced the standard one. Maybe the kernel is the cause? But still, when I try to boot the old kernel and hibernate, it does the same thing...

Any thoughts? I'd be more than grateful for advices...

---

### Post by michux on 2005-06-03
Still haven't resolved it... still waiting for some ideas, maybe?...

---

### Post by michux on 2005-06-11
Ok... some more details... maybe that will help.

I noticed that after I put the notebook to hibernation state (seems to work fine),
the system starts up (no waking up rom hibernation, reiserfs replacing nodes...)
WITHOUT the SWAP partition activated.
Even if I do swapon -a, it doesn't work! It starts working only if I reformat the swap partition. What the heck?

Any thought on what can be causing this problem?

---

### Post by jshein on 2005-06-11
Same experience here using kubuntu. Searching for a solution.....

---

### Post by jshein on 2005-06-11
It seems sometime in the last few updates I lost reference to my swap partition in the /boot/grub/menu.1st file.

For my system, with the root partition on /dev/hda3 and swap on /dev/hda2 edit the line

#kopt=root=/dev/hda3 ro

change to

#kopt=root=/dev/hda3 resume=/dev/hda2 ro

Subtitute your proper partitions.

If you suspend, and the system cannot find the swap partition where you resumed to, it can not enable the swap partition stated in /etc/fstab

then do

#sudo update grub

All fixed

---

### Post by michux on 2005-06-13
Thanks. It helped!

I invoked 
```
update-grub
```
and it screwed up my grub settings, but after repairing (reenter the resume partition and vga mode) the system can hibernate again!

Great.

---

