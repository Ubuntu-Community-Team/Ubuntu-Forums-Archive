---
title: "&quot;SMART not available&quot; Why did it turn off? How to bring it back?"
date: 2010-04-20
forum: Hardware
---

### Post by Zeniff on 2010-04-20
Hi~
In brief:
I'm using Ubuntu 9.10.
SMART turned off. I don't know why. I don't exactly know when.
How do I make SMART come back?
I did not before and do not now have smartmontools installed.
I did not update the kernel or change BIOS.
I'm pretty sure I did nothing remotely related to any system changes in the past week.

All my hard drives are still just as accessible as before, but I would really like SMART back, or at least know the reason it's gone or turned off.

Thanks for any kind help you can offer!!! ^^


If you want more info:
I have an extra ~160 GB internal IDE hard drive. It was bought used and since I put it in, Disk Utility (palimpsest) had immediately marked it as failing because of 103 bad sectors. I ignored it, because I simply want to use the drive as extra, expendable, temporary space, such as to practice installing other Linux/BSD distros (since many distros' documentation often leave out critical points useful to new users and I'd rather not have to redo everything on my good, but old HD.) 
I had run all three tests available on the disk, and all of them passed. There were no other problems with the disk and it never increased in bad sectors. 
I installed one BSD and also put several GB of stuff on the disk. If it actually does fail, I'm okay with that because it's all extra stuff.
Everytime (as far as I know) I turned on this desktop computer, it would let me know that the disk was failing... until yesterday when I first noticed it didn't... 
Did Disk Utility change it's mind about the disk? 
No, it says SMART is not available.
It says SMART is not available for any of my three hard disks.

This is strange, because I did not do any kernel updates, I did not change anything in BIOS, I did not use the computer much recently and only installed a few games to try out.

Also the "One of your hard disks may be failing" message that appeared at every boot had two choices: "OK" and "Cancel" and I'm really sure that I chose both at different times, and it still appeared on the next boot.

---

### Post by ellgor on 2010-04-21
Hi,

I have my Smart disabled by choice, om my comp its the bios that determines whether its on or not, when you boot-up access the bios menus, especially the one related to hard drives, thats where the option for turning Smart on or off is for mine. 

Regards, Ellgor.

---

### Post by Zeniff on 2010-04-22
Thanks for the good tip, Ellgor. ^^

Unfortunately, though, my BIOS doesn't have any options related to SMART and so was always apparently on by default...until now.

It looks like someone just had a similar issue as me:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9148254](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9148254)
Looks like a recent update to devicekit-disks turned it off.

I'm still hoping there's a way to turn it back on, though~

---

### Post by Morbius1 on 2010-04-22
SMART has ben disabled because it does dumb things to SSD's:

[https://edge.launchpad.net/ubuntu/+s...s/007-2ubuntu6]("https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6")
                                                      > devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

  * Add 11-disable-smart-probing.patch: Disable ATA SMART probing on ATA
    disks. It causes hardware damage to a lot of SSD disks. This is a
    workaround, until a real fix in libatasmart is found. (LP: [#445852]("https://edge.launchpad.net/bugs/445852"))
 -- Martin Pitt <email address hidden>   Thu, 25 Mar 2010 18:47:35 +0100                       [COLOR=Blue]EDIT: OOPS, sorry. It seems your link points to the same bug report. Didn't read your post carefully enough.[/COLOR]

---

