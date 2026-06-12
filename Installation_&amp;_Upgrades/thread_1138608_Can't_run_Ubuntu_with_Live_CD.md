---
title: "Can't run Ubuntu with Live CD"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Dryel on 2009-04-26
I downloaded the latest Ubuntu .iso file (9.04) and burnt it. When I try to run Ubuntu from the CD without changing stuff on the computer I get the following errors after some time of waiting;

[I]init: Unable to execute "/bin/sh" for rcS: Input/Output error
init: rcs main process (1778) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Input/Output erroer
init: rc-default main process (1779) terminated with status 255[/I]

I have no clue what these mean or what I should do, any help would be appreciated a bunch. There shouldn't be anything wrong with the .iso file since I checked the .iso file with md5sum. 

Computer specifications:
Processor: AMD Athlon 64 X2 dual core Processor 6000+ 3,01 GHz
Graphics: NVIDIA GeForce 8600 GT
RAM: 2GB
Installed OS: Windows XP Pro

Thanks in advance,

---

### Post by Dryel on 2009-04-26
Bump, if anyone just knows what these error lines means maybe it could help me some way.

---

### Post by hansdown on 2009-04-26
Hi Dryel.

You need to burn the disk at the slowest possible write speed.

Here is some info on the error messages.

[http://www.google.ca/search?q=+init%3A+Unable+to+execute+%22%2Fbin%2Fsh%22+for+rcS%3A+Input%2FOutput+error+init%3A+rcs+main+process+(177+terminated+with+status+255+init%3A+Unable+to+execute+%22%2Fbin%2Fsh%22+for+rc-default%3A+Input%2FOutput+erroer+init%3A+rc-default+main+process+(1779)+terminated+with+status+255&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+init%3A+Unable+to+execute+%22%2Fbin%2Fsh%22+for+rcS%3A+Input%2FOutput+error+init%3A+rcs+main+process+(177+terminated+with+status+255+init%3A+Unable+to+execute+%22%2Fbin%2Fsh%22+for+rc-default%3A+Input%2FOutput+erroer+init%3A+rc-default+main+process+(1779)+terminated+with+status+255&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by lisati on 2009-04-26
If a "bad burn" turns out to be the problem, there are some tips here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

