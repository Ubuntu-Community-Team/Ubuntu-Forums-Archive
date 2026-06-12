---
title: "nvidia card locks restart"
date: 2013-01-29
forum: Hardware
---

### Post by rhering on 2013-01-29
[**Solved] **Hi All,
I am having a problem with Ubuntu 12.04 and my nvidia gforce 6200 card. It seems that it keeps the system from restarting, from the button or by terminal. The card works grreat other than that and the system restarts without the video card. Any ideas or suggestions would be greatly appreciated. Thanks

Edit: I also just noticed my HD is being checked at boot. It wasnt before removing video card.

Found out the problem and a solution, the Intel 865 chipset must be slightly incompapable. Changed the board to one with an 845 chipset and all works great.

---

