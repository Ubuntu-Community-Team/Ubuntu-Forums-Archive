---
title: "HP Pavilion dv6 can't resume from suspend on Ubuntu 12.04"
date: 2012-04-29
forum: Hardware
---

### Post by teeli on 2012-04-29
Hi,

I installed Ubuntu 12.04 on my HP Pavilion dv6 laptop and otherwise it seems to be working fine except it can't resume from suspend. When I suspend the computer (or close the lid) and try to resume after it, it just gets stuck on black screen, the fans start screaming and the computer just keeps getting hotter.

I tried searching for solutions and there seems to be similar issues with this model, but all the suggested solutions I found this far, were for older Ubuntu versions and did not solve my problem.

So does anyone have any suggestions how to even start solving this problem?

I'm not linux expert by any means, so I'm sorry if I seem completely clueless :)

---

### Post by jackdale on 2012-05-05
No answers here but just adding to the question.

I have an ASUS laptop with Intel® Core™ i5-2450M CPU @ 2.50GHz × 4 and nVidia GeForce 610M with 2GB using the nouveau driver.

Has had the same problem since 11.10.

No problems with this on my desktop since 8.10.

When I close the laptop lid it suspends with no problem, but now when lid opens, there is no response to anything and I need to do a hard shutdown (laptop version).

Same problem when hibernate is chosen on close lid instead of suspend.

Otherwise I'm loving 12.04.  It even tells me how much charge is in my phone when connected :D

---

### Post by dotnick on 2012-05-17
I have the same problem with the radeon driver.  I changed to fglrx and it now works correctly.  I think there are still issues with the radeon driver.

---

### Post by sscaff1 on 2012-06-09
I have the same problem. Is there a solution for this problem? I'm using the FGLRX driver. I downloaded the latest Catalyst Controller Center and drivers from AMD's website.

---

### Post by andyhelloween on 2012-06-09
Just installed 12.04 on HP DV6-7032TX. It has integrated Intel video and nVidia GT 630M I believe it's using the Intel one.

I've just suspended it and went back normal. The only thing I noticed was the Wireless led indicator turned off... although wireless was up and running.

Sorry I can't help you more...

---

