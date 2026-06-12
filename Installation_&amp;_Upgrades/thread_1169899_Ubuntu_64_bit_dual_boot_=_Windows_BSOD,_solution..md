---
title: "Ubuntu 64 bit dual boot = Windows BSOD, solution."
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Hutchewon on 2009-05-25
System setup:
EVGA 680i Mother board
Intel core duo E6600 cpu
2 Western digital 500 GB hard drives
Widows XP Pro
Ubuntu Jaunty Jackelope 64 bit

Windows XP Pro was the existing OS, tried to setup from graphical interface, upon reboot Ubuntu worked fine except sound did not work. When I restarted and attempted to run Windows, I got a Blue Screen of Death that flashed so fast I was unable to read it. I tried reinstalling Ubuntu, thinking it was wiping out the last install. Attempted that until the disk I had designated for Ubuntu was full. Some kind soul on the IRC channels, talked me through most of it, but gave up when the disk got full.

Final solution:
Booted from the Windows XP Pro CD. When I got to the welcome screen I pressed "R". When I got a DOS prompt, I typed "chkdsk /p". When that was finished I exited the Window CD and was able to boot Windows normally,

Another possibility if that fails:

The site that I got that tip from also suggested typeing "fixboot" at the dos prompt spawned by the Windows CD boot, then answering "Y" to that question and hitting enter. I did not try that, because I suspected it might mess up grub, but if you are desperate to get your windows partition functioning and the first step doesn't work. Try this step. The worse that can happen is that you will lose the new Ubuntu partition too.

---

