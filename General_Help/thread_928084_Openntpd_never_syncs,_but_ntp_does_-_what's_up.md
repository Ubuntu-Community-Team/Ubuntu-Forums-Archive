---
title: "Openntpd never syncs, but ntp does - what's up?"
date: 2008-09-23
forum: General Help
---

### Post by lil_elvis2000 on 2008-09-23
Hello all,
  I've an interesting problem;

I installed openntpd on to my 8.04 server and configured it - very easy. I then did a ntpdate to a time server to set my clock and then started openntpd.

I can see in the logs the clock being slightly and the queries to the timservers. I waited 10 minutes and then attempted to synchronize from my other Linux box and also a Windows box. These failed. The Stratum is 3, accuracy -19, Leap 11...
So the server doesn't think it is sync'd.

After a couple of hours of waiting I tried again and same result.
So I gave up and installed ntp instead. Within 10 minutes it was sync'd and broadcasting the time to my other machines.

Is Openntpd broken on Ubuntu 8.04. Anyone using their latest version 4.4(?) on 8.04 and got it to work..

Thanks.

---

