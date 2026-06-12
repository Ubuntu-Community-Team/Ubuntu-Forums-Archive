---
title: "USB Modem Question"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by Ingla on 2005-11-08
Hello.

I'm using a USB modem. It works fine, but I've noticed something strange.

I run Windows on one hard drive and Ubuntu on another. I just tell CMOS which to boot to.

After I've been on Linux for a while and go back to Windows, the modem is messed up. It cannot connect (and has 2 of its 3 lights on...but the wrong ones). If I unplug the modem from both the computer and the adsl line, wait a minute, and reconnect it, it works fine.

This is not too big a deal, but I can't help wondering if I'm doing some kind of damage to the modem using it under Ubuntu.

Anybody have such an issue or can anyone who knows about hardware take an educated guess?

Thanks very much.

---

### Post by 23meg on 2005-11-08
It probably has to do with the fact that the linux driver is loading a firmware image into the modem which may not be unloaded correctly every time. It won't do any damage, don't worry.

---

### Post by Ingla on 2005-11-08
Thank you very much.

---

### Post by 23meg on 2005-11-08
You're welcome. Which modem are you using? I've noticed the behavior you describe in one that uses the eciadsl driver and I have another workaround for you if you use this driver.

---

### Post by Ingla on 2005-11-10
Hi.

Sorry to take so long responding. I'm on the Windows hard disk a lot (until I can find enough of the alternative Linux programs I need), and I usually wait until I'm back on Linux to get to the forums (I have a number of issues on different threads, and some require me to try different things and write back and forth).

I'm using a USB ADSL ALE 130 modem provided by my ISP. It says it comes from [www.rotalcom.com](www.rotalcom.com), but I think this is some sort of subsidiary or reseller. The system recognized it under a different company name, but I can't recall what it was.

Once or twice, when I booted back into Windows, it just worked. However, I usually need to unplug it. This is even after completely shutting down the computer for a few minutes.

As I said, it's not the worst problem in the world, but if it can be fixed, that would be nice.

Thanks a lot.

---

### Post by Ingla on 2005-11-13
Hi, 23meg.

I'd still be interested in your workaround.

Thanks.

---

### Post by 23meg on 2005-11-23
If you can verify you're using eciadsl, try entering the ```
eciadsl-stop
``` command before logging out.

---

