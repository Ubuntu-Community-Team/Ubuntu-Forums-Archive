---
title: "ubuntu karmic dual boot with windows 7 grub error"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by sakekasi on 2009-11-03
i have a dell studio 1555 with pre-installed win7, and when i dual booted ubuntu along with it, after a few restarts, i got this error...

Grub loading.
cannot find character 'k'
Aborted.

and something about PXE.

note that this is not the exact output.

i believe that this happened after i used win7 in a dual-boot configuration.

i know that i can fix this by reinstalling ubuntu, but i dont want to constantly reinstall.

please help.

---

### Post by sliketymo on 2009-11-03
Good info here:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by sakekasi on 2009-11-03
i have win7 installed first

---

### Post by sakekasi on 2009-11-07
i found out that i can temporarily fix the issue by reinstalling grub2 from the ubuntu livecd, but when i start windows again, it kills grub again.

---

### Post by Zorrothustra on 2010-03-14
Sakekasi,

Did you manage to fix this issue ? Working on Dell Studio 15 as well. I have exactly the same problem as you described and it drives me mad. I went to this thread [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) where I asked if they could assist me (#199 on page 20). But maybe you can help ? 

Thanks,

Z

---

### Post by oldfred on 2010-03-14
Have you checked these sites. HP & Dells have software that can cause problems.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.

I saw your results.txt in the other thread. It looks like you did not repair your install but just reinstalled it.

---

### Post by Zorrothustra on 2010-03-16
Thanks for your suggestions. I finally managed to get it fixed.

Guess you might be right about Dell software having something to do with the Grub-rape. 

This is how I fixed it. Since it was getting far too technical for me I did the following in that exact order (probably you can skip a few, but anyway). NOTE: I didn't have any personal documents on my computer !

1. reinstall Windows 7 on the NTFS partition
2. install Easy BCD in Windows
3. install 9.10 after cleaning up the old Ubuntu partitions (manual partitioning) and putting grub in my clean ubuntu installation (in my case, the sda4 partition).
4. Started up in Windows (didn't have a choice anyway, no grub or EasyBCD showing up) and then configuring EasyBCD to point it to the sda4 Ubuntu partition.
5. Reboot. If I chose Windows in EASYBCD-screen at startup, no prob, it would start. If I chose Ubuntu I had a Grub command line where I didn't know what to do. ](*,)
6. I had a big beer and a cigarette 
7. I reinstalled (again !) Ubuntu 9.10 with manual partitioning and decided to put grub on the MBR.
8. It works: Grub at startup, choosing Ubuntu working perfect. Choosing windows shows first the Easy BCD screen, but whatever.

Maybe it was the Dell software that overwrote the MBR, no idea. Anyway it works and I don't really need EasyBCD for it.

---

