---
title: "Forget Gutsy 7.10 on Laptop: Fesity 7.04 or Edgy 6.10?"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by ace007 on 2007-11-30
Just got gutsy on my Dell Laptop (700m).

Well, I guess gutsy just doesn't like suspend/sleep/hibernate and there are a few workarounds I dont particularly like.  So, I guess I am going to downgrade.  The main issue is that when I suspend, I get a blank screen after trying to wake up.

Also, when I close the laptop it does not go to sleep on gutsy.  Would this be a gutsy issue, or do I have to manually enter suspend mode before closing the laptop?

Anywho, in order to take care of these problems, for the experts out there, will going back to 7.04 or 6.10 make a difference?  Or are the workarounds my best bet?

---

### Post by Bazirker on 2007-11-30
Have you tried messing with acpi settings at all?  Sometimes changing options there can fix things (though make sure to make backups!)  I had similar issues and some tweaking in this file helped, although I can't remember what I did...

```
sudo gedit /etc/default/acpi-support
```

---

### Post by ace007 on 2007-11-30
Well, I messed around with it, and I think it did the trick, but now I have some other issues.  So, I deleted the partition and installed feisty.  Guess what? works perfect without messing with anything!

---

### Post by ace007 on 2007-11-30
Check that, wireless wont work after suspend...

---

