---
title: "Busybox issue with new Mint install"
date: 2008-08-21
forum: General Help
---

### Post by tstack77 on 2008-08-21
I'm setting up a dual-boot system for a friend of mine after he showed a lot of interest in my hardy setup (it only seems to take one look ;-)

I decided on the latest Linux Mint, installed it with no issues, but on the first boot it stalled with error:

[B]Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/B]

I was able to get around it by deleting "quiet splash" from the Linux Mint boot command 'root=/dev/sda5 ro quiet splash'. Figuring I'd address this problem after I set everything up, I went ahead with the configuration and was able to boot into hardy each time using that method. 

Of course now after everything is all up to date and configured just so, the Busybox issue appears every time :mad:

I am quite the novice with the command line, so when I typed 'help' I had no idea what to do. After a few unsuccessful commands I typed in 'return' and got:

**Target filesystem doesn't have /sbin/init**

Ideas?

Side: I did a few searches on this subject and it seems the only people having this problem are those using the liveCD (bad medium) or wubi. Even though this differs already because the system is installed, I am positive that the CD is perfect from checking the MD5, AND I have used it to install Mint on my laptop.

---

### Post by tstack77 on 2008-08-25
Still having this problem and cannot boot into the ubuntu partition. I really don't want to format/reinstall if I don't have to.

help

---

### Post by randipoling on 2008-08-25
I have had this issue aswell..not even the recovery works for me...So I had to re-install...thats all the advice I can give...

---

### Post by tstack77 on 2008-08-25
Same, the recovery option worked once after the other quit. I would love to bypass a complete reinstall but will do it if I can be sure this problem won't return. It stinks that I don't even know what the issue is (argh)

---

### Post by phidia on 2008-08-25
Have you looked at your logfiles esp /var/log/messages? Maybe there's more info about this there.

---

### Post by tstack77 on 2008-08-25
I'm using the liveCD and have opened /var/log/messages, there's a lot here but nothing pertaining to Busybox...what am I looking for?

---

### Post by tstack77 on 2008-08-25
Alright, I give up. Burned another CD for insurance and am formatting now. Will update if new problems arise.

---

### Post by sokraski on 2008-09-12
I just did a fresh install of Mint and found the answer to the problem from reading many of the other pages.  You have to change (in menu.lst and fstab) /dev/hdaX to /dev/sdX.  I did this in both files, and it worked just fine afterwards.  I also had to do the same for my CD-ROM, but I don't think that everyone is having that problem as well.

---

