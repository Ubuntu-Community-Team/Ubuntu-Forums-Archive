---
title: "Ubuntu multi boot with multiple hibernation"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2009-01-20
I have 4 different OS on my multi-boot disk:  XP, Ubuntu-hardy, Ubuntu-intrepid, kubuntu-hardy.  I also have a Shared_Data partition and 3 swap partitions--one for each Ubuntu OS.  I would like to be able to hibernate one OS, start up another, hibernate the second one, and resume the first OS.  I have been able to do this by editing /etc/fstab and /boot/grub/menu.lst.  However, when I change a file in one OS and resume another one I end up bashing my disk partitions.  So far I have been sucessful in recovering them using fsck, but I need to fix the problem.  

From another posting I found out about /etc/initramfs-tools/conf.d/resume.  This file contain a single line "RESUME=UUID=3f349791-91e1-4641-a7a8-9c0d50035542" specifying a resume device.  I now know that I didn't have this file set correctly in two of my OS's.  Could this be the cause of the problem?  Does anybody know what use is made of this file and how an incorrect setting might manifest itself?  I would experiment more, but I am concerned that I might not be so lucky next time in recovering corrupted files.

In addition, I don't understand what would happen if I opened and wrote to a file with OpenOffice, saved the file to the Shared_Data partition, left OpenOffice running, hibernated the OS, started another OS, opened the same file with OpenOffice in the 2nd OS, edited it, hibernated the second OS, resumed the first OS, and continued editing in the first OS.  I don't know if the hibernate feature is smart enough to handle this situation.  It would require a very sophisticated design.  Now I am beginning to think that it may be impossible to allow multi-hibernations with resumes while using a Shared_Data partition for all my user files.

Can anybody tell me whether multi hibernation is possible with the present design, or should I just give it up?  Incidentally I see that at least one other person is trying to do the same thing--http://www.linuxforums.org/forum/ubuntu-help/126744-solved-vista-multiple-linux-installations-partitions-boot-loading.html

Thanks for any help you can give.

Ralph

---

