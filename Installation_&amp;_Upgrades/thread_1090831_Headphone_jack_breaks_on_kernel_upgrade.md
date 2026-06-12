---
title: "Headphone jack breaks on kernel upgrade"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by minj on 2009-03-08
So I was using my Hardy Heron quite flawlessly for some time and one day I see a kernel upgrade available. Being trustworthy of ubuntu and canonical and using LTS version I did everything as usual: download, install, reboot, go on.... 

STOP RIGHT THERE

2.6.24-22-generic was upgraded to 2.6.24-23-generic I think and my headphone jack just stopped working! Btw spare me with the comments about volume control and bad headphones. I changed nothing and my headphones were fine, tested 2 different ones btw.

Anyway I was a bit mad but thought 'whatever these things happen'. So I downgraded to 2.6.24-22-generic and locked the version. Guess what I had been enjoying my headphone jack for a few months after that.

Now I started to feel behind the times a bit you know and decided to test intrepid today with its 2.6.27-11-generic kernel.... And guess what?!

The sound does not work again! Now this is seriously messed up. You would think they noticed it while going 3 subversions up but NO....

So, any bright ideas what should I do now?

---

### Post by Neo_The_User on 2009-03-08
Well you can always compile your own kernel and fix it yourself but first file a bug.

---

### Post by minj on 2009-03-08
Bugzilla turned up empty but here is what I have found on the launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957)

Apparently headphones are controlled by the 'surround' channel o.0

---

### Post by sgosnell on 2009-03-08
Open the ALSA mixer and make sure the headphone checkbox on the Switches tab is ticked.

---

### Post by Neo_The_User on 2009-03-08
ALSA mixer can be launched from the terminal by doing

```

sudo alsamixer

```

---

