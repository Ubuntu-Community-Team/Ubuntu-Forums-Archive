---
title: "Ubuntu gone after re-installing xp"
date: 2008-08-27
forum: General Help
---

### Post by yaaman on 2008-08-27
I am new here. I have a Gateway laptop 4530GZ (bought four years ago) and it has 60Gb hard drive. My friend last year installed Ubuntu. He partioned the hard drive. 20Gb for Ubuntu and 40Gb for windows XP. Two days ago I had a lot of virus on my XP. It was so bad that I had to re-install xp using the recovery CD. I used the destructive option in the recovery process to get rid of the viruses. After re-installing XP, when I start my laptop I don't see the bootloader anymore allowing me to switch to Ubuntu. But when I go under my computer on XP is says the total hard drive size is 40GB. **My question is how do I get back Ubuntu?** Did ubuntu get deleted? Do I have to re-install Ubuntu?

Thanks,
-yaaman

P.s. Keep in mind I am very new to ubuntu.

---

### Post by mocoloco on 2008-08-28
Depends on how you did the XP install.  If it was only reinstalled on it's own partition, Ubuntu should still be there.  Your HD has a section called the Master Boot Record (MBR) which is where GRUB goes (the bootloader Ubuntu uses), and Windows will overwrite it with it's own boot loader.  On top of that unlike Linux distros, Windows doesn't check to see if there are other operating systems on the drive and offer you the option to access them, it just assumes it's the king of the machine.

Boot from an Ubuntu LiveCD and you should be able to go to "Computer" and see your partitions.  If your Ubuntu partition is there, here are instructions to [reinstall GRUB while running from a LiveCD]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by phidia on 2008-08-28
No it isn't deleted windows always puts the bootloader in for windows only.
Use your ubuntu install disk and select re-install grub or get the super grub disk.

---

### Post by yaaman on 2008-08-28
Thank you mocoloco and phidia for your quick reply. I have one more question the ubuntu version on my laptop is 7.10 and if I Boot from an Ubuntu LiveCD does the CD have to be the same version as the Ubuntu installed on my laptop? Because I have a live CD for 8.10 will this also work?

Thanks in advance.
-yaaman

---

### Post by amirman on 2008-08-28
yaaman, it's not the same version but since you're using it to just reinstall GRUB it doesn't matter, GRUB is independent of ubuntu, it just lets you boot partitions.

---

### Post by mocoloco on 2008-08-28
amirman is right, it will still work fine with your 8.04 disc.

---

### Post by yaaman on 2008-08-29
Thanks guys, it took less than two minutes to get my boot loader back. You guys are awsome!

-yaaman

---

