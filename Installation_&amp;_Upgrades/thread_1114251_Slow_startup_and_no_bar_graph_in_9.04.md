---
title: "Slow startup and no bar graph in 9.04"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by keithclark on 2009-04-02
I just upgraded to 9.04 and now I don't get the Ubuntu title screen with a bar showing progress.  It is just a black screen.

I also have times where it takes forever to boot up.  So long in fact that I end up powering down and trying again.

There is also the matter of the DVD +/-RW driver.  I cannot write to it anymore.  It see the drive, will allow me to erase the media (at times) but will just error out when I try to write something to it.

Thanks,

Keith

---

### Post by cariboo on 2009-04-02
It sounds like your upgrade didn't finish. Start in recovery mode and at the menu drop to a prompt with networking. At the prompt type:

```
sudo apt-get install -f
```

If there are any missing dependencies, the above command wil repair the problem. Then at the prompt type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The above commands should should complete the upgrade process.

Jim

---

