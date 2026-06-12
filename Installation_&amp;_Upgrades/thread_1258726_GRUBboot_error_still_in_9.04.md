---
title: "GRUB/boot error still in 9.04?"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by JaredtotheRESQ on 2009-09-05
Hello everyone,
   I think this is in the correct section, and I'm going to try to explain as well as I can. It's been a little while since I used Ubuntu (used to be a full time user before this problem), so, I'm just double checking before I go back in.

   I've been an Ubuntu user since 6.10, and I was a very happy user until 8.04 was released. When I upgraded to 8.04, everything went smoothly. After about a week, I got a GRUB/boot error (If I remember correctly, it was something like GRUB error 17) and could only boot past the BIOS screen before erroring. I thought maybe something in the upgrade was bad, so I reinstalled.

   After reinstalling, everything was fine again....until about a week later, when I got the GRUB/boot error again. I researched the problem and found out the Boot partition was needed at the front of the HDD in order for it to boot properly. If it wasn't at the front, after putting so much data on the HDD, it wouldn't be able to find the boot partition anymore, resulting in the error.

   After finding this out, I reinstalled and manually created the partitions. I thought everything was fixed and I could start enjoying my computer again. Then AGAIN, after about 2 weeks this time, it gave the same error message. Fed up, I installed XP and have been using it since.

   I don't like XP. Never have, never will. I want to use Ubuntu again. I am in the process of building a new computer, and want it to solely run Ubuntu. My question is; does 9.04 still give that error? I can give the specs on the computer I'm building (or the one previously used), if that will help determine if hardware is at fault. 

Thank you so much for your time, and sorry about the wall of text. I'd rather give too much information than too little.

---

### Post by presence1960 on 2009-09-05
well first of all that error is not a fault of Ubuntu. That error is caused by the BIOS not being able to read past a certain point on the hard disk. if you are building a new computer your BIOS should not be affected by the inability to read a point past 137 GB on a hard disk. it is unfortunate that no one explained that to you last time. It is not Ubuntu's fault. A BIOS upgrade may have fixed it or you could have bought a second hard disk to put in your machine and installed Ubuntu only to that disk.

The separate /boot partition at the very beginning of the hard disk usually circumvents that error.

---

### Post by meindian523 on 2009-09-05
Well, did you create a thread about your error 17 problem?If yes, please provide the link here.
And do provide hardware specs of both machines. I don't think it's a hardware issue, unless it's the hard disk, which seems unlikely since the error occurred even after relocating the partition. Still, we might be able to see what's the difference.

---

### Post by JaredtotheRESQ on 2009-09-05
Now that you said something about it, I do remember something about the BIOS not reading past 137 GB. However, I was very confused why it would work with 6.10-7.10 with no errors whatsoever, and all the sudden with 8.04, it happened frequently. What are the BIOS specifications that make this error occur?

I'll list both my computers' specs in a little bit. I'm at work right now and don't have access to them at the moment.

---

