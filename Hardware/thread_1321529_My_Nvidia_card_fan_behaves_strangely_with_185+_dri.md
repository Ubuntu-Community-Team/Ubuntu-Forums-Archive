---
title: "My Nvidia card fan behaves strangely with 185+ drivers (nVidia 8400M GS)"
date: 2009-11-10
forum: Hardware
---

### Post by tribaal on 2009-11-10
Hi folks,

I have a Dell M1330 laptop that runs Ubuntu beautifully since I bought it.

However, since I upgraded to 9.10, the nVidia drivers have been bumped from 180.* to 185.*, and now my video card has a weird behavior:
Everything works just fine, but the fans blow at full speed for the first 15 minutes of activity, then suddently fall back to a normal speed. It's quite noisy, so my temporary "patch" is to use the 173.* drivers from the repositories instead.

Does anybody have a workaround for this problem? Trying 190.* series drivers gave me the exact same results.

Please note: I'm not looking for a "it's not ubuntu's fault, ask nvidia" type of answer, I know exactly where this stands. I'm looking for a workaround. And yes, I did read search the forums first.

Cheers,

- Trib'

---

### Post by tribaal on 2009-11-16
Ok I fixed it.

Upgrading the BIOS for my computer solved the problem entirely for me, and I have the latest 185* drivers working perfectly without any fan problems.

The procedure to upgrade your Dell BIOS [can be found here]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate").
It's really extremely easy to do (even for a total newbie), but please don't hesitate to report back here if you're having issues, I'll try to help as much as I can.

Hope this helps,

- Trib'

---

