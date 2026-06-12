---
title: "Has ANYONE gotten an RF remote to work with Ubu?"
date: 2011-07-24
forum: Hardware
---

### Post by Mugsy323 on 2011-07-24
I have tried futility, since around Ubuntu 7.04, to get my "ATI Remote Wonder Plus" RF remote to work with Ubuntu.

I've found threads from people getting it to work with "*MYTH*buntu", but never straight Ubuntu. I've also read of people getting IR remotes working using LIRC, but never the "Remote Wonder Plus" (which is an RF remote).

I'm wondering if anyone has gotten *ANY* rf remote to work with Ubu? (preferably RW+, but knowledge of any other would be helpful.)

---

### Post by Mugsy323 on 2011-08-01
(Bump) Still hoping SOMEONE out there has gotten an RF remote to work with Ubu.

---

### Post by bonbasket on 2011-11-19
I got it working see my post you need to patch your driver or use the original ati remote wonder

[http://ubuntuforums.org/showthread.php?t=1875938&highlight=ati+remote+wonder+plus](http://ubuntuforums.org/showthread.php?t=1875938&highlight=ati+remote+wonder+plus)

---

### Post by Mugsy323 on 2011-11-20
> **bonbasket said:**
> I got it working see my post you need to patch your driver or use the original ati remote wonder

[http://ubuntuforums.org/showthread.php?t=1875938&highlight=ati+remote+wonder+plus](http://ubuntuforums.org/showthread.php?t=1875938&highlight=ati+remote+wonder+plus)

Thanks for the reply. I noticed that you refer to Mythbuntu, and I ran across the Mythbuntu kernel patch instructions back when I last worked on this. But I'm not using Mythbuntu (only standard Ubuntu), which is why I assumed it didn't work (even worse, it corrupted my installation so bad I was left with no choice but to reformat and reinstall.)

Are you using Mythbuntu instead of standard Ubuntu? I've seen plenty of people note success getting the RW+ to work with Mythbuntu, but not "Unbuntu" specifically.

I need to know before I go down that road again. Thx.

 -*- Mugsy -*-

---

### Post by Logan 1229 on 2011-11-20
I currently use a Go Plus Air Gyration Mouse (& keyboard) as a remote & it is RF.  Have used on all Ubuntu versions since 9.04 working flawlessly & I didn't need to add any additional drivers, etc, to get working.  

  Info on the one I use here:  [http://www.gyration.com/index.php/us/products/in-air-micekeyboards/go-air-mouse.html](http://www.gyration.com/index.php/us/products/in-air-micekeyboards/go-air-mouse.html)
  But if looking to buy, be aware the replacement battery packs for the mouse are not available in Canada, & nearly impossible to get from elsewhere.  Best bet is to have repacked by a battery rebuilder (or do yourself if you are good at soldering).

  I had previously used a RW but found it flaky at best.  The Go mouse is much better (works in air or on a desktop as a regular mouse).

  As for your RW, have you opened it up to ensure there's no internal damage?

---

### Post by Mugsy323 on 2011-11-20
> **Logan 1229 said:**
> I currently use a Go Plus Air Gyration Mouse...

  As for your RW, have you opened it up to ensure there's no internal damage?

I have a triple-boot PC with 32bit-Ubuntu-11.11, XP and Win7 all installed, which I switch between as needed. Win7 (64bit) is my primary OS.

My Remote Wonder works just fine with Windows. I would also like it working with Ubu as well. Since I already have this remote, which works great, I see no need to scrap it and buy something else just for Linux compatibility.

---

### Post by Mugsy323 on 2011-11-21
> **bonbasket said:**
> I got it working see my post you need to patch your driver or use the original ati remote wonder.[/url]

**Update:** Here is what I discovered for anyone that comes across this post in the future:

I was able to borrow and tryout an older Remote Wonder (the *[tubular style]("http://media.soundonsound.com/sos/sep03/images/pcmusician5.l.jpg")* remote) with receiver, on my PC.

My current *["Remote Wonder Plus"]("http://techreport.com/r.x/aiw-x1900/remote-wonder2.jpg")* is the flat "hour-glass" style with color function keys. Also different, the receiver on the older unit has a red power LED on it while the newer receiver does not.

In Windows, both Remotes work with both receivers interchangeably. But only the older (tubular) remote works out-of-the-box with unmodified Ubuntu.

Surprisingly, it didn't matter which receiver I used. Only the remotes themselves mattered. You would EXPECT that the USB receiver would be the most likely culprit, but it's not.

Why the older RW works in Ubu when the RW+ does not, regardless of the receiver used, is a mystery, and seems like it should be easy for the Developers to fix.

---

