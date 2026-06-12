---
title: "Why is Cron not started automatically in Ubuntu??"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by bngguy on 2009-05-17
Hello All,
           Is there a reason cron is not started during bootup in Ubuntu???,
Look forward to your response.

Bye,
Aravind

---

### Post by squaregoldfish on 2009-05-17
Hmm... as far as I know, it's always been started by default. Perhaps your config has got screwed up somewhere along the line.

I don't know how experienced you are with this, so let's start with the basics (forgive me if you're more advanced!).

First, let's make sure it's not running:

```
ps -eaf |grep cron
```

If you get a result, cron is running - so what make you think it isn't? Do you have a cron job that's not running?

If you don't get any output, it's definitely not running.

Check /etc/rc<runlevel>.d (for whichever runlevel you're using - use runlevel to find out, most likely 2), and see if you've got symbolic links named S89cron and S89anacron in there. If you have, it will be trying to start it, but for some reason it's failing. Try to start it by hand:

```
sudo /etc/init.d/cron start
```

and see what the output is.

Let us know the result!

Steve.

---

### Post by kpkeerthi on 2009-05-17
Check if it is disabled under System -> Admin -> Services

---

### Post by bngguy on 2009-05-18
> **kpkeerthi said:**
> Check if it is disabled under System -> Admin -> Services

Thanks, that fixed it.

---

