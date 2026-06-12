---
title: "Install freezes at 27%"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by littleport2003 on 2009-01-09
Hi guys,

I'm trying to install in parallel with windows, I've burnt a install CD, put it in the drive when I'm running windows, it does it's thing and asks me to reboot, I reboot in ubunto and it carries on installing, it gets to the point where it's saying 'copying files' but everytime it just freezes at 27%, no responce from moveing the mouse, and I've left it a good half an hour a couple of times, but still doesn't do anything. Any ideas what I'm doing wrong?

Thanks,
Matt

---

### Post by avtolle on 2009-01-09
Did you check the md5sum of the iso before burning to a CD? Did you burn the iso as an image at a low speed (4x)? Did you use a CD-R or a CD-RW (I use CD-Rs as they give the best results). Did you do a verify on the CD before beginning the installation? I ask these questions because the above are very common issues. Take a look at [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) for some general information. Good luck, and post back with questions.

---

### Post by albinootje on 2009-01-09
> **littleport2003 said:**
>  it gets to the point where it's saying 'copying files' but everytime it just freezes at 27%, no responce from moveing the mouse, and I've left it a good half an hour a couple of times, but still doesn't do anything. 

You can try again, and press F6 at the installation cdrom prompt, and then pass the parameters "noapic nolapic" to the end of that line (without the " " signs).

And if you can, please post the output of the following before starting the installation :
```

dmesg
lspci

```

---

