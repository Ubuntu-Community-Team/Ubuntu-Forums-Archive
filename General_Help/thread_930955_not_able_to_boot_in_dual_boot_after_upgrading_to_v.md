---
title: "not able to boot in dual boot after upgrading to vista..."
date: 2008-09-26
forum: General Help
---

### Post by Mia_tech on 2008-09-26
guys, I had my laptop in a dual boot conf, and I after I upgrade my xp to vista, I'm no longer able to boot into ubuntu, I guess the upgrade overwrite my MBR, and therefore the pc no longer sees two OS, but instead only one.... I don't remember exactly what I have to do, but I think I probably have to redo the grub, I read a post around here about that, but can't find it now
could someone point me in the right direction

---

### Post by EmanresuusernamE on 2008-09-26
Boot to a liveCD, and then under Gparted, select your linux partition, right-click on it and then click on Manage Flags.  Then choose boot, Close, and then apply your changes.

---

### Post by markharding557 on 2008-09-26
> **Mia_tech said:**
> guys, I had my laptop in a dual boot conf, and I after I upgrade my xp to vista, I'm no longer able to boot into ubuntu, I guess the upgrade overwrite my MBR, and therefore the pc no longer sees two OS, but instead only one.... I don't remember exactly what I have to do, but I think I probably have to redo the grub, I read a post around here about that, but can't find it now
could someone point me in the right direction

Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.

If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:

How to Restore the Grub Menu:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su or sudo -i or sudo grub"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps

---

### Post by Mia_tech on 2008-09-26
let me just clarify something here, I think what it was before was the grub, b/c I had xp, then installed ubuntu in dual boot that would make the grub overwrite the MBR, then I upgrade xp to vista again that would make vista overwrite itself over grub, that's why I need to restore the grub

let me know if I'm in the right path... and also which of the two previous route should I take, mean while I'm googling

---

### Post by Mia_tech on 2008-09-26
let me say something... if you don't know what you're doing please don't tell ppl to do something you don't know..I'm referring to the firs post

---

### Post by Mia_tech on 2008-09-26
markharding557 thanks a lot, I tried a second time and it worked, I guess the first time I was a bit mad lol and didn't type the commands correctly, but after a second time got it right, and you save me the time of having to search on the big G

just on a side question, you asked me if the pc was booting with grub or through vista, I thought that the only way of doing dualboot was with windows installed in the 1st partition and linux on the 2nd and that way is obvious that grub will overwrite the MBR... or is there another way? please explain

---

