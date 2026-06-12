---
title: "Firefox 3 random exits"
date: 2008-10-17
forum: General Help
---

### Post by preki on 2008-10-17
Hi all,

The last few days I've been having trouble with Firefox randomly closing down.  (When I restart I get the 'Firefox unexpectedly closed' dialogue box asking whether to resume the old session.)

I'm running Hardy and the start of the problem coincided with upgrading the kernel to 2.6.24-21 a few days ago.  But I now also have the problem when I boot to 2.6.24-19 (but maybe less frequently - hard to tell).

Seems to me like there could be all kinds of causes, e.g. new versions of Firefox plugins, but because the problem is intermittent (might go 5 mins or 2 hours without closing itself down) it's difficult to test where the problem lies.

Any suggestions?  Are there places I should look for crash dumps?

Thanks for your help, 
preki

---

### Post by sethvath on 2008-10-17
run firefox from the terminal and look out for faults/errors when it randomly shuts down. 

cd to your firefox folder
./firefox

---

### Post by preki on 2008-10-17
Have since found this - might be related to a recent Foxmarks update:

[http://getsatisfaction.com/foxmarks/topics/firefox_crashes_when_i_try_to_create_a_password_sync_pin](http://getsatisfaction.com/foxmarks/topics/firefox_crashes_when_i_try_to_create_a_password_sync_pin)

---

