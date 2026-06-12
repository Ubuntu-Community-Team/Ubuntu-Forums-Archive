---
title: "Upgraded to 9.04.....rude shutdown"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Shriner on 2009-04-25
After upgrading to to 9.04, I was experiencing rude shutdowns on my lappy, like it thought I was on the battery (I wasn't) and it was critically low.

Ultimately I traced this to running BOINC (formerly seti@home). The default settings were overdriving the CPU causing it to overheat (or send that signal). 

Adjusting BOINC to use only 10% of the CPU seems to have cleared the problem. Note that even with this setting it is using approximately 50% of the CPU.

Lappy is HP Pavilion DV9000, AMD Turion 64 X2 Mobile TL-64
9.04 is 64 bit version.

EDIT: BTW, thanks for the forum. Been reading here and there for some time and using 8.10 most recently. This was first I needed to post anything. Thought the info was worth posting.

---

### Post by Shriner on 2009-04-26
I just noticed that BOINC is reporting that htere is a new version (6.4.5) available, but it is not in the repository yet. 6.2.18 is the one currently there.

---

### Post by michael37 on 2009-05-02
A few things.
[LIST=1]
[*] Yes, BOINC with new apps tend to stress the computer CPU quite a bit.  Try to get a control software for fans and make the fans work harder.  I am using gkrellm (for monitoring) and i8k utilities (for fan control/Dell only) on my Dell laptop to accomplish just that.  

[*] Get BOINC 6.4.5 from [http://www.getdeb.net/app/Boinc](http://www.getdeb.net/app/Boinc)

[*] If you want to speed up seti@home on your computer, read up the following webpage [http://www.arkayn.us/seti/index.htm](http://www.arkayn.us/seti/index.htm).

[*] Jaunty has a bug which affects *optimized*  Seti application **only** on Core 2 Duo mobile laptops. From [http://lunatics.kwsn.net](http://lunatics.kwsn.net).
*If you don't know what an optimized Seti application is, read above*.
[/LIST]
> So, if you want to use the optimized application version astropulse 5.03 x64 sse3 with Ubuntu/Kubuntu/Xubuntu 9.04 and kernel 2.6.28-11-generic on a core 2 mobile with "Merom" core, please use astropulse 5.03 x64 sse2 optimized application version instead.

---

