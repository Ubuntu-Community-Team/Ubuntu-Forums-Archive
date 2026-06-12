---
title: "[GRUB]One day all of this one model broke grub!"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by Serpreme on 2009-10-01
Hello!
I work at a company that has many different models throughout its establishments. 

We currently have roughly 50 HP D510s. Randomly since this last weekend, they have started to fail to load through the stages of grub correctly. We see Stage 1.5 on the screen briefly before it reboots back to bios.

You can dd if=/dev/zero out the hard drive, re-image the computer and upon a few reboots, they will start this problem again.
But some will keep working for a whole day or more, and then randomly start this problem.

We've tried dd if=/dev/hda of=/mnt/usbdrive bs=512 count=1 and then putting that file back down on a same model with same hardware and same image.

It appears when we join the domain this causes the problem also. 

I was wondering if anyone had any ideas on what we can try? I'm going to swap out the /boot/grub directory from a working computer into a broken one and hope it works, even if temporarily. Then slowly replace the files until we find the broken one.

I'm also thinking about taking some images of the first couple sectors during different stages of the process, and doing a compare difference on them.

But we're all really stumped and its really odd. This is the only model doing this. 

Thanks for any help! And thanks for taking the time to read this whole thing.

---

### Post by Serpreme on 2009-10-02
Bumpity bump1

---

### Post by oldfred on 2009-10-02
I am suspicious that it is not Grub? Did you roll out new software or an update that takes more memory, or fill up the HD with log files, or a power surge that affect a group of PC's.

I would have thought grub could not cause a HW issue but on another thread someone's PC lost it's CD with grub and it was a known bug with only a few Lenova PCs. The work around was to disable the CD in bios then grub could find it.

---

### Post by Serpreme on 2009-10-03
> **oldfred said:**
> I am suspicious that it is not Grub? Did you roll out new software or an update that takes more memory, or fill up the HD with log files, or a power surge that affect a group of PC's.

I would have thought grub could not cause a HW issue but on another thread someone's PC lost it's CD with grub and it was a known bug with only a few Lenova PCs. The work around was to disable the CD in bios then grub could find it.

We do have a client on each computer that will update the PC's. Were checking to see if a update was pushed out around the same time.

The strange thing is that hardware drivers wouldn't just magically change themselves. Neither in our linux partition we use a imaging software nor windows side.

So something else has to be to blame. Either some weird program that no longer functions properly  or potentially anything i suppose.

I'm taking this chance to learn Grub very thoroughly.

Is there any tests we can do to verify grubs health or potentially step grub through its paces?

Like use SuperGrub to launch stage 1 and have the clients 1.5 step in to see if it balks.

Thanks for any thinking power you guys put forth. Nothing is crazy.

---

### Post by oldfred on 2009-10-03
I do not know if it will help but the bootinfoscript is useful in knowing what is booting where. It is more for when it does not work at all.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
This will create a RESULTS.txt file in the same directory.

---

### Post by Serpreme on 2009-10-03
Awesome. I'll do that first thing in the morning.

---

