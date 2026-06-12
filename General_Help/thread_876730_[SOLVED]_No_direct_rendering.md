---
title: "[SOLVED] No direct rendering?"
date: 2008-08-01
forum: General Help
---

### Post by Mark77 on 2008-08-01
Hello. I'm trying to get direct rendering working on Ubuntu, which I installed through Wubi (I'm not sure if this would be important or not), but I've been unable to get it to work. I have a nVIDIA geForce 8800 GT with 512mb memory for my graphics card. It should be able to support direct rendering. 

Are there any suggestions for what I can do? Thanks!

---

### Post by primolarry on 2008-08-01
Hi,

Did you activate NVIDIA restricted drivers?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Regards,

---

### Post by Mark77 on 2008-08-01
> **primolarry said:**
> Hi,

Did you activate NVIDIA restricted drivers?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Regards,

Well, I had, but the resolution was so low (640 x 480) and created problems for me being able to see easily that I reinstalled Ubuntu using Wubi. I did try to see if I had direct rendering after enabling the nVIDIA driver but it still said that I did not.

---

### Post by primolarry on 2008-08-01
Well I have never installed ubuntu using Wubi, I don't know if it works the same. You could try downloading the driver from NVIDIA web page.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Regards,

---

### Post by Mark77 on 2008-08-01
> **primolarry said:**
> Well I have never installed ubuntu using Wubi, I don't know if it works the same. You could try downloading the driver from NVIDIA web page.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Regards,

I'm sorry. I meant that I had downloaded the driver from nVIDIA and that was what caused the problems with resolution. After I had installed the one from nVIDIA I still didn't have direct rendering enabled.

---

### Post by Mark77 on 2008-08-01
If I were to reinstall the propriety driver, is there a way for me to uninstall it? I had troubles with that last time and was the reason I had to reinstall Ubuntu.

---

### Post by primolarry on 2008-08-01
Can you paste the output of ```
dpkg -l|grep nvidia
```

---

### Post by Mark77 on 2008-08-01
ii  nvidia-kernel-common                       20051028+1ubuntu8                        NVIDIA binary kernel module common files

I also tried to use the envy installer, but... 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by primolarry on 2008-08-01
that error msg means that you were performing other package operation at the same time (apt-get etc etc).

Try with the envy installer again, if you get the same erro message and can't figure out what other procress is locking the database just reboot and try again.

Regards,

---

### Post by Mark77 on 2008-08-01
> **primolarry said:**
> that error msg means that you were performing other package operation at the same time (apt-get etc etc).

Try with the envy installer again, if you get the same erro message and can't figure out what other procress is locking the database just reboot and try again.

Regards,

I managed to get it installed with Envy and it's working. Direct rendering is enabled as well as perfect resolution maintained. Thanks so much primolarry! You helped me a lot. I wish you the best of luck! :KS

---

### Post by Vadi on 2008-08-01
Please click on thread tools - mark thread as solved :)

---

