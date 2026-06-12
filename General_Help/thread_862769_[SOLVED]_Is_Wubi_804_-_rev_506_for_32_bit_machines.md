---
title: "[SOLVED] Is Wubi 804 - rev 506 for 32 bit machines?"
date: 2008-07-17
forum: General Help
---

### Post by JohnFUSA on 2008-07-17
I installed wubi 8.04-rev506 on my 32 bit computer, is this the correct version? My current hardware conig is:
Asus p5ne sli
intel core 2 duo 2.2ghz
nvidia 8500 gt 512 mb
Maxtor 120 gb sata

---

### Post by minhmeoke on 2008-07-17
Yes, Wubi 8.04-rev506 is the latest stable version. The Wubi installer should autodetect your computer's capabilities (32 or 64-bit), and download the corresponding iso.

I think that the Core 2 is a 64-bit processor, so it might install the 64-bit version (x86_64), but if you want to use install 32 bit operating system, then use download the 32-bit iso and place it in the same folder as wubi.exe, or add the "--32bit" argument when running wubi from the command line.

[https://wiki.ubuntu.com/WubiGuide#head-f08a3f4a79668f448aa172983f369799d9d1a008](https://wiki.ubuntu.com/WubiGuide#head-f08a3f4a79668f448aa172983f369799d9d1a008)

---

### Post by JohnFUSA on 2008-07-18
Thanks minhmeoke, I've had it installed for about a week. It works except for a couple of strange little bugs; The java in Firefox doesn't work, and all the windows on the desktop seem to open with the title bar obscured by the top task panel. I know my system is 32bit and thought I could have downloaded the wrong version of wubi.(when I tried to Install the 32 bit Opera browser it said my version of ubuntu was 64 bit so it wouldn't install}
Well I really like Ubuntu and now I am considering Installing Hardy Heron on a dedicated partition. I'm definitely not going with that behemoth vista that Microsoft is trying to shove down every ones throats.

---

