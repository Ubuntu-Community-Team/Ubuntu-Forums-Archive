---
title: "GPU hang with Cairo-dock with openGL activated"
date: 2013-04-11
forum: Hardware
---

### Post by sjaglin on 2013-04-11
Hi,

Just wanted to share that really. I have a new laptop thinkpad T410 with intel i5 M520 on board and the intel integrated graphics. I installed the latest version of Ubuntu 12.04 LTS. All was working well, I had compiz enabled with wobbly windows and expo enabled.

I kept having some GPU hangs where the screen would freeze and a message error "do you want to report etc..." indicating a GPU hang. It became a real embarassement, my brand new laptop would run better on windoze 7 that on Linux! I nearly sent the machine back.
Then I remembered that cairo-dock used compositing and that it could be the reason.

BINGO! I replaced cairo-dock by AWN (avant-windows-navigator) and it worked, no more GPU hangs and all works fine now.

I thought I'd share that here i order to reassure user of the Thinkpad t410 that it works fine with Ubuntu and compiz activated.

Cheers,

:P

---

