---
title: "Bluetooth mouse pairing problem"
date: 2010-01-04
forum: Hardware
---

### Post by ectospasm on 2010-01-04
I recently installed both Windows 7 and Ubuntu Netbook Remix 9.10 in dual-boot configuration, over a Windows XP and UNR 9.04 installation.  I can get my Microsoft Bluetooth Notebook Mouse 5000 working in both Win7 and UNR9.10, but if I swap from Win7 to UNR or vice versa, I have to put my mouse in discoverable mode before it starts working again.  Suprisingly, going from UNR to Win7 is more difficult, because I have to totally remove the mouse from the software installation and pair it again, whereas I just need to reconnect the mouse going into UNR.

It used to work flawlessly in WinXP and UNR9.04, once paired with both operating systems the mouse didn't need to be paired again, regardless of which OS was used last with it.  Also, if I reboot the machine and go into the same OS, everything works fine.  I figured I'd have more luck asking here rather than on the Windows forums, and ironically it does seem that Win7 has more trouble connecting to the mouse after UNR uses it than the other way around.  Any ideas?

---

### Post by ectospasm on 2010-03-20
Bump.  This is still an issue.  It never seems consistent, sometimes in UNR all I have to do is try to use the mouse, UNR asks for a pairing code, and it works.  The same process occurs in Win7, but it has only succeeded in working once, and I can't figure out how to get it working.  

This is the only issue which plagues me now on this machine.

---

### Post by LotusEffect on 2010-04-21
Bump

I've *exactly * the same problem. I've Ubuntu 9.10 and Win 7 installed in dual boot and I'm using a Microsoft bluetooth 5000 mouse.

---

### Post by ectospasm on 2010-04-21
> **LotusEffect said:**
> Bump

I've *exactly * the same problem. I've Ubuntu 9.10 and Win 7 installed in dual boot and I'm using a Microsoft bluetooth 5000 mouse.

I've resigned myself to doing what I can for this, usually involving removing the mouse from software and re-pairing it.  Of course, in UNR it seems to work OK most of the time inputting the pairing code.  It has happened a couple of times where Windows didn't need the re-pairing, one time the PIN code actually worked rather than throwing the error message, the other time it just worked automagically.  But the norm is to delete the mouse from software, put it in pairing mode, and reconnect it.  That I suspect will be the only workaround until Microsoft fixes their software.

---

### Post by LotusEffect on 2010-04-21
> **ectospasm said:**
> I've resigned myself to doing what I can for this, usually involving removing the mouse from software and re-pairing it.  Of course, in UNR it seems to work OK most of the time inputting the pairing code.  It has happened a couple of times where Windows didn't need the re-pairing, one time the PIN code actually worked rather than throwing the error message, the other time it just worked automagically.  But the norm is to delete the mouse from software, put it in pairing mode, and reconnect it.  That I suspect will be the only workaround until Microsoft fixes their software.

Yeah 90% of the times I enter the pairing code (0000) in win7, the system just vomits an error message saying there were "problems" and that I should contact the administrator or something like that lol...

In Ubuntu IIRC I just have to press the button under the mouse. But it's still annoying.. my friends mice work perfectly when switching from one OS to another.

Anyways if I can't resolve the problem I might just buy a standard wired mouse @ $10...

---

### Post by JesperSP on 2010-09-29
I'm having the same problem with my Nokia N82. It works fine when just paired in WinXP SP3, but if I pair it under ubuntu 10.04 it stops working under XP. I have previously had my phone paired to several computers without any problems, so my immediate thought is that the problem is due to both operating systems using BT hardware with the same MAC address, and this confuses the N82 phone to think it's the same protocol for each system. If it was possible to have the ubuntu reconfigure the MAC address of the BT hardware this issue would go away..

Cheers,
Jesper

---

### Post by ectospasm on 2010-09-30
> I'm having the same problem with my Nokia N82. It works fine when just paired in WinXP SP3, but if I pair it under ubuntu 10.04 it stops working under XP. I have previously had my phone paired to several computers without any problems, so my immediate thought is that the problem is due to both operating systems using BT hardware with the same MAC address, and this confuses the N82 phone to think it's the same protocol for each system. If it was possible to have the ubuntu reconfigure the MAC address of the BT hardware this issue would go away..


I filed a bug with Microsoft regarding this, since it's an OS level bug in Win7.  I had no problems dual-booting with XP, so you should probably file this under a different forum post.

---

