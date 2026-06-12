---
title: "Intel 4965 AGN with hardware switch"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by kkjaergaard on 2007-08-16
I've found quite a few threads and guides about Intel 4965 AGN wireless card. But none of them deals with with a physical network switch - all of them deals with e.g. Ctrl+F2 as switch, but I have a physical (hardware) switch on the side of my laptop.

E.g. this guide [http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794) makes my laptop crash after a few seconds. What can I do to make it work?

---

### Post by ddrichardson on 2007-08-17
Are you downloading the drivers from this post or are you using your own from your Windows installation?

---

### Post by kkjaergaard on 2007-08-17
> **ddrichardson said:**
> Are you downloading the drivers from this post or are you using your own from your Windows installation?

I used the drivers at [http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng](http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng) as descriped in the thread I refered to.

---

### Post by AlbinoButt on 2007-08-17
Kkjaergaard, the guide that you linked to uses the Windows 4965 driver and NDISWrapper. This isn't an ideal solution. Ideally, you would install the native linux driver. The guide can be found here:

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

I also have a hardware switch on my laptop, and this guide worked for me. You don't even have to follow all the steps on that thread because the latest Gutsy kernel (2.6.22-9-generic as of the time of this post) has the wireless drivers integrated already. So all you have to do is change your repositories to Gutsy, upgrade the kernel, and remove the repository links you added. (Basically, only follow steps 1, 2, and 4.)

---

### Post by kkjaergaard on 2007-08-17
> **AlbinoButt said:**
> Ideally, you would install the native linux driver. The guide can be found here:

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

I also have a hardware switch on my laptop, and this guide worked for me. You don't even have to follow all the steps on that thread because the latest Gutsy kernel (2.6.22-9-generic as of the time of this post) has the wireless drivers integrated already.

But then I have to switch to the Gutsy kernel. What are the differences (pros and cons) of switching?

Do you have any additional reading about switching kernel?

---

### Post by ddrichardson on 2007-08-17
Installing a native driver is the best solution but I think your problem realtes to the Windows driver not being the exact one needed. Did you have a driver with the system?

---

### Post by AlbinoButt on 2007-08-17
> **kkjaergaard said:**
> But then I have to switch to the Gutsy kernel. What are the differences (pros and cons) of switching?

Do you have any additional reading about switching kernel?

switching kernels might break stuff that used to work on your system, depending on your hardware. On the other hand, switching kernels might fix lots of problems you might have been experiencing. You can always just go back to your old kernel if it doesn't work out for you.

> **ddrichardson said:**
> Installing a native driver is the best solution but I think your problem realtes to the Windows driver not being the exact one needed. Did you have a driver with the system?

I do know that the 4965/NDISWrapper driver is known to have issues such as lock-ups, even when using the correct driver that came with the system.

---

### Post by kkjaergaard on 2007-08-17
> **AlbinoButt said:**
> I also have a hardware switch on my laptop, and this guide ([http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)) worked for me. You don't even have to follow all the steps on that thread because the latest Gutsy kernel (2.6.22-9-generic as of the time of this post) has the wireless drivers integrated already

So what you are saying is: switch kernel and it might work. When (during boot, start of ubuntu or later) did you turn on the network switch?

---

### Post by kkjaergaard on 2007-08-17
I typed lspci in the terminal, but it says:

...
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
...

Shouldn't it say something else than "Unknown device"?

---

### Post by kkjaergaard on 2007-08-17
Now it works. After installing linux-ubuntu-modules the wireless network works.

Thanks for your support and patience.

---

### Post by AlbinoButt on 2007-08-18
Glat to hear you got it working, kkjaergaard! :)

Once Gutsy comes out in October things like the 4965 wireless should work without having to do any fiddling around.

---

