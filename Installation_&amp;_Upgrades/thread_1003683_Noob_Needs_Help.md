---
title: "Noob Needs Help"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by skiguy45 on 2008-12-06
I wasn't really paying attention to my system as I was installing the OS and now that it's done, the system has booted up and is prompting me for a UN and PW - I haven't a clue what I told it to use, is there any way to bypass this or do I just have to re-format my HDD and re-install the OS (and pay attention this time)?

---

### Post by taurus on 2008-12-06
Is Ubuntu the only OS on that machine?  Can you boot into recovery mode from GRUB menu (press ESC when you see the word GRUB to bring up the menu)?  If you don't remember your username, look at the output of this command after you have booted into the recovery mode.

```
ls -la /home
```

---

### Post by Diabolis on 2008-12-06
Since thats a fresh install, you won't lose anything if you reinstall the OS. There are workarounds, but probably that will be the easiest solution.

---

### Post by skiguy45 on 2008-12-06
> **taurus said:**
> Is Ubuntu the only OS on that machine?  Can you boot into recovery mode from GRUB menu (press ESC when you see the word GRUB to bring up the menu)?  If you don't remember your username, look at the output of this command after you have booted into the recovery mode.

```
ls -la /home
```

Yes it's the only OS on the machine.  I took an older P4 with XP pro and decided that it's time to put a more robust OS on it since it was running like crap.

---

### Post by lukjad on 2008-12-06
Here is a guide on how to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It gives you all the steps you need.

---

### Post by skiguy45 on 2008-12-06
> **lukjad007 said:**
> Here is a guide on how to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

It gives you all the steps you need.
That did it!  Thank you very much.  I look forward to immersing myself in this new OS and community. It's about time that I learn what open source has to offer.

Cheers!

---

### Post by lukjad on 2008-12-06
I'm glad it worked. :D 

Just a tip, keep that site handy. It's really good. It gives you a pretty good start on what your need to know.

---

