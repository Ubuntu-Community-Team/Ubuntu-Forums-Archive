---
title: "IDE Question"
date: 2005-11-14
forum: General Help
---

### Post by justintime32 on 2005-11-14
I just recompiled my kernel so it has Software Suspend 2 support. It works really well, but It suspends kinda slow. It can write about 5 MB/s and read about 6. I read on the [HOWTO]("http://ubuntuforums.org/showthread.php?t=75443") that you're supposed to include appropriate support for your particular IDE, but I can't find mine there. I have an Intel ICH5 IDE, and can't find it on the list. Can someone tell me what I can do? Printout of 'lspci | grep "IDE"':```
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
```I have an HP Pavilion a250n desktop with Ubuntu Breezy.

---

### Post by darknuala on 2005-11-14
Have you tried enabling the dma setting?
I know there is an ubuntu link here, but here is the link from linuxquestions.org about enabling dma.

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363780](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363780)

---

### Post by Ryba on 2005-11-14
[quote=justintime32]I just recompiled my kernel so it has Software Suspend 2 support. It works really well, but It suspends kinda slow. It can write about 5 MB/s and read about 6. I read on the [HOWTO]("http://ubuntuforums.org/showthread.php?t=75443") that you're supposed to include appropriate support for your particular IDE, but I can't find mine there. I have an Intel ICH5 IDE, and can't find it on the list. Can someone tell me what I can do? Printout of 'lspci | grep "IDE"':```
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
```I have an HP Pavilion a250n desktop with Ubuntu Breezy.[/quote] I have no idea if this is relevant to you or not but I know just last week on a DELL computer my friend was reinstalling ubuntu to breezy (he doesn't believe in dist-upgrades cause he likes having clean systems???).

So anyway, I noticed during one of the restarts that the kernel was using his ATA 133 HDD at only ATA 33 speed. I was like wtf? So I looked in the bios and noticed he had hard drive compatibility mode on. I was like why are n't you using native mode? He said that he thought linux would be more stable on compatible mode. I flipped it to native and now his computer is blazing fast (at least it is when he does things like compiling and stuff that require lots of read/write to the disk).

Moral of the story, take a look at your bios settings and make sure you are not slowing it down at the bios level.

---

### Post by justintime32 on 2005-11-16
I think that I fixed it. I compiled the Intel PIIX driver into the Kernel, and now I get 50 MB/s read and slightly more write.

Yay Ubuntu!

---

