---
title: "Question about Wacom tablet support."
date: 2015-10-31
forum: Hardware
---

### Post by at35z on 2015-10-31
Hi there,

I've recently bought a Wacom INTUOS Draw tablet, and when I plugged in, it wasn't working. I understood that since the tabled was released in 2015 and I was using Ubuntu 14.04. I read the [Linuxwacom](http://linuxwacom.sourceforge.net/wiki/index.php/Main_Page) site, but I would prefer not messing with that if not necessary.

My question is, is there a chance that my tablet will be supported in future Ubuntu releases, so should waiting for another release be enough or do I have to install these drivers manually anways? If it will be supported, will it be shown in changelogs specifically? Or 15.04 and 15.10 versions already support it?

Thanks in advance.

---

### Post by mörgæs on 2015-11-01
Hi, welcome to the fora.

I don't know Wacoms but it's likely that your old 14.04 is the problem. The best way to find out is to try a live boot of 15.10.

---

### Post by zeke2135 on 2015-11-01
Hello
As I understand it, the new models (e.g. CTH-490, CTH690) are scheduled to be supported in kernel 4.4. If I'm not mistaken 15.10 has kernel 4.2. There has been a [discussion]("http://sourceforge.net/p/linuxwacom/mailman/linuxwacom-discuss/thread/5612ED90.6090101@gmail.com/#msg34516798") in the linuxwacom-discuss mailing list about the new models. At one point the developers made pre-release source code available for download but apparently it is not currently available (at the original url anyway), maybe because even tho it basically worked, it had some problems.

---

### Post by at35z on 2015-11-01
> **mörgæs said:**
> Hi, welcome to the fora.

I don't know Wacoms but it's likely that your old 14.04 is the problem. The best way to find out is to try a live boot of 15.10.

I just tried that, not helped.

However, I visited the linuxwacom wiki once more and found out that these new models (mine is CTL-490) are *expected to work* with Linux kernel 4.4. I noticed this after trying and *failing* with 15.10, since that is based on Linux 4.2.

Basically, if Ubuntu 16.04 will be based on 4.4 (I guess it's really likely) then it should work on that.

---

### Post by Bucky Ball on 2015-11-01
Wacom are friendly and their older tablets work 'out of the box' so it is only a matter of time before the newer ones do also one would think. If you wanted to, you could try the [16.04 daily build ]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/")(expect the unexpected), 'Try Ubuntu, and check what kernel that is using or do some research and you should be able to dig it up.

* Did a little archeology and still looks like 4.2 [here]("http://packages.ubuntu.com/source/xenial/linux"), but might not be that way by next April when it is released I guess.

---

### Post by at35z on 2015-11-03
They will probably have a reason not to upgrade if they decide not to, but let's hope for the best in April!

---

### Post by Bucky Ball on 2015-11-03
Completely by coincidence I found out through another staff member on another thread that 14.04 LTS will actually get to the 4.2 kernel in February next year. FYI. :)

See [here]("https://wiki.ubuntu.com/Kernel/Support#A14.04.x_Ubuntu_Kernel_Support"). 14.04.4, the hardware enablement stack from Wily happens. Says in the chart at the top of that page that 15.10 has the 4.2 already.

---

### Post by at35z on 2015-11-04
> **Bucky Ball said:**
> Completely by coincidence I found out through another staff member on another thread that 14.04 LTS will actually get to the 4.2 kernel in February next year. FYI. :)

See [here]("https://wiki.ubuntu.com/Kernel/Support#A14.04.x_Ubuntu_Kernel_Support"). 14.04.4, the hardware enablement stack from Wily happens. Says in the chart at the top of that page that 15.10 has the 4.2 already.

Could this mean that 14.04 may even get 4.4?

---

### Post by Bucky Ball on 2015-11-04
> **at35z said:**
> Could this mean that 14.04 may even get 4.4?

14.04.5 point release has the kernel as 'TBD', to be decided, so who knows? ;)

---

