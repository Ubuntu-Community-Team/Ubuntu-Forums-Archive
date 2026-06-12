---
title: "Um, where did XP go? -- Partitioning Woes"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by fathafiga on 2008-12-22
Hi,

I've used Ubuntu and Xubuntu here and there for just over a year now. I just attempted my first dual boot project on a Dell Latitude PP01X with Windows XP, and now I don't get an option to boot to XP.

I was having some trouble figuring out the partitioning during the Xubuntu installation, so I made a GParted boot CD to handle the partitioning. I used GParted to resize the XP partition to be half the size of the hard drive, and I created a new partition out of the other half for Xubuntu. This worked fine. I booted back to Windows, and the partition was the correct size, and all was well.

Then I went on with the Xubuntu install. I selected the unused partition for Xubuntu, and I chose to use the Windows partition as a Linux swap. I understood this wouldn't corrupt the existing instance of XP.

Xubuntu boots and works fine, but Windows seems to be gone. I've tried the boot menu and bios, and I can't seem to find an option to boot to XP. I've used GParted to change the partition flags to various configurations, but none seem to have made any difference.

(I realize this is as much an XP question as it is an Xubuntu question.)

Please help!

---

### Post by IamReck on 2008-12-22
You went wrong when you choose the windows partition as swap.  You aren't suppose to do that, swap should be a completely separate file space, with any file system.

I believe your Windows partitions is basically gone.  Sorry.

---

### Post by HSKR on 2008-12-22
I did [something like this]("http://ubuntuforums.org/showthread.php?t=1018248") as well, and ended up having to reinstall XP. I just hope that you had your files backed up. :(

---

### Post by fathafiga on 2008-12-22
> **IamReck said:**
> You went wrong when you choose the windows partition as swap.  You aren't suppose to do that, swap should be a completely separate file space, with any file system.

I believe your Windows partitions is basically gone.  Sorry.
Thanks for the quick reply.

If that's really the case, and if the devolopers of Ubuntu (and its variants) happen to read this thread, I'd highly recommend tweaking the partitioning feature in the install to make it easier to understand. I found it difficult to understand, even after a bit of research. Also, I don't recall being given any kind of formal warning during the install about partition swaps potentially wiping out entire operating systems. I guess I assumed that the installer would inform me if I was about to do something regrettable.

(Don't get me wrong; I take full responsibility for my actions, and I'm not trying to peg them on anyone else, but a little babytalking never hurt anyone :)

---

### Post by hyperdude111 on 2008-12-22
You went wrong because the swap is just hard drive space that can be used as extra ram if the ram runs out. If you turned the xp partition into swap it will have been re-formatted deleting all data.

If you need to recover lost data try this: 
Search "hirens boot cd" in google
It is Copy write Material so it is illegal, but it can be used to recover lost partitions.

Good Luck

---

### Post by fathafiga on 2008-12-22
It's sounding like my only potential way out of this would be to somehow turn the Linux swap off in the XP partition. Anyone know if this is possible?

In GParted, if you right click a partition, there should be an option to "Swapoff," but I'm not sure if that refers to undoing a Linux swap. Whenever I try it, it just give me an error: 

Then again, I don't have a full understanding of the whole "swap" thing. If making a partition into a Linux swap formats the partition, then I suppose I'm out of luck. However, if it doesn't format it, all the Windows files should still be there, so perhaps there's still hope.

---

### Post by fathafiga on 2008-12-22
Thanks for the info, everyone. I guess this case is as good as closed.

Fortunately, there are no personal files on this computer, but it belongs to my work, so I'll have to contact home office to get a new XP image for it. (It's more annoying than anything; I won't get into trouble.)

---

### Post by HSKR on 2008-12-22
> **fathafiga said:**
> Thanks for the info, everyone. I guess this case is as good as closed.

Fortunately, there are no personal files on this computer, but it belongs to my work, so I'll have to contact home office to get a new XP image for it. (It's more annoying than anything; I won't get into trouble.)

That's good to hear. Good luck.

---

