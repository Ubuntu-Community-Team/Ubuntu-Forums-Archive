---
title: "Hauppauge HVR4000 no channel lock on mythtv"
date: 2008-05-27
forum: Hardware
---

### Post by ajw107 on 2008-05-27
Hi

I've just had to reinstall ubuntu, and seem to be having a bit of a problem with my hvr4000 tv card (but only in mythtv):

When I select watch tv I get told mythtv can't get a lock.
I close mythtv frontend and backend
run kaffeine
Kaffiene finds the channels okay
restart mythtv backend and frontend
channel lock and scanning now works

If I were to try and run any other dvb program with the backend running the /dev/dvb/adapter1/frontend0 is busy (using dvb-t and the multi front end patch [this problem also occurs with the single front end patch])

My log file also gets filled up with the line:
cx22702_readreg: readreg error (ret == -121)

I did find these pages, however:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971)
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.24.y.git;a=commitdiff;h=dcd8f5bca3782f180c028446710edc16ebce73f6](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.24.y.git;a=commitdiff;h=dcd8f5bca3782f180c028446710edc16ebce73f6)
[http://linuxtv.org/hg/~stoth/v4l-dvb/rev/e55d97ff8bba](http://linuxtv.org/hg/~stoth/v4l-dvb/rev/e55d97ff8bba)

which talk of exactly the same problem with the HVR1300 caused by a bug in hal cauing some values to be overwritten (I can even confirm this, as their work around of stopping hal, then unloading and reloading the v4l modules works, but the kaffine work around above also works conversly).  Unfortunately though, the code fix does not work for me (applied to the v4l driver rather than the kernel [which would get overwritten once I installed the v4l patched for hvr4000 support]).

I'm at a loss to what to do next, and was wondering if anyone else has any ideas?  As I say, the card did work before  had to reinstall ubuntu (this problem occurs on mythbuntu as well).

Thank you for any help you can give.

---

### Post by ajw107 on 2008-05-28
Sorry to be a pain about this, but BUMP...

---

### Post by munzli on 2008-06-11
hey, did you find the problem?

i'm about to buy a DVB-S2 card and try to get it running... right now i can't help you but i'd like to know if the card runs ok. are you using any of these patches? [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)

---

