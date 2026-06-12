---
title: "Live CD + NTFS"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by BitRogue on 2009-04-23
My apologies if the wrong forum, but since there is no category for 'Live CD' or 'disaster recovery', I figure the next most applicable section is this one.

I was 'almost' the hero on the team the other day when one of the (lady) consultants on our project came up and asked if I could assist her in getting her data off her (Windows) laptop so it could be rebuilt. It transpired that something had gone wrong and she couldnt boot and was really worried she wouldnt see her data again.

No worries. I have my trusty bootable USB flashdrive with an Ubuntu 8.10 Live CD on it. This thing can do ANYTHING.
Boots up fine (more life than she's seen on that laptop the whole day, her eyes are shining and shes starting to sing praises to the great god of Linux). Connect the backup external hard drive. Open up Nautilus and try to mount the internal hard drive. And THATS where it all went wrong. A huge error box is displayed about how the last useage of the drive wasnt shutdown cleanly, and some sort of convoluted error dump which mentions NTFS a couple of times. (Because it was an NTFS drive) 

So Im curious, WTF?!?! Do Ubuntu Live CDs no longer contain NTFS kernel drivers? This is one application I thought it would be imperative that would include all manner of file system compatibility, even if it was just read only.

---

### Post by yeats on 2009-04-23
You have to force the drive to mount when this happens.  You might benefit from reading this post:

[http://ubuntuforums.org/showthread.php?t=855081]("http://ubuntuforums.org/showthread.php?t=855081")

---

### Post by Sef on 2009-04-23
> So Im curious, WTF?!?! Do Ubuntu Live CDs no longer contain NTFS kernel drivers?

Did you install NTFS-3g?  If not, Ubuntu will not be able to read NTFS.  

If not, then do this:

Applications > Add/Remove > Show: All Available Applications > Search: NTFS > check box next to NTFS Configuration Tool (top option) > apply changes > apply > close

---

### Post by BitRogue on 2009-04-23
No, I didnt install anything extra. I spend most of my life avoiding Windows, and especially NTFS since its never been Linux friendly. So I kinda expected the LiveCD standard boot to already be feature complete in this area (since Live CDs are targetted at people who want to play with Linux before they commit, it might just be a good idea that those same people can see their NTFS drives before hand)

I will try this again on my work laptop running M$. It will be good to know as these kind of situations seem to come up more often than youd believe.

Thanks for the replies.

---

