---
title: "How do I disable some of the hardware?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by ruialexbarbosa on 2007-06-20
Hi,

I'm running ubuntu on a laptop and I would like to disable some hardware to save resources. In Win XP you can just go to hardware and disable whatever, is there a similar way in ubuntu?

I want to disable bluetooth, ethernet, irda, pcmcia ...

Cheers:p

---

### Post by txgeek on 2007-06-20
Not sure how many system resources you're going to free up, but the following should do it.


sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

Remove the X for all of those you listed above then reboot

---

### Post by ruialexbarbosa on 2007-06-22
Thanks ;)

---

