---
title: "Partion problem..Deleted Ubuntu partion and now GRUB won't work on ThinkPad t60"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by spootmonkey on 2007-07-28
Hello,
I recently needed more room on my HD, so I deleted the partion that held Ubuntu. Everything was fine (I use Vista btw) until I restarted my computer. I forgot that I use GRUB to Multiboot Vista and Ubuntu, and now that the Ubuntu partion is gone, GRUB doesn't work, it just give an error 17. Is there anyway I get replace GRUB with a different bootloader using a Live CD. I can't get onto my laptop at all since I can't reach my Vista Partion. All I get is the GRUB error message as its trying to load.
I feel really dumb for not even thinking about this. I hope someone can give me some advice that I can take, or point me in the right direction. 
Thanks for your time!!!

---

### Post by logos34 on 2007-07-28
grub needed the config files (i.e.menu.lst) in /boot/grub dir...you deleted all that when you wiped ubuntu.  Reinstall vista bootloader using the vista install dvd.

---

### Post by spootmonkey on 2007-07-28
I'm sorry if this is out of the scope of this fourm, but I don't have my Vista DVD, I got it from my school. Is there anyway I can put in ubuntu again..or get the vista bootloader with the dvd? 
Thanks for you help!!!

---

### Post by logos34 on 2007-07-28
ok, then just reinstall ubuntu on a minimum size partition (you say you need room).  That'll solve the problem.  

Idea: if you just need to be able to boot into vista, you could even specify during ubuntu reinstall to make a separate ~50 MB /boot right after vista partition.  After install is complete boot into vista and format root and swap, leaving just the /boot.  But can't you spare a few gigs for Ubuntu? it's such a great little OS!

---

### Post by motoperpetuo on 2007-08-11
For what it's worth, I had a similar problem with my Gateway Solo 1450. I deleted my Ubuntu partition (couldn't get xwindows to work, but that's another story). After that, I got the same "error 17" when GRUB would load and couldn't boot into windows XP.

Anyway, after some playing around, I figured out how to get rid of GRUB and restore the XP Master Boot Record:

1) Boot to the Windows XP install CD.
2) When the Windows install finishes loading, choose 'R' to go to Recovery Console.
3) Login to your Windows partition.
4) Type the following at the command prompt:

fixmbr

5) Reboot.

That should do it. I know the original poster asked about Vista, not XP, but I thought this might help some people (like me) who might be looking for a solution to this particular problem. Plus, it's likely a similar solution in Vista.

---

