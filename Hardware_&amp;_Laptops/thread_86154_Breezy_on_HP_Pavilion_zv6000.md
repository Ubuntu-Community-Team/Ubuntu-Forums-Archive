---
title: "Breezy on HP Pavilion zv6000"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by Crazkid4eva on 2005-11-04
Hello, I have been trying to install Breezy on my HP, should I use one of the customized versions for HP, I have an AMD 64 Chipset and when I tried the install I can't get past partioning my hardrive to install Breezy, it just doesn't let me resize the harddrive to create additional space for a partition.

Thanks.

---

### Post by Salane on 2005-11-25
[QUOTE=Crazkid4eva]Hello, I have been trying to install Breezy on my HP, should I use one of the customized versions for HP, I have an AMD 64 Chipset and when I tried the install I can't get past partioning my hardrive to install Breezy, it just doesn't let me resize the harddrive to create additional space for a partition.

Thanks.[/QUOTE]

it sounds like a irq lockup. Try
 linux pci="noirq"
when starting install

---

### Post by almahtar on 2005-11-26
Hey I have a zv6000 as well.  I'm running the amd64 Breezy.

It's a bit tough getting everything working.  If you have some knowlege of Linux or a lot of patience (having both would be nice), Breezy is for you.  There are a few threads on this board that are solely about installing Breezy on the zv6000.  I kid you not: whole threads just about it.

My advice to you is this: go read some of those threads.  If the problems those people are reporting look like something you can take on, Ubuntu is worth it.

I'm going to give 32 bit Breezy a shot right alongside the 64 since support for 64 bit processors still has a few gaps (I miss my zsnes!!!).  Did that answer your question sufficiently?

---

### Post by greenerpole on 2005-12-09
Crazkid4eva : 
Just like you, I have a zv6000 and try to get Ubuntu Breezy installed. 
Just like you, it refused to resize the C: partition where the native WinXP was installed.

What I did is pretty brutal : from the WinXP CD, I repartitionned (20Go/60Go) and reinstalled a WinXP (as i need something operational while i try to get Ubuntu installed) on the smallest partition. Then rebooting on Ubuntu, you can install it on the unused partition... or try... I am blocked at the "copying remaining packages" step, as the computer systematically freezes up (tried 10 times in a row).

---

### Post by walterpontes on 2005-12-30
Hi everybody. I have the zv6100 and I had a problem installing Linux. I had the same problem you wrote. I solved that this way: On Windows XP I ran scandisk then I installed Partition Magic 8, resized the 100 GB Disk. The installation was succesfull after these steps. Now I have problems with the video and the wireless. I can't compile ndiswrapper. I have the 64 bits kernel installed. Is it a better choice installing the 386 kernel instead?

Regards,

Walter

---

### Post by dsierpin on 2006-01-04
Hello-

I've got a zv6000, and I've been trying to get stuff going for awhile.  I've pretty much given up on the modem, the guy that was helping me from linmodems.org stopped returning my e-mails :( .

As for the video, go [here ]("http://ubuntuforums.org/showpost.php?p=423584")first, and if you can't get that to work, go [here]("http://www.ubuntuforums.org/showthread.php?t=75378").

Most of the major problems I had with installation I took care of by entering:

```
linux vga=771 noapic nolapic
```

at the boot prompt, and after installation (when you can't get to the login because you have the pretty white and blue hatched lines) I rebooted in recovery mode and edited /etc/X11/xorg.conf by adding the line:

```
Option     "NoAccel"
```

In the video card section.  It's a bit of trouble to get things in order, but I guess that's what we get for buying computers that are designed specifically to run with windows.  Anyway, the trouble it takes is well worth it, and you learn quite a bit along the way.

---

### Post by Ch33zm0ng3r on 2006-01-10
dsierpin:

It looks like my problems is what you were talking about.  I've gotten just as far as getting to the blue and white hatched lines.  How exactly would one boot into recovery mode to edit the xorg.conf file?

---

### Post by elephanthunter on 2006-01-10
It should work when you select the "Recovery Mode" option on the GRUB menu with no additional flags.

---

