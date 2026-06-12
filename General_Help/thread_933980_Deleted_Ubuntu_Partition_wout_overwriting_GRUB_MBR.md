---
title: "Deleted Ubuntu Partition w/out overwriting GRUB MBR, please help!"
date: 2008-09-30
forum: General Help
---

### Post by Hungus on 2008-09-30
So I made the mistake of deleting my Ubuntu partition before uninstalling the GRUB MBR. I am stuck in the boot screen with "Error 17". From what I've read, it sounds like I should actually be seeing Error 22.

I've read some posts and articles describing solutions that involve either re-installing GRUB or overwriting the GRUB IPL with the bootloader for my Vista. These both sound like they would fix my problem however all the posts I've read about how to do this don't explain how to get past the boot screen so that I can get in there and repair it. Currently, the only thing I can access on my computer is the BIOS setup screen which doesn't provide me with any options as far as re-writing the GRUB IPL code.

So basically, I understand how to solve the problem, however I don't have the access to my computer in order to do so. It's like seeing the light at the end of a tunnel through a wall of bullet-proof glass.

I hope that I've explained this thoroughly enough, please let me know if anybody has any ideas! :)

---

### Post by melojo on 2008-09-30
have a look here [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by melojo on 2008-09-30
here is another link  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bufsabre666 on 2008-09-30
with vista its cake, boot from the vista disk, and select your language and the next screen on the lower left it says repair, click on that and it will search for your vista partition, click on your vista partition when it shows up and then select next, on the next screen select startup recovery, it take a couple minutes but it will rewrite the vista bootloader, next reboot and enjoy

people critize vista too much, they made a whole lot so much easier, this same process with xp took like 40 more steps plus a recovery console, which from what you can see on this forum, alot of people dont like command prompts, so this way is way better ((and ive done it a few times so i know it works))

---

