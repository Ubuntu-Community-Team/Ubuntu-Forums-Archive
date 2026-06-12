---
title: "Laptop won't boot Xubuntu live cd anymore!"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by link141 on 2007-02-14
Hey guys.
I recently booted my sister's old IBM thinkpad off of a Xubuntu 6.06 live cd (successfully), and it locked up, because the cd drive was functioning sporadically.  I then had to manually reboot it, and I tried booting off the live cd again, but it gave me this error:
```

[994.750773] Invalid compressed format (err=1)
[994.752255] Kernel panic - not syncing VFS: unable to mount root fs on unknown block (1,0)
[994.757333]

``` 
The numbers are different each time, and the error differs slightly for each live cd.  I've tried booting the Ubuntu 6.06, Ubuntu 6.10, Xubuntu 6.06, and Xubuntu 6.10 live cds, but they all give me the same error.  Does anyone know how to fix this?

---

### Post by bandie on 2007-02-27
how much Ram is in the PC if its less than 192mb then the live CD will have problems, use the "ALT" CD which allows you to install with as little as 64mb

---

### Post by link141 on 2007-02-28
Thanks for your response.
See, the weird thing is, that when I booted it before off the live-CD, I was able to use the live system (without it giving me this error on boot), but after it locked up in the middle of a live session (due to a bad CD drive) and I had to do a manual reboot.  The live CD will always give me this error (unless it's a Kubuntu live-CD, but that's a little too heavy on system requirements...) after choosing any of the boot options.  But you've got a point, the darn thing only has 128MB of RAM in it, and so, I've downloaded and burned an alternate install CD (what's weird though, was that I was able to install from the live-CD in the past without any errors) which I can now use to install the system on. 
Thanks again for responding :)

---

