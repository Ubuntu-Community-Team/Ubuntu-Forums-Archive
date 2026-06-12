---
title: "Dual boot and Windows disk check with GRUB"
date: 2008-09-03
forum: General Help
---

### Post by ds3 on 2008-09-03
I'm not sure if this is the correct place to ask for help, but hopefully someone will have a suggestion.
I have a Dell Latitude D531 which came with Windows XP Professional and I set up to dual boot with Hardy Heron. It uses the GRUB bootloader and I've never had any problems until I tried to run a disk check from Windows yesterday. The system restarted normally, I selected Windows XP from the operating system list in GRUB, and the disk check took place. Then the problem started: instead of completing loading Windows XP, the system went back to the GRUB menu. I selected Windows XP again and the system restarted the disk check...repeatedly.
I could still start Ubuntu, but it wouldn't access the Windows partition, presumably because it was locked waiting to complete the disk check since it didn't know it was done. I finally used F8 to restore Windows to the last working configuration, but is there no way to get the disk check to work with GRUB?
I'd appreciate any help.
Thanks.

---

### Post by caljohnsmith on 2008-09-03
> **ds3 said:**
> I'm not sure if this is the correct place to ask for help, but hopefully someone will have a suggestion.
I have a Dell Latitude D531 which came with Windows XP Professional and I set up to dual boot with Hardy Heron. It uses the GRUB bootloader and I've never had any problems until I tried to run a disk check from Windows yesterday. The system restarted normally, I selected Windows XP from the operating system list in GRUB, and the disk check took place. Then the problem started: instead of completing loading Windows XP, the system went back to the GRUB menu. I selected Windows XP again and the system restarted the disk check...repeatedly.
I could still start Ubuntu, but it wouldn't access the Windows partition, presumably because it was locked waiting to complete the disk check since it didn't know it was done. I finally used F8 to restore Windows to the last working configuration, but is there no way to get the disk check to work with GRUB?
I'd appreciate any help.
Thanks.
I don't think the Windows disk check problem had anything to do with a Grub problem, because to boot Windows, all Grub does is chain load the partition boot record (PBR) of your Windows partition, exactly like a Windows MBR does. If you want to prove it to yourself, you could even temporarily reinstall the Windows MBR with "fixmbr" from the Windows Install CD, and I'm betting that wouldn't change the problem at all. The problem lies with Windows I think, and there could be many causes for why Windows wasn't able to complete the disk check.

---

### Post by ds3 on 2008-09-03
I suppose that's possible, but it did complete the disk check. It went through it, gave results, claimed to be complete, and then went back to the GRUB menu instead of completing the Windows boot sequence. That really seems more like a boot manager problem to me than a Windows problem, but I could easily be wrong.
Can you suggest where I might find more information?
Thanks.

---

### Post by caljohnsmith on 2008-09-03
> **ds3 said:**
> I suppose that's possible, but it did complete the disk check. It went through it, gave results, claimed to be complete, and then went back to the GRUB menu instead of completing the Windows boot sequence. That really seems more like a boot manager problem to me than a Windows problem, but I could easily be wrong.
Can you suggest where I might find more information?
Thanks.
I think the only realistic way Windows could have put you back at the Grub menu is if it restarted your computer. All the boot manager does is try and boot an OS, but once the OS takes over and begins successfully loading, the boot manager has nothing to do with what happens after that. But like I mentioned, if you want to prove to yourself whether that is true or not, you can temporarily reinstall the Windows MBR with "fixmbr". If you do, instead of getting thrown back to the Grub menu, your computer will just try and boot Windows again I believe, and you'll be caught in a loop. Once you are ready to put Grub back in the MBR, you can just do the following from a Live CD:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][will return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

---

