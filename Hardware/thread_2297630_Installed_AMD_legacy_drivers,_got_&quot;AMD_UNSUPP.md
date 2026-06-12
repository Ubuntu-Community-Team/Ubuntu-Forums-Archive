---
title: "Installed AMD legacy drivers, got &quot;AMD UNSUPPORTED HARDWARE&quot; on the screen"
date: 2015-10-05
forum: Hardware
---

### Post by rocket3 on 2015-10-05
Hey everybody, i installed the amd catalisty legacy drivers ([https://launchpad.net/~makson96/+archive/ubuntu/fglrx](https://launchpad.net/~makson96/+archive/ubuntu/fglrx)), and when i boot in it says unsupported hardware, how can i fix this?
(i got kubuntu 12.04)

---

### Post by QIII on 2015-10-05
What prompted you to install the legacy driver?  There was no need for that.

This is the source of the warning.

I would recommend removing the driver you got from the PPA and installing the supported fglrx driver from the repo.

---

### Post by rocket3 on 2015-10-05
Alright, i will do that

---

### Post by rocket3 on 2015-10-05
I used the purge command, like it suggests, but it didnt remove the ati driver, can you help me?

---

### Post by QIII on 2015-10-05
Unfortunately, I have no experience with the makson PPA and recommended against it several years ago because nobody at the time could possibly have known what future problems might arise.

One thing I believe it did was roll back Xorg to an earlier version, which may also now cause you problems.

You may have to contact the maintainers of the PPA.

---

### Post by QIII on 2015-10-05
Also -- what is the model of your graphics adapter?

If it is earlier than an HD 5000 series you will need to use the default open source Radeon driver.

---

### Post by Bucky Ball on 2015-10-05
*Thread moved to **Hardware**.*

---

### Post by rocket3 on 2015-10-05
Alright, i just fixed it, thanks for trying to help me!

---

### Post by Bucky Ball on 2015-10-05
Good news. Please confirm it was the fglrx driver that did the trick to help others. Thanks. :)

---

