---
title: "Single Boot Loader"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by jfreak53 on 2009-08-03
Ok searched everywhere for this and cannot find it.  I don't want to DUAL BOOT.  Well sort of.  I currently have two disks, one two windows installs and one ubuntu.  My problem is Grub is giving me major problems, error 18 at erradical times!  I'm tired of it.

So I don't want to dual with lilo or Grub anymore.  I want to install XOSL on the main hard drive windows drive, and some small bootloader in the MBR of the second drive for XOSL to boot, since it won't do linux directly.  But I don't want to use Lilo or Grub as the small bootloader in the MBR of the second drive.  Grub gives errors, error 18, probably because of drive setup or Bios, don't know don't care, too much work.

Isn't there some straight forward booter for linux that doesn't multiboot but just sits in the MBR and without a menu just boots to linux?  There has to be something.  I could use lilo if nothing else exists, and just place it with a single option on the MBR of the second drive, but I don't wish too, there has to be something smaller and straight forward sort of a Bootloader for linux?  I mean I haven't used Lilo since my FreeBSD days, HAHAHA, 2.2.7 to be exact!  Long, Long Long time ago.  I upgraded to 3.0 and I thought I was in heaven ha ha ha :o  Aww the old days.

Any ideas?  Thanks in advance for the help.

---

### Post by presence1960 on 2009-08-03
[don't know , don't care]("http://www.gnu.org/software/grub/manual/grub.html")
[URL="http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors"]
Hint[/URL] this will save you some time! Scroll down to error 18

usually error 18 means your BIOS cant read past a certain point on your disk and unfortunately your boot files are located past that point. if that is indeed the case it won't matter what bootloader you use. You are going to have to create a boot partition within the boundary that your BIOS can read. I think you may want to know/care.

I am being sarcastic for a reason. In case you haven't noticed your thread was started 5 hours ago and nobody but myself has replied. I have noticed quite a few knowledgeable members on here during the time since you have posted. I think the reason is in the attitude you have in asking for help. I was tempted not to respond because as you said you don't know and don't care. But I don't wish anyone to have a rig that can't boot. My advice is "if you don't want to hear the answer, then don't ask the question." Do you grasp where I am coming from?

---

### Post by jfreak53 on 2009-08-05
Thank you for your comments.  I have read this before on what error 18 actually is:

```
18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 
```

Unfortunately in all my searching no one, and I mean no one in any forum or any site could answer this question as to HOW EXACTLY TO FIX?  All they kept saying was that this was the problem, hey it's a limitation of the Bios, nothing else ever.  So I have resorted to saying fine, it won't work, grub is a mess let's try something else.  Hey at least I'm willing to try instead of working with just the bios press F8 to select boot device, come on here.

Now I do have to say, other loaders work.  Plus this is not constant, this error comes and goes, some times it works some times it doesn't.  So I'm not the expert but doesn't that mean it's erradical?  Most forums and answer, even on this forum, I found for error 18 said, it was erradicle and not worth the try to fix, and of course they wouldn't say why.

Other loaders do work, ones that sit in the same area that Grub does, even LILO I had working for awhile.  But I don't like LILO plus I like to play.  So after trying many I stuck with XOSL, even though it can't boot the kernel directly.  I installed a single boot option LILO on my second drive MBR.

Mainly the reason of this thread is I'm actually curious, is there a simple bootloader for linux?  Or I read somewhere that you could write the kernel directly to the MBR of a floppy.  Is anything like this possible with the MBR of the drive?  I'm really just tired of errors and I want to play a bit, so is there something like this for linux?

Again thanks for the comments and advice, but I'm really just tired of errors and no one seems to have an answer as to, OK here is how you fix error 18 on Grub.  If someone had this I would try to fix, I love grub!

And I honestly don't see where an attitude was in the first post, the only part I said anything remotely about was, don't know don't care.  And that should be understandable, it's a simple comment of frustration, we shouldn't all be getting offended by comments not directed at anyone at all but at my computer, aren't we adults?  Just a thought.

---

### Post by presence1960 on 2009-08-05
the fix is to install Ubuntu with a separate /boot partition at the very beginning of your hard disk. This will keep the boot files directly within the readable area for your BIOS. Unfortunately that is a BIOS problem not a GRUB problem. see [here]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall") to try without reinstalling.

---

### Post by jfreak53 on 2009-08-05
Thank YOU!  This info I did not find before.  Unfortunately I don't think I'm going to be doing it.  I have experience resizing partitions and in that experience I have found if you do it at the end of the partition, in other words, shrink it from back to front, it works.  But at the beginning I have found many problems, like loosing files, and I don't want to have to re-install my ubuntu.  So for right now I think I will stick with what I have running.

QUICK IDEA THOUGH!  You can tell me if this would work.  Could I not boot using live CD, make an image of my ubuntu partition, a complete image, and save that image to another partition.  Then re-partition everything, this time the right way.  Then just still in live CD paste the image over the partition?  I would still have to change the config files, but I save myself from breaking my partition and loosing everything.

I guess I could always run remastersys and just do a complete backup then re-install, but that's a lot more time that I don't have for such a simple problem that is already fixed using other means.

My question still remains though.  Is there some sort of simple bootloader for linux, or a way to put the kernel directly in the MBR.  I don't like the second idea since when you upgrade kernels I would have to do it again I would think.  Anyways I'm just curious now.

But thank you for the help.  This is all I was looking for.

---

### Post by presence1960 on 2009-08-05
you could use remastersys, clonezilla, partimage or [PING]("http://ping.windowsdream.com/")

---

