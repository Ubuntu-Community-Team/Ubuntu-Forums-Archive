---
title: "[SOLVED] Help needed for install of ubuntu"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by wenn_die on 2008-12-27
I have been interested in using linux for a while and here I am. I have an XP home, Intel dual core, 2X HDD system
The first HDD is windows only 350GB.
The second HDD which is blank I partitioned into 3 partitions with msoft disk manager, the ran Parted Magic where I made the first partition ext3 10GB, the second partition swap/linux 35GB and wish to keep the remaining extended partition for windows backup. I got confused about where these partitions should be mounted.
I then tried to install ubuntu 8.10 form a live cd which I had checked for errors and was ok.
The first menu loads, I choose english then the first option of demo ubuntu with later install. It starts to install, the slide progress bar gets to about 95%, then the screen goes black and nothing happens. Cant use my mouse, nothing, though the cd spins for a few minutes and the screen occassionally flickers. I tried this several times, each with the same result, and eventually have to reset.
Any help much appreciated.:confused:

---

### Post by Partyboi2 on 2008-12-27
35 gig for swap is to much you only need a swap about 1.5 the amount of your onboard ram so if you had 512mb ram your swap would only need to be 1 gig. But I would say no more then 3 gig max.
When you are at the main menu of the ubuntu live cd press F6 and remove the word splash then press enter. Hopefully this will provide more info on where it is stopping.

So for an example you could set it up like this:
10 gig / (mount point set to /) (system files)
1 gig swap (if you have 512mb ram)
34 gig /home (mount point set to /home) (where your data, videos, music etc..)

---

### Post by wenn_die on 2008-12-28
OK, got the install sorted thanks to Partyboi2 and nhasian. I found the alternate install gave me security that I was installing correctly.
Now when I try to boot the installed ubuntu I have the same issue as when trying to load the initial install disk.
I get the ubuntu logo, an orange progress bar fills to about 95%, then everything goes black, and nothing, till eventually I have to do a hard shutdown.
I have checked my windows install and it is still fine.

---

### Post by Partyboi2 on 2008-12-28
Try booting again with out the splash screen. When you boot and are at the grub menu choose highlight the first entry ubuntu 8.10, kernel... and press "e" then highlight the line starting with "kernel" and press "e" again then remove the word splash and press "enter" then "b" to boot.

---

### Post by wenn_die on 2008-12-28
OK, did that. Could see the boot up of various bits scrolling down the screen, but then it gets to about the second page of boot text and the screen goes black.
I cant read the last line of text, it moves too fast.
Again need to reset then reboot.

---

