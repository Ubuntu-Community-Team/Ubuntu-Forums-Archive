---
title: "Ubuntu 9.10 Fails to Shutdown"
date: 2010-01-02
forum: Hardware
---

### Post by xtjacob on 2010-01-02
I have Ubuntu 9.10 64-bit on an Acer Aspire 4530, and it recently started to shutdown incorrectly. When I choose shutdown or restart it shows the logo then the screen goes black and it sits there. The hard drive light flashes for a little bit then stop and the laptop sits there doing nothing. To get it to finally shut down I have to hold down the power button. Thanks in advance!

---

### Post by benbelly on 2010-01-03
I am having the same problem on my Dell D630.  Are there any trouble shooting guides for shutdown?

---

### Post by xtjacob on 2010-01-03
I got it solved on mine. I have a duel-core laptop so I add "CONCURRENCY=shell" to /etc/default/rcS to use both processors on startup and that caused the problem. Taking it out fixed it.

---

### Post by benbelly on 2010-01-03
I don't have that setting in mine.  :(  Oh well

---

