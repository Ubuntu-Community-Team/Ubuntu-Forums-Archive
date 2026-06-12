---
title: "[SOLVED] What's the difference between reiserfs and ext2/3"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by hatten on 2009-01-02
Earlier when my brother installed ubuntu for me he installed it on a reiserfs partition, now i wanna do a new, clean installation and delete my old windows partition. I have read about reiserfs and ext2/ext3 but i haven't really found out what to use for / and /home. What's the difference and which should i use?

---

### Post by tommcd on 2009-01-02
Here is a brief article explaining the different file systems:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
And here are some interesting benchmark comparisons of the different file systems:
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)
Reiserfs and XFS are a bit faster than ext3 performance wise. Ext3 is probably the safest and most reliable against data corruption; but it is a bit slower. Personally, I have always used ext3. I did use XFS once or twice with Zenwalk linux. I can't say I saw much of a performance increase though from what I remember.

 I think Ubuntu 9.04 will offer ext4 as an option in addition to the others.
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

---

### Post by hatten on 2009-01-02
shortie: reiserfs is faster and ext3 is safer. thanks

---

### Post by RansomStark on 2009-01-02
I wonder how/what the arrangements are for future development/maintanence of the ReiserFS since the lead developer has been imprisoned!

[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

Hans Thomas Reiser (born December 19, 1963) is an American computer programmer, the owner of Namesys, and the primary developer of the ReiserFS and Reiser4 computer filesystems. On April 28, 2008, he was convicted of the first degree murder of his wife, Nina Reiser, who disappeared in 2006.

I choose ext3!

---

### Post by Copernicus1234 on 2009-01-02
> **RansomStark said:**
> I wonder how/what the arrangements are for future development/maintanence of the ReiserFS since the lead developer has been imprisoned!

[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

Hans Thomas Reiser (born December 19, 1963) is an American computer programmer, the owner of Namesys, and the primary developer of the ReiserFS and Reiser4 computer filesystems. On April 28, 2008, he was convicted of the first degree murder of his wife, Nina Reiser, who disappeared in 2006.

I choose ext3!

That Wikipedia entry was interesting... almost like a movie plot. The guy even bought books about murder investigations, trying to avoid to get caught...:)

---

### Post by hatten on 2009-01-02
> **RansomStark said:**
> I wonder how/what the arrangements are for future development/maintanence of the ReiserFS since the lead developer has been imprisoned!

[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

Hans Thomas Reiser (born December 19, 1963) is an American computer programmer, the owner of Namesys, and the primary developer of the ReiserFS and Reiser4 computer filesystems. On April 28, 2008, he was convicted of the first degree murder of his wife, Nina Reiser, who disappeared in 2006.

I choose ext3!
yeah, very interesting. I hope he is allowed to code in prison:D

but if the developers of reiserfs are murderer i don't really trust them my computer, what if they slaughter it!?!. j/k

---

### Post by Sef on 2009-01-02
The charge was reduced to second degree murder, which he pled guilty to.   In return, he lead authorities to Nina's body.

From [Wiki]("http://en.wikipedia.org/wiki/Hans_Reiser"):

> On August 29, 2008 he pleaded guilty to a reduced charge of second degree murder as part of a settlement that included identifying the location of Nina Reiser's body.

---

