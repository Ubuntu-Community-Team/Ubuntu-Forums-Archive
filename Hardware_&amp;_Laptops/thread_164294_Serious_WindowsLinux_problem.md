---
title: "Serious Windows/Linux problem"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by Parag0n on 2006-04-22
Okay a while back I tried to do a dual-boot without reading anything. I'm good with computers but fairly new to Linux. It didn't exactly work but my computer and Linux worked fine. 

However, I tried to reinstall Windows and the Windows CDs (I have two Xps, Home and Professional) will _not_ boot up when I restart. They will however run in my other computer so I know the discs work.

For four days I've had GRUB error 17 and I've been working on it, and I've finally gotten that fixed. Now the problem I'm having is again, not being able to boot Windows.

I love using Linux it just doesn't work with Steam for Counterstrike as well as I hoped it would, so I have to reinstall Windows so I can run my server.

I've tried partitioning in multiple times in multiple ways using the Linux CD although I've been doing this all with my own knowledge and google.

So here I am now after searching for hours and not finding the answer needed.  If someone please knows what the problem is and could tell me how to fix this it would be greatly appreciated.

Thanks.

---

### Post by cilynx on 2006-04-22
Ok, so you're trying to get a straight WinXP / Ubuntu dual boot setup, right?

You're saying that the WinXP install CD won't boot?  Or just that the WinXP system installed on your hard drive won't boot?  If the latter, does it show up on your Grub menu and not work, or does it not show up on the menu?

Basic details of your setup as well as basic details of your optimal working end system would be appreciated.

---

### Post by Parag0n on 2006-04-22
No I would like to completely erase Linux and install WinXP instead. And WinXP isn't already on the computer, the CD itself will not boot.

The CD does work though.

---

### Post by cilynx on 2006-04-22
Ok, I follow.  

The problem isn't with Linux.  Linux can't make your WinXP CD not boot.  

You checked the disc in other machines, so you know that works.  Did you check the machine with other bootable discs?  I would guess that booting from the CD is disabled in BIOS or some such.  Check that and get back to me.

To play with partitioning, you may want to look into the gParted Live CD.  It's a nice graphical partitioning tool.

Also, this may be of interest to you: [http://www.ubuntuforums.org/showthread.php?t=159420]("http://www.ubuntuforums.org/showthread.php?t=159420")

---

### Post by Parag0n on 2006-04-22
BIOS is configured correctly, it boots the Linux CDs. I've also tested the WinXPs on other PCs and they work.

---

### Post by Parag0n on 2006-04-22
Nevermind I finally got it to work.

Thanks though.

---

### Post by cilynx on 2006-04-22
If I may ask, what was wrong?  Don't want to dead-end any Googlers out there...

---

### Post by Parag0n on 2006-04-22
Good idea.

To be honest though I'm not entirely sure.


All I know is that I would put in the CD and then restart, but it wouldn't boot the CD.

So instead when the computer was booting I quickly opened and closed the tray to make the CD re-load and that seemed to work.

Weird problem..weird solution.

Pisses me off that I've been working on this for hours..reformatted probably 20 total times..Messed up GRUB..took 2 days to do one install because GRUB was effed..and all I had to do was to reload the CD when the computer was booting.

---

### Post by cilynx on 2006-04-23
Always seems to be something dumb.  I hope things smooth out for you from here.

---

