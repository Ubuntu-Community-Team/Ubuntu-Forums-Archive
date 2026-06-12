---
title: "[SOLVED] Live CD doesn't boot"
date: 2008-09-04
forum: General Help
---

### Post by Coco999 on 2008-09-04
Live CD does not boot

I'm trying to work with a brand new CD (ubuntu - 8.04.1 - desktop i386, just downloaded).

I get an error message:


[COLOR="Red"][ 252.664924 ] Buffer I/O error on device sr1, logical block 32
[ 252.668198 ] Buffer I/O error on device sr1, logical block 33
[ 259.805161 ] Buffer I/O error on device sr1, logical block 32
BusyBox v1.1.3(Debian 1:1.1.3 - Subuntu12 Built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)[/COLOR]


If I enter 'help' I get a list of commands, most of which don't seem to work at all. One of the commands is wget, and it seems to work, so some kind of operating system seems to be loaded already, although useless to me.

However, I can boot OK with 2006 Kubuntu or Gnomix 2.10 live CDs. Also I can boot OK with the Ubuntu as quoted in another computer.

What does the error message mean? 
What is the trouble and what can I do?

The computer is a Pentium IV with 1 GB RAM and runs at 1600 kH, I think.

Thank you for your help and regards.

---

### Post by overdrank on 2008-09-04
Hi and please do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=908786](http://ubuntuforums.org/showthread.php?t=908786)
Have you checked the cd for errors and the ISO
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
I do understand that the cd may work in another system but as you stated you have tried other versions of ubuntu and they work. If you check the cd and iso for errors this will help trouble shoot I believe.

---

### Post by Coco999 on 2008-09-04
Sorry, overdrank, but there are so many new threads that if you don´t get a reply within a few hours, the thread becomes sort of stale and nobody seems to be reading it any longer. Anyhow, I still have the problem and therefore can't cross it out as solved. Since you are in the forum staff, perhaps you may suggest what can I do, perhaps place the question in another section.

As a rule, after I download an ISO image, I calculate the MD5 and compare it with the published value before burning. Also the burning program checks the disk before finishing. So I'm fairly sure that the CD is right. Also it works properly in other machine, as live and for installation in the HD. In my modest opinion, there must be something wrong in the original ISO image, having it check something that is not necessary. I hope you can sugest something for me to do, otherwise I wait eagerly for the next version hoping the development team is aware of the unsolved issues.

Thank you for your concern.

Best regards
Coco999

---

### Post by overdrank on 2008-09-04
> **Coco999 said:**
> Sorry, overdrank, but there are so many new threads that if you don´t get a reply within a few hours, the thread becomes sort of stale and nobody seems to be reading it any longer. Anyhow, I still have the problem and therefore can't cross it out as solved. Since you are in the forum staff, perhaps you may suggest what can I do, perhaps place the question in another section.

As a rule, after I download an ISO image, I calculate the MD5 and compare it with the published value before burning. Also the burning program checks the disk before finishing. So I'm fairly sure that the CD is right. Also it works properly in other machine, as live and for installation in the HD. In my modest opinion, there must be something wrong in the original ISO image, having it check something that is not necessary. I hope you can sugest something for me to do, otherwise I wait eagerly for the next version hoping the development team is aware of the unsolved issues.

Thank you for your concern.

Best regards
Coco999

Ok and you may bump your thread once a day to help viewing.
You can try and use the F6 option and remove the quiet splash to see and errors and add noapic in it place.

---

### Post by Coco999 on 2008-09-04
Thank you. I tried F& in other machine and it gives me a long line of abstruse commands. But no means to make a choice, either to mark up or remove any of them. I'll try it again, but it does not seem a friendly feature to me. I saw the word splash but could do nothing about it. I didn't see the word noapic.

---

### Post by Coco999 on 2008-09-05
I marked this thread as solved because I tested with yet another version, 7.04, and it booted OK, confirming that there is a bug in the new 8.04, that makes it incompatible with certain hardware configurations. I hope the development team are aware of this and will correct this for 8.10. 

Many thanks to all who replied.
Regards.

---

