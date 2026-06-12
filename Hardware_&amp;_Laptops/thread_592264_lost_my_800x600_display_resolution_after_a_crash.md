---
title: "lost my 800x600 display resolution after a crash"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by bertszoghy on 2007-10-26
Hello,


Am running Ubuntu 6.06.1 LTS

I had a undiagnosed crash of the KUbuntu Desktop, it recovered fine except I now have only two monitor resolution choices: 640 x 480 and 1280 x 854

Am missing 800 x 600 and 1040x780

I tried a sudo apt-get update but that did not fix the problem

I think the graphics card is not detected properly, it says "Graphics card: nv"

Suggestions?

TIA,
Bert

---

### Post by overdrank on 2007-10-27
> **bertszoghy said:**
> Hello,


Am running Ubuntu 6.06.1 LTS

I had a undiagnosed crash of the KUbuntu Desktop, it recovered fine except I now have only two monitor resolution choices: 640 x 480 and 1280 x 854

Am missing 800 x 600 and 1040x780

I tried a sudo apt-get update but that did not fix the problem

I think the graphics card is not detected properly, it says "Graphics card: nv"

Suggestions?

TIA,
Bert
Hi and welcome, this link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
You may also and try to reconfigure your xorg also with
this command 
```
sudo dpkg-reconfigure xserver-xorg
``` and answer a few questions and if you don't know the answers leave as the default answer given. Hope this helps and good luck!

---

### Post by bertszoghy on 2007-12-01
Thank you,

This resolved my problem!

What a relief!

I wanted to mention that the first solution worked for me, there was a file missing, but I just ignored and kept going and the fix worked great.

Bert

---

