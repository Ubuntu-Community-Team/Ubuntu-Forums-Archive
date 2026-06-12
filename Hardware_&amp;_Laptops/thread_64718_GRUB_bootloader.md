---
title: "GRUB bootloader"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by windowsatemyhomework on 2005-09-11
ubuntu is on a HDD that is the master on the Primary IDE. Windows XP is on SATA-4. I am only presented with a choice of operating systems when I set the ubuntu HDD as the first booting drive, and in that case, the Windows XP choice doesn't work. I'd like to be able to switch between operating systems without changing the boot order all the time. The message I get when I try the Windows XP choice is this:```
    Booting 'Microsoft Windows XP Professional'

root    (hd1,0)
    Filesystem type unknown, partition type 0x7
savedefault
chainloader +1
```

---

### Post by windowsatemyhomework on 2005-09-11
I think I may have really fouled things up now. I reinstalled ubuntu, and this time I tried putting the bootloader onto the drive with Windows XP (thinking that linux, being more versatile, was more likely to successfully be pointed to from a different drive), and now when I boot up either drive I get the choice of which OS to run. When I boot up off of the ubuntu drive, ubuntu works and Windows doesn't (like before), but now when I boot up off of the windows drive, neither works, meaning I have no way of getting into Windows. Can anybody help me out? It would be best if I could figure out how to get Windows to run when I boot up from the ubuntu drive and choose Windows when the choice comes up, but, pending that, it would be nice to simply remove the bootloader from the windows drive so that I can at least get into Windows somehow!

---

### Post by whisperx on 2005-09-12
[QUOTE=windowsatemyhomework]I think I may have really fouled things up now. I reinstalled ubuntu, and this time I tried putting the bootloader onto the drive with Windows XP (thinking that linux, being more versatile, was more likely to successfully be pointed to from a different drive), and now when I boot up either drive I get the choice of which OS to run. When I boot up off of the ubuntu drive, ubuntu works and Windows doesn't (like before), but now when I boot up off of the windows drive, neither works, meaning I have no way of getting into Windows. Can anybody help me out? It would be best if I could figure out how to get Windows to run when I boot up from the ubuntu drive and choose Windows when the choice comes up, but, pending that, it would be nice to simply remove the bootloader from the windows drive so that I can at least get into Windows somehow![/QUOTE]

I'm not too sure I can find a solution to your problem, at least not yet, since I'm still a complete novice with this myself.  However, my set-up seems nearly identical to what you described and I had the exact same problem (and got the same message).

When you say that you put the bootloader on the same drive as Windows XP, do you mean that you installed Ubuntu on that drive (on a new/separate partition than the one Windows is on)?  If that's the case, all you need to do is use the partition manager included on your Windows installation CD to delete the partition with ubuntu, and you should be able to boot into Windows on that drive once again.  Sure, you lose the ubuntu installation, but at least Windows is restored and you can try again with Ubuntu.

Alternatively, if you somehow put ONLY the bootloader on your SATA drive but left the Ubuntu OS itself on your IDE hdd (is that even possible to do??), then I'm not sure what to do :?

As for myself, I still haven't found a way to have a smooth dual-boot system.  Right now I've got Ubuntu on a partition on my IDE but I set my BIOS to boot off my SATA with Windows XP.  Like you, if I do it that way, Windows doesn't seem to recognize the Ubuntu OS and doesn't give me the option to load it, but at least I can get into Windows when I need to get work done and stuff.  If I set my BIOS to boot off the IDE, I get the Grub bootloader which will load ubuntu, but not WinXP.  So basically I have to go through the BIOS to choose... not ideal but it might be the best case scenario for the time being.

---

### Post by renatomsteiner on 2005-09-14
I have the following problem: one single sata hd, windows 2000 installed on partition 2, files on partition 3. I want to install ubuntu on partition 1 but I'm afraid to mess up the boot for windows!
Any sugestions?

---

