---
title: "new firefox update crashes with gmail--security question"
date: 2008-09-25
forum: General Help
---

### Post by fred168 on 2008-09-25
Hi,

The recent firefox update (2.0.0.17, for feisty) does not work with gmail (i.e. the firefox window closes immediately).

I managed to figure out how to remove it and reinstall 2.0.0.16, but this leaves me open to the security fixes in 2.0.0.17 listed here:

[http://www.ubuntu.com/usn/usn-645-1](http://www.ubuntu.com/usn/usn-645-1)

What should I do?----Opera looks tempting...

[Is there somewhere more suitable I should post this question?]

---

### Post by New_Horizons on 2008-09-26
Hi!

Do you have any extension installed? I deinstalled foxyproxy, which solved the problem for me. Try deinstalling some extensions one by one to track down the problem ...

---

### Post by fred168 on 2008-09-27
Yes I am using foxyproxy, so that could well be the problem, thanks. [I'm not sure I want to give up the convenience of foxyproxy though--I need to tunnel to work quite often, so may stick with version 2.0.0.16, and risk the insecurity]---I guess the nice people at foxyproxy might be able to solve this though:

[http://foxyproxy.mozdev.org/drupal/content/foxyproxy-crashes-firefox-20017-shutdown](http://foxyproxy.mozdev.org/drupal/content/foxyproxy-crashes-firefox-20017-shutdown)

[https://bugzilla.mozilla.org/show_bug.cgi?id=456705](https://bugzilla.mozilla.org/show_bug.cgi?id=456705)

[The connection with gmail seems to be just that I was using the https version, and foxyproxy+2.0.0.17 is having trouble with this.]

---

