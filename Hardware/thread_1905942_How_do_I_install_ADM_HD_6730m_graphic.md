---
title: "How do I install ADM HD 6730m graphic ?"
date: 2012-01-08
forum: Hardware
---

### Post by mohsen_bu on 2012-01-08
Hello Ubuntu users
I recently installed the operating system
And I am a beginner
I want to install graphic on the laptop

my graphic is ADM HD 6730m.

i download the:

[B]ati-driver-installer-11-12-x86.x86_64.run
[/B]

How do I install it with terminal or other ways ...?

Thanks

---

### Post by khelben1979 on 2012-01-08
You can begin to read through [this document]("http://wiki.cchtml.com/index.php/Ubuntu") slowly, at first.
So according to the instructions, make sure that you haven't got an old Catalyst driver which haven't been removed, then do like this:

```
sudo ./ati-driver-installer-11-12-x86.x86_64.run
``` or run it as root user without the sudo command at first.

Then
```
aticonfig --initial
```

(Also, it's very important that you choose the exact right video driver based upon the choice when you downloaded it from the AMD webpage, like for instance having a 64 bit driver on a 64 bit system etc etc. no rush in download in other words.. A reboot afterwards might be required as well.)

---

### Post by mohsen_bu on 2012-01-08
> **khelben1979 said:**
> You can begin to read through [this document]("http://wiki.cchtml.com/index.php/Ubuntu") slowly, at first.
So according to the instructions, make sure that you haven't got an old Catalyst driver which haven't been removed, then do like this:

```
sudo ./ati-driver-installer-11-12-x86.x86_64.run
``` or run it as root user without the sudo command at first.

Then
```
aticonfig --initial
```(Also, it's very important that you choose the exact right video driver based upon the choice when you downloaded it from the AMD webpage, like for instance having a 64 bit driver on a 64 bit system etc etc. no rush in download in other words.. A reboot afterwards might be required as well.)
Thanks
 The problem was solved
:D

---

### Post by khelben1979 on 2012-01-08
Sounds good! :)

*PS. mark the thread as solved by clicking on thread tools menu.*

---

### Post by mohsen_bu on 2012-01-08
hi.
there is a problem.
after reboot the laptop , desktop show a logo in right bottom side.
the logo title is :

AMD 
Unsupported
hardware

what can i do to hide it....?

Thanks.

---

### Post by silverhaze06 on 2012-01-08
> **mohsen_bu said:**
> hi.
there is a problem.
after reboot the laptop , desktop show a logo in right bottom side.
the logo title is :

AMD 
Unsupported
hardware

what can i do to hide it....?

Thanks.

Read this thread. I never had the watermark problem. But for people who did, this thread helped. For me it just made my graphics card perform a whole lot better. So either way, it's worth taking a look at. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by khelben1979 on 2012-01-08
The solution would be to wait for a newer version for AMD Catalyst to get released.

Other than that, what version does your AMD Catalyst Control center report? I think the watermark correctly identifies your HD 6730M graphics as unsupported, but it works due to being part of the Radeon HD 6000M series... just that your specific model isn't fully supported as well as the other ones which have been out longer on the market.

---

