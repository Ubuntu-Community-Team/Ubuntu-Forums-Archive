---
title: "Problem while installing Jaunty without a CD"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by Slorg1 on 2009-05-13
Hello,

I followed step by step the no CD-ROM install from linux install from the ubuntu help website. Of course I encountered the problem linked with the fact that the partition I am using to boot and install is on the same disk as the destination OS and I used the super umount options from the help.

A little bit of background information first : I am actually installing Jaunty on my wife's computer which has the particular problem of not being able to boot on its built in CD-ROM drive nor any external drive from that matter. It is a sony vaio with a little BIOS defect that makes it impossible. I previously installed Intrepid Ibex on it from windows and she was very pleased with it although she was experiencing some slow downs from time to time. When the new ubuntu (9.04) came out I wanted to make a clean install so she would be happy. I reduced the swap partition size to have a good 750 MB free to copy the disk as described in the help. The installation completed without any errors and then prompted me to reboot. This is where the problem is. When I reboot I only get 1 line in Grub : the mem test. So I played around with it tried to reinstall several times, reset Grub... nothing worked. I do find something suspicious though: in /boot, she does not have any files over 10MB, and she only has a vmcoreinfo,a System map, an initrd and nothing looking like the kernel was put there. When I played around with Grub I got the error saying it does not know the FS format. Looking online I saw there were issues with ext4 so I went back to ext3: problem persisted which is logical if she does not have a working kernel.

Alright I think I described as much as I could the problem, would any of you have an idea about what is going on?

Thank you in advance guys.

---

### Post by Slorg1 on 2009-05-15
Hi,

Well I figured a work around my problem by having Jaunty installed on a different machine and copy the generic kernel in the boot directory, I then edited the menu.lst to use the right root. I hope it help anyone running in the same problem.

Regards

---

