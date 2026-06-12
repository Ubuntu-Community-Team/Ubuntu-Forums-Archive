---
title: "CanoScan N670U problem"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by brainformat on 2007-08-05
fiesty recognizes it fine.
but, when i try to scan it kinda does that, but then gives me a black picture as outcome.
help pls!

---

### Post by mikeescott on 2007-09-03
I am having the same problem after upgraging to Feisty 7.04 last week. was working fine the week before. Is there a solution to this problem.

---

### Post by mikeescott on 2007-09-26
Is anyone using this scanner in Gutsy yet?




> **brainformat said:**
> fiesty recognizes it fine.
but, when i try to scan it kinda does that, but then gives me a black picture as outcome.
help pls!

---

### Post by mikeescott on 2007-09-26
> **brainformat said:**
> fiesty recognizes it fine.
but, when i try to scan it kinda does that, but then gives me a black picture as outcome.
help pls!


I got it working!!!!!

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

---

### Post by WOTHed on 2007-09-27
Was your solution to install sane-backends-1.0.18.tar.gz from source?

---

### Post by mikeescott on 2007-09-28
> **WOTHed said:**
> Was your solution to install sane-backends-1.0.18.tar.gz from source?


I downloaded it from the Sane website and installed from the Terminal.

---

### Post by rpaco on 2007-10-24
Upgrade to 7.10 Gutsy Gibbon.
Whoopee! Joy! Celebrations! 
At last**[SIZE=4] I can scan again!!!![/SIZE]**, nothing worked before, all of the work arounds just made the scanner emit a horrible grinding noise. I tried 
Scanbuttond, rolling back the scanlib, Xsane and just using the basic "scanner utility" nothing worked all the time I had Feisty Fawn.
But now I have upgraded to Gutsy Gibbon 7.10 I have scanned 20 documents in a row with no problems at all. The only drawback is the the upgrade took so long it could have been a MS Windows installation. Though to be fair it was actually only about 2 hours it took, as opposed to 3 days and 14 re-boots for that other lot.

---

### Post by sanitycheck on 2007-10-29
I can also confirm that the Canon CanoScan N670U does not work after an upgrade from Edgy 6.10 to Feisty 7.04, so this must be a bug.

---

### Post by bliffle on 2008-01-25
My old N670U worked first time I tried it on gutsy 7.10. Usually, the first trick with getting a scanner going is to find out how to "acquire" the scanner.

---

