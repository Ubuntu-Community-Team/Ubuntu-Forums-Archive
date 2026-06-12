---
title: "When i installedf ubuntu from windows. Missing MBR error. Pls help"
date: 2008-07-14
forum: General Help
---

### Post by Racera1 on 2008-07-14
After install when i boot to ubuntu i get a missing MBR error message. Install from windows using wubi. What do i do pls.?

---

### Post by Racera1 on 2008-07-14
I installed using wubi installer to second partition.Wubi formated and rebooted to menu. and then i get missing MBR error. Does anyone know what will correct this?

---

### Post by Racera1 on 2008-07-14
I installed using wubi installer to second partition.Wubi formated and rebooted to menu. and then i get missing MBR error. Does anyone know what will correct this?

---

### Post by ago on 2008-07-14
Wubi does not touch the MBR so it must be some other issue. You can try to restore from the windows cd, you can also use the ubuntu cd to access and copy the files.

---

### Post by Pumalite on 2008-07-14
Double post!
[http://ubuntuforums.org/showthread.php?t=859400](http://ubuntuforums.org/showthread.php?t=859400)

---

### Post by Pumalite on 2008-07-14
Something to read:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Racera1 on 2008-07-14
Do i need the grub installer as well?

---

### Post by Racera1 on 2008-07-14
The first time i installed ubuntu with grub & Wubi the install went clean but after it loaded to ubuntu a grub command bash program started and i dont know where to go from that point. So i reboot back to xp and the startup fails saying no autochk program found so i thought id see if i could repaip with xp disk and the xp startup says it doesnt recocnise the file system. As well, when i boot to ubuntu i get to grub command bash and dont know where to go from there.

---

### Post by Racera1 on 2008-07-14
I installed ubuntu on my system with wubi installer, but i had grub in the folder too. when it booted to ubuntu it got to grub command loader and i dont know what happened after that. i didnt know what to do in grub prompt so i rebooted to windows and now windows tells me it cant find autochk program and shutsdown. can anyone help me with this please?

---

### Post by Racera1 on 2008-07-14
After reboot to ubuntu i get to grub command prompt and i dont know what to do after that. How do i lose the prompt and run ubuntu?

---

### Post by Racera1 on 2008-07-14
I nstalled ubuntu with wubi loader from windows xp, it went fine to a point.After i intalled ubuntu to sencond partition on second hard drive [E:] my first drive went inactive it still functions i can boot to xp loading screen then it says cant find autochk.exe then after disabling reboot on error i get to see the error something about value of drive should be 0 3 0000000 is 0 0 0000000 0 0 0000000. How can i fix this problem and save xp drive?

---

### Post by upchucky on 2008-07-14
both os are there the bootloader is confused.

may need advanced supergrub to repair, but also there are hundreds of posts here about bootloader repair. search for them there are many ways to fix this depending on the symptoms. post your specs here according to the posts you find.

---

### Post by Afkpuz on 2008-07-15
Is this right after a fresh install?  If so, sounds like the install didn't work correctly.  Might want to try a reinstall and check the integrity of your install disc.

---

### Post by overdrank on 2008-07-15
> **Afkpuz said:**
> Is this right after a fresh install?  If so, sounds like the install didn't work correctly.  Might want to try a reinstall and check the integrity of your install disc.

Hi and if you look at the other post by the op. installed using wubi and is having issues.
And has multiple threads on the issue.

---

### Post by Racera1 on 2008-07-15
I installed using wubi installer to second partition.Wubi formated and rebooted to menu. and then i get missing MBR error. Does anyone know what will correct this?

---

### Post by Racera1 on 2008-07-15
I installed ubuntu from xp to another hard drive and i apear to be having bootloader issues. The intall went ok rebooted into grub command prompt and i was coming here to see what to do next. So i reboot to xp it gets to XP loading screen, stops with a missing autochk.exe bypassing autochk and reboots. So from there first thing shut off reboot to get error report "Value of 0,3 is 0,0,00000 0,0,00000 maybe more zeros but you get the idea. So i use xp repair and fixmbr, fixboot and chkdsk /p, still wont take me to windows. Checked partition and it says its inactive.  Can anyone offer more suggestions or an actual fix?  I wouldnt really care if ubuntu would load because in order to get back up i had to install xp again and i cant activate it again (How stupid is that in a product???). Just another reason to install Linux!!!!!!   I can still use grub prompt.

---

### Post by logos34 on 2008-07-16
Boot from the ubuntu live cd and open gparted (system>admin>partition editor)

right click on xp partition>manage flags>check 'boot' (=making it 'active')

But not sure that will make a diff because there may be deeper probs with xp

You can check the integrity of the partition table with testdisk

system>admin>sofware sources>enable universe repo

sudo apt-get install testdisk

sudo testdisk

(boy I've recommended that program so much lately I'm starting to sound like a one-note Johnny!)

You might want to mount your linux root and post output of 

sudo fdisk -l

and your /boot/grub/menu.lst (which might clue us in on why you're getting the grub command line rather than menu screen)

Or get Super Grub Disk.  It might be able to fix boot of ubuntu

---

### Post by nwubie on 2008-07-16
You started 8 threads about the same problem. Please don't start multiple threads, there's no way you'll get better help this way since we can't see what's already been advised to you.

Your best solution is to follow logos34's advices here but don't forget to tell him you used wubi :
[http://ubuntuforums.org/showthread.php?t=860737](http://ubuntuforums.org/showthread.php?t=860737)

---

### Post by p_quarles on 2008-07-16
Eight threads merged. Please refrain from cross-posting.

---

### Post by ago on 2008-07-17
As mentioned earlier, wubi would not touch the mbr. It might be that you are confusing with a fs corruption or some other side issue/hardware problem. In any case you might want to try booting off windows CD in the recovery console and run chkdsk /r and/or fixmbr

---

