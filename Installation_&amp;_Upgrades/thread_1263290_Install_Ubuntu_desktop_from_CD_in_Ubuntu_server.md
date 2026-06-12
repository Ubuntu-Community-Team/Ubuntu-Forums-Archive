---
title: "Install Ubuntu desktop from CD in Ubuntu server"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Anaximines on 2009-09-10
Hi, I'm sorry if this is the wrong place for this question but I'm sure someone here can help me.

I've installed Ubuntu 9.04 Server and want to change to 9.04 Desktop. For some reason my computer has lost the ability to boot from any disc (Ubuntu or Windows XP - it says "operating system not found") so I'm trying to get the Ubuntu Desktop install running from within Ubuntu Server... maybe this is impossible? I really don't know that much about Linux.

Anyway, I've mounted the Ubuntu Desktop install CD and am browsing the files there but I'm not sure how (or again, if it's possible) to start the process.

Any help?

Thanks a lot!

---

### Post by wojox on 2009-09-10
Just type:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Anaximines on 2009-09-10
Thanks a lot! I didn't think about just doing it that way...

I don't have the machine online right now but I'll look up how to set that up and then be on my merry way. Thanks!

---

