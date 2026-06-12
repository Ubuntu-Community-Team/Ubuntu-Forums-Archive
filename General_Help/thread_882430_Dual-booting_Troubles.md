---
title: "Dual-booting Troubles"
date: 2008-08-06
forum: General Help
---

### Post by XkW on 2008-08-06
Hi guys!

  I'm a new Linux user, just got into it about 2 weeks ago. It all started with the dreaded loss of sound on my Windows HDD, had to reinstall it, only problem was, IT WAS A SATA! Windows doesnt natively support SATA drives, so I went out and bought a new one. But, before I bought a new one, I installed Ubuntu. Me being an expert at Windows, I caught on fast. I like Ubuntu, so I wanna dual boot. Only problem is, I can't get GRUBs to boot up! I've followed various guides, including the whole "sudo grub", "find /boot/grub/stage1", blah blah blah. I've even installed Ubuntu AFTER Windows, but the MBR still reigns supreme :(
I have 2 HDDs
1x 80gb IDE HDD (Windows is on this one)
1x 80gb SATA HDD (Ubuntu is on this one)

Your help is VERY much appreciated!

  I look forward to your replys.
~Kev

---

### Post by tuxxy on 2008-08-06
If i understand right GRUB wont load and its booting windows everytime? you may have a boot loader that you need to diable in your BIOS first, this could be preventing GRUB loading

---

### Post by XkW on 2008-08-07
Well, thanks for the reply, but there was nothing in there. However, I did get it to work ^_^
As I was poking around in my BIOS, I found the Hard Disk Boot Priority. Now, as you know, I have an IDE and SATA HDD, but, my BIOS are retarded and only recogonize IDE drives, but there was a second option, the second hard disk was "Bootable add-in device," so I made that one boot up first, and it worked like a charm, GRUBs came right up, everything boots up perfectly. Thanks for your suggestion ^_^

---

