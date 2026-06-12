---
title: "nVidia &quot;legacy&quot; video support in 8.10"
date: 2008-10-24
forum: General Help
---

### Post by belovedmonster on 2008-10-24
I was reading the release notes for the RC and it seems that in 8.10 my graphics card will no longer support 3D acceleration. What I want to know if whether this is just a temporary thing and will be fixed in 9.04 or whether it will be unable to do 3D for ever now. :confused:

---

### Post by sco01 on 2008-10-24
That worries me too. It sounds like a dealbreaker to me. Does anybody know what they did to Xorg to break compatibility with these drivers?

//S

---

### Post by Elfy on 2008-10-24
> The xserver was updated to version 1.5, which broke the ABI compatibility. As a result, drivers 96 and 71 (and fglrx) dont&#8217; work with the new xserver and unfortunately the -IgnoreABI option of Xorg doesn&#8217;t solve the problem. This is something that only NVIDIA can solve. (177 and 173 work well) from alberto milone's blog - no idea what it means - except it broke it :(

> ...this is just a temporary thing and will be fixed in 9.04 or whether it will be unable to do 3D for ever now...That is in the hands of nvidia - there's more thna one thread on the situation and people using, I think, fedora 9 have been waiting longer.

I personally hope that the nouveau driver get's more work - and I wish I could help, but can't - and ends with 3d and tvout and I'd would stop using nvidia.

---

