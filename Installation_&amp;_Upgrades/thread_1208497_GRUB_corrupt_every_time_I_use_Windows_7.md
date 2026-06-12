---
title: "GRUB corrupt every time I use Windows 7"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by simplysped on 2009-07-09
I have Ubuntu/Windows 7 on my laptop, lately for some reason grub has been corrupting it self every day. I'll turn on my laptopb after being on windows 7, and then it goes from Bios to grub screen, it says loading grub 1.5, and then it restarts and does it all over again. It wil loop like ths forever until I boot into Ubuntu live and set grub to (hd0). 

When I do the fine stage1 command, I see that grub is installed on hd0,4, then I just run setup (hd0) and the problem is fixed.

Does anyone know why the grub is getting corrupt every time? My partitions are setup like this: swap|windows|ubuntu|files.

Thanks :(

---

### Post by InnocentBystander on 2009-07-09
I'm having the exact same problem.  It's not happening *every* time I reboot, but it's happened twice now in three weeks.  From the order of your drives, I'm guessing you also have some sort of Dell laptop?  Mine's a Vostro 1720.

But, yeah.  Reboots at "loading GRUB" and setting it up again from a liveCD fixes it.  It's certainly annoying.

---

### Post by philcamlin on 2009-07-09
its a beta os its not perfect thats why its for "testing" and thn you file a big fix thing :P

i wouldent use 7 till its out

---

### Post by InnocentBystander on 2009-07-13
@philcamlin:

Do you really want to bet on Microsoft fixing a problem with Windows 7 that causes hardship for people wanting to dual-boot with Linux?  That's a laugh.  I'd give decent odds that the "bug" is there on purpose... and I certainly wouldn't expect to see it fixed unless we're the ones to fix it.

---

### Post by Mark Phelps on 2009-07-13
Vista was known to cause this problem; looks like Seven may be repeating the same thing.

See the link below.  If this is the same problem, this will fix it:

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

---

### Post by junxuan on 2009-07-13
hmm windows 7 and grub works fine with me. Which release of windows 7 are you using?

---

### Post by InnocentBystander on 2009-07-13
@Mark Phelps-

The description on that page does sound pretty much like what's happening with me.  I'll give it a shot!  Thanks.

@junxuan-

It's build 7100.

---

