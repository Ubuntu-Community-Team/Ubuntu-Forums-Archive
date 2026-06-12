---
title: "[SOLVED] Dual-Booting"
date: 2008-08-16
forum: General Help
---

### Post by robotman5 on 2008-08-16
i have kubuntu as my main OS and i wanna put Windows 2000 Pro on a 10 GB harddrive  is it possable?
 

i just wanna Dual-boot!


Can Someone Please help!:confused:

---

### Post by robotman5 on 2008-08-16
Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump Bump

---

### Post by jualin on 2008-08-16
You can install Windows 2000 but it will overwrite the GRUB (Linux Boot Loader) therefore you would need to follow [this instructions]("http://ubuntuforums.org/showthread.php?t=891898") after you finish installing Windows 2000. Hope this helps!

---

### Post by alzie on 2008-08-16
There are instructions for dual booting here as well: [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm) 

Please be sure to back up any important files before you start.  Just in case... and besides its a good thing to do periodically ;)

---

### Post by robotman5 on 2008-08-16
ok ill try that Thanks.:popcorn:

---

### Post by robotman5 on 2008-08-16
ok its copying the files now for Windows 2000 Pro



ill tell what happens next later:guitar:

---

### Post by robotman5 on 2008-08-16
k i restored my Kubuntu Now i need Help adding Windows 2000 to the GRUB Menu CAN SOMEONE HELP??



oh and BUMP BUMP BUMP BUMP!:guitar:

---

### Post by alzie on 2008-08-17
We can try,  where are you at?

You've installed Windows,  Did it boot up ok?

You've reinstalled grub?

Can you give the link to the instructions you followed to get to where you're at?  And did you make it all the way through those instructions or did you stop part way?

And would you run " sudo fdisk -l " and " gedit /boot/grub/menu.lst " in terminal and post the results. ( -l  and lst use lowercase L's or just cut and paste)

---

