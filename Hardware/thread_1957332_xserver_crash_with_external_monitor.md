---
title: "xserver crash with external monitor"
date: 2012-04-12
forum: Hardware
---

### Post by manybodycpa on 2012-04-12
Dear all,

I am experiencing xserver crashes on a very regular basis (often after a couple of minutes) when using my Lenovo X220 with an external TFT screen.

Xorg.log always contains the same error:

[mi] EQ overflowing. The server is probably stuck in an > infinite loop.

The mouse cursor can still be moved, but the system does not respond in any other way.

I am running Natty with the 3.2.5 kernel. I have tried switching off
the rc6 option for the intel driver, and also tried the 3.2.9 kernel, with no success. However, working without the external screen has so far solved the problem. 

I have been using a different external screen for about a year without this issue, except for one similar hang-up about a week ago.

I would appreciate any input.

Thanks,

Martin

---

### Post by manybodycpa on 2012-04-13
I can now confirm that this problem exists with both of my monitors.
 Since the system was working fine for many months, I suppose a recent update (xserver, intel driver?) is causing the trouble.


Does anybody else have similar issues?

Can I get a list of recently updated packages somewhere?

---

