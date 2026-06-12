---
title: "Slow, &quot;Failed to Initialize HAL&quot; Message, &amp; More..."
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by cg333 on 2006-04-16
Good day,
Running a dual-boot Alienware Sentia Laptop w/ a 1.8Ghz Intel & 2GB Memory, Ubuntu 5.10 & WinXP Pro.  Using Grub 0.95 & Ubunutu kernel 2.6.12-10-386, .  

Current times:

XP from Grub boot-time to Login: 17 sec.
From login to usable gui: 28 sec.
Total time: 45 sec.

Ubuntu from Grub boot-time to Login: 16:41
From login to usable gui: 3:58
Total time: 20:39

As you can see, over 20 minutes is a little crazy.  After a couple minutes later, a "Failed to Initialize HAL" message appears.  Also once in the gui, everything runs slow, really slow.  Searching the forums, there is no definitive THIS IS HOW YOU FIX THAT explanation, so do to that I am posting here.  I will make the assumption that fixing that message will also help in fixing whatever is causing a 20min. boot-up. _ I have followed the pinned post to disable several start-up services. _ This is most likely two different issues.  I have attache several logs, feel free to lend advice and ask for anything additional that is needed to diagnose/fix these 3 issues.

Goals: 1-Get boot-time down to a few minutes or faster  (c'mon an MS product is beating a much better product, this needs to be fixed)
         2-Speed-up the GUI interface as clicking anything runs slowly and opening anything is also slowly
         3-Fix the "Failed to Initialize HAL" message (probably related to slow issue)

Take a look at the logs below, thank you.

---

