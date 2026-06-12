---
title: "[SOLVED] Partitioning Gone Wrong"
date: 2008-07-29
forum: General Help
---

### Post by SlalomMan on 2008-07-29
Earlier this month I decided to feed Ubuntu a little bit more memory; I couldn't increase Ubuntu's partition size from the OS, and I didn't have my LiveCD, so I downloaded GParted USB edition and shrunk my Vista partition by 60GB and gave it to my Ubuntu partition. GParted messed something up, though; I could still boot to ubuntu and vista, but XP displays an error message "NTLDR is missing."

I can remedy this by using a windows xp recovery disk to fixboot/fixmbr, which allows XP to boot. However, this erases GRUB and the Vista Bootloader. So only XP can boot. I tried multiple times to restore the Vista bootloader using EasyBCD, so I could then install GRUB on top, but every time I reinstall the Vista Bootloader, I get the "NTLDR is missing" error on XP.

Any suggestions?

---

### Post by nbayiha on 2008-07-29
What about fixint first Vista/XP like you did fixboot/fixmbr and then reinstall grub from ubuntu live cd. 
I think it should fix your problem.

---

### Post by SlalomMan on 2008-07-29
Alright, my logic was that if XP didn't work from the Vista bootloader then it wouldn't work from grub.

---

### Post by louieb on 2008-07-29
Windows is weird when it comes to booting multiple versions. 
Basically it wants the older version installed 1st. The newer version will the place its boot loader in the older version. If that makes ant sence:confused:
[Understanding MultiBooting]("http://www.goodells.net/multiboot/index.htm") this is about booting multiple versions of windows

---

### Post by SlalomMan on 2008-07-29
I think I know how it works, I can restore the Vista bootloader so I see both XP and Vista as options, but when I select XP, i get an "NTLDR" is missing message; I'm not sure of the problem. I might boot to vista and try to put XP into the menu from there; I'm kind of desperate now, whatever it takes to get back to ubuntu.

---

### Post by nbayiha on 2008-07-29
So try to get Grub reinstall from LiveCd , here is the link. Follow those instruction and you should have it done.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=backup+system](http://ubuntuforums.org/showthread.php?t=224351&highlight=backup+system)

[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+Grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+Grub)

As for me the first thread is much more explicit.

---

### Post by SlalomMan on 2008-07-29
I'm quite confident that I can get grub working; the problem is that XP won't work after I restore grub, or the vista bootloader. I'm thinking of just screwing it and reinstalling XP, maybe that will fix the problem.

EDIT: I downloaded the latest version of EasyBCD, restored the MBR and Vista boot files, and added XP to the bootloader...it worked! Now I just have to install GRUB from the liveCD, and everything should be working...right?

EDIT Again: Reinstalling Grub did it; thanks everyone who helped.

---

