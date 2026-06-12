---
title: "Boot flags and Windows 7"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by whaledawg on 2009-05-18
So I had Ubuntu and grub duel booting fine with Windows 7. Then I tried to install OSX86 and someone my Windows partition got set as the boot partition.

I used the Parted Magic live CD to set Linux as my boot partition again and everything worked. That is the grub menu came up and I loaded Ubuntu.

But the next time I loaded Windows 7, it reset itself as the boot partition. How do I tell Windows 7(it should be similar to Vista) to stop setting itself as the boot partition?

---

### Post by coffeecat on 2009-05-18
Ubuntu doesn't need the boot flag. No Linux OS needs the boot flag. Windows needs the boot flag. If you're unable to boot into Ubuntu, there must be some other problem.

Or are you talking about something other than the boot flag?

---

### Post by JK3mp on 2009-05-18
+1 . I don't know much about windows 7. Tested it for my blog at one point, but standalone on a test machine. But u don't need a boot flag on linux.

---

### Post by whaledawg on 2009-05-18
But Windows has the boot flag so it boots into that instead of the Linux partition. Or I assume that's why, there could be something else.

But the gist is, delete the boot flag from the Windows partition and put it on the Linux partition, boot fine(to grub). First time I boot into Windows it always boots into Windows after that.

---

### Post by coffeecat on 2009-05-18
Have you got both Linux and Windows choices on your grub menu.lst? Because if so, you can forget about the boot flag. Just let Windows have it.

And if you do have both Windows and Linux choices in your grub menu, I'm afraid I don't understand what you are trying to say.

**Edit:** you do know that you can boot Windows from grub, don't you?

---

### Post by whaledawg on 2009-05-18
grub is on my Linux partition. If I boot to that grub takes over and I can choose my OS. If I choose Windows, from then on it automatically boots Windows.

---

### Post by coffeecat on 2009-05-18
> **whaledawg said:**
> grub is on my Linux partition. If I boot to that grub takes over and I can choose my OS. If I choose Windows, from then on it automatically boots Windows.

You are baffling me. You don't boot to grub; grub is the bootloader. The fact that grub stage 2 is on your Linux partition is immaterial.

Let's take this slowly. If you have grub installed, grub stage 1 is in the mbr, replacing the Windows mbr. When you first switch on, after the POST, the BIOS hands control to grub stage 1. That, in turn, passes control to grub stage 1.5, which is a small piece of code written to an otherwise unused area just after the partition table. Grub stage 1.5 then passes control to grub stage 2, which now displays the grub menu, and which just happens to be in /boot/grub of your Linux partition. But at this point you are not booted into Linux, even though the code controlling your computer is in your Linux root partition.

Now you choose either Linux or Windows from the grub menu. If you choose Linux, grub stage 2 invokes the Linux kernel and initrd, which initiates the Linux boot sequence. **You do not need a boot flag for this**. If you choose Windows, a grub chainloader command passes control to the Windows NTLDR, which handles the Windows boot sequence. Normally, you do need the boot flag set on the Windows partition for Windows to boot, unless you use the 'makeactive' command in grub.

I'm sorry if you know all this, but your posts suggest a confusion about what grub does.

A question: if you can boot both Windows and Linux from the grub menu, why are you concerned about who has the boot flag?


**Edit:** just noticed this:

> First time I boot into Windows it always boots into Windows after that.Do you mean that if you choose windows one time, it boots into Windows next time if you don't make a choice at the menu? Or do you mean that it boots into Windows if you choose Linux? If the first, it probably means you've got the 'savedefault' option in your grub menu.lst. If the second, I haven't a clue. You need to explain clearly what's going on.

---

