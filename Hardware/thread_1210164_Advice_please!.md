---
title: "Advice please!"
date: 2009-07-11
forum: Hardware
---

### Post by sub_acoustic on 2009-07-11
Hi,

My laptop freezes at random times.  

It first started about a month ago, and after about half an hour it would freeze (display still on move still moving but not able to click anything) when using 8.10 and while I was using Amarok or VLC.  

I assumed this was a software problem so I decided to upgrade to 9.04.  The freezing problem became much worse, often freezing after a couple of minutes on a whole variety of tasks.  

I'm now back to 8.04 which seems to be running better but these inconvenient freezes keep coming along about once an hour - often with a high processor load - like when copying many files.  

So I began to think that this may be a hardware problem.  I've run all the RAM and Hard Drive tests and they say there's no problem (though my drive is 5 years old and has been used a lot).  Any advice would be greatly appreciated!

---

### Post by kixome on 2009-07-11
Possibly overheating?

---

### Post by sub_acoustic on 2009-07-11
It's not overheating - when 9.04 was installed sometimes it would freeze shortly after a cold start & the fans are working fine.

---

### Post by sub_acoustic on 2009-07-15
Cross-posting this from [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1135055&page=54](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1135055&page=54)
as I'm certain this is a hardware issue

Well back to 8.04 and the problem continues, (I've previously been on 8.04 and 8.10 with no problems in the past).

So my thoughts are that maybe its

- some update included in 9.04 and 8.10 that was also applied to 8.04 LTS
- a hardware issue (though ram and hard disk tested okay)
- a power issue (though it seems to happen either on battery or adaptor)
- a wireless thing (though it's also happened when on a wired connection)
- some BIOS thing (though I've altered nothing)
- some kind of conspiracy?

Freezes generally seem to happen with high CPU loads, though that has never happened before, and sometimes it freezes when not much is happening.

---

### Post by sub_acoustic on 2009-07-15
One vital clue perhaps...thanks to htop...

My CPU load seems to be constantly at 100% even though if I were to add up the percentage column of all the different programme functions, the total would not be more than 15%.....

is this normal?

acpi -t says that it's not overheating at all

any advice?

---

### Post by sub_acoustic on 2009-07-16
ah...the latest updates seem to have fixed it.....

Thanks Developers!

---

