---
title: "Installing Ubuntu on a New Laptop"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Eomi on 2009-04-17
Hello,

I've been using Ubuntu in my (very) old laptop for a little over a year now, and I love it so much that I bought my new laptop OS-free so I can put Ubuntu on it.  I've run into a bit of a snag, though, and I'm hoping some one can give me some advice.

I've downloaded the 64-bit version of Ubuntu 8.10 and burned it to a disc, but each time I stick it in my new laptop and run the "check CD" test, I get a series of errors: 'buffer I/O error on device sr0' (which I know is the CD/DVD drive).  I've burned almost a half-dozen different discs - at as slow a speed as I can, and with as many different programs as I can - and the result is the same.  I also tried loading an older, 32-bit copy of Ubuntu 8.04 from a disc I know is good, and I got the same problem.

Is it possible my drive is faulty, even though this is a brand new cpu?  Or am I missing something in the BIOS that I need to tweak?  Or is this some kind of catch-22 (I need to install the OS to get the cd/dvd drive working, but I need the drive to install the OS), in which case I need an alternative way of getting the OS up-and-running?

I'm troubled that the I/O errors appear even with a CD I know is good.  Though I consider myself computer-savvy, and though I have installed Ubuntu on my old laptop and on a friend's desktop before, I have never done it on a brand new, out-of-the-box computer before.  So I don't know if there's some key, obvious step that I'm overlooking, or if I'm in a situation that requires manufacturer intervention.  My next step is to contact the manufacturer, but I want to make sure I'm not doing something wrong.

Thanks in advance.

---

### Post by lisati on 2009-04-17
You might want to check out your options for cleaning your drive's lens before writing it off, and check for fingerprints, scratches & other stuff on the CDs
 
Is your machine still under warranty? If you're experiencing difficulties with known good CDs you might be in with a chance of getting it fixed for little or no cost.

---

### Post by Eomi on 2009-04-17
Ok, so I've now tried downloading the latest LTS (8.04) and installing it instead.  I can run the CD check fine, and it reports that the CD is good, so it looks like I'm past the drive problem.

New problem, though, is that when I ask Ubuntu to boot (without installing), it gets part way and gives me a blank screen.  When I ask it to install, it gets most of the way through the loading screen, then kicks out the following error message:

code: f3 48 a5 89 d1 f3 a4 c3 66 66 66 66 2e 0f 1f 84 00 00 00 00
RIP [<ffffffff8035025b>] memcpy_c0xb/0x20
RSP <ffffffff80635d80>
CR2: 0000000039a847c0
---[ end trace bcd71ff2a4c9c2b5 ]---
Kernel panic - not syncing: Aiee, killing interrupt handler!

I've tried turning off acpi and acip, which google searches suggest as possible workarounds, but I get the same error.  I'm downloading the 8.04 alternate install now, to see if the text-based installer works any better for me.  In the meantime, any tips are appreciated.

Aloha.

---

### Post by ahbart on 2009-04-17
You should not try 8.04 (Hardy) on a brand new laptop and expect it to run properly. Try at least Intrepid, maybe the alternate version, or Jaunty (9.04). 
Though Jaunty is beta, it is very good in my opinion.

---

### Post by Eomi on 2009-04-17
Thanks for the advice.  I'm downloading Jaunty, too, to see if it runs better.  On the other side of things, would I be better off trying to run 32-bit instead of 64?  I've got 4 GB of RAM, and a processor that can do 64-bit, but maybe my compatibility will be better at 32?

Thanks again.

---

### Post by ahbart on 2009-04-18
Yhat is kind of difficult question. Because your laptop has a 4Gb memory, 64Bit Ubuntu would be better. But in my opinion 32 bit is 'still' lots easier to configure. Especially with some browser plugins and some software you'll need to compile. And sometimes there is even no package for 64bit.
32bit is easier but you might miss 1 gb of available memory then.

The general advise to use the server kernel to make advantage of all the 4Gb of ram is a little bit out of the question on a laptop I assume. Ubuntu should add 4Gb support to all there kernels now-a-days.

---

### Post by Eomi on 2009-04-18
Thanks for the advice.

I ended up installing Jaunty with no trouble at all (silly me, thinking I should go with an older version).  It's up and running, and I'm posting now for the first time with my new computer.  Obviously I haven't gotten to set things up to my liking yet, and I'm sure getting the most out of the 64-bit OS will be a learning process, but basic functionality is there, and my love affair with Ubuntu is as strong as ever.

Aloha.

---

