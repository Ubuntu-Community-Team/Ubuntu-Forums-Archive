---
title: "Thinkpad R52, kernel panic! not able to hibernate; w.t.f."
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by shmi85 on 2007-07-12
Hi everyone, I'm a bit at a loss right now. I'm running 7.04 on the R52.

I was having trouble with my sound for a while, which was fixed with the HIBERNATE=platform discussed in bug #80893 found here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893")

This worked perfectly fine for a week or so, but now for whatever reason, hibernate never works -- I haven't been able to watch the whole series of events since usually I need to hibernate and leave, but it generally goes a black screen and there's a few screens-worth of commands and/or error messages and then I believe that it stops. Usually when I get back and open up the laptop, the login screen pops up as if I had gone idle and I can tell from the heat of the case that it never actually hibernated. 

Today when I got back, it was frozen at the black screen full of commands/errors, the last one being kernel panic! I'd like to provide the system logs for someone more experienced than I to take a look at, but I don't know which logs to provide, after looking through the System Log Viewer. If anyone has any ideas or could tell me which logs to provide and if I should just save them as a text file with gedit or in some other way for upload to this post, that would be great!

---

### Post by EXCiD3 on 2007-07-12
I know that Hibernate and Suspend support for laptops is lacking quite a bit in Ubuntu for the moment. Many laptops, mine included cannot successfully resume. One of the problems is due to using the proprietary drivers such as the NVIDIA driver has broken hibernate for many people. I have tried it a couple of times and when i saw that it looked like my screen's liquid was draining i decided not to try it again for a while...

---

