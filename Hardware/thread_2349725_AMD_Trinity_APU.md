---
title: "AMD Trinity APU"
date: 2017-01-17
forum: Hardware
---

### Post by alku1 on 2017-01-17
I have to bump this.

Im stuck with the same/similar problem.
I managed to set up my first linux (16.04) installation, but I had to use some grub modifications (nomodeset) like the original poster. Unfortunately, Im now stuck without the full hardware acceleration of my APU (AMD A4-5300 Trinity).
Is there anything I can do to fix this?

[ATTACH=CONFIG]273233[/ATTACH]

---

### Post by Yellow Pasque on 2017-01-17
> I had to use some grub modifications (nomodeset)

Why? You need to solve that issue. You're not going to get graphics acceleration using nomodeset. Try a newer kernel. Or maybe try a LiveUSB of Ubuntu 16.10 or the latest daily image of 17.04. Can you get it to start without nomodeset?

---

### Post by QIII on 2017-01-17
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2344351").

Please don't tag on to someone's older thread  Your problem may appear to be similar, but similar symptoms may arise from entirely different underlying causes.  Be fair both to yourself and the original post of the other thread by avoiding confusion.

Thanks.

---

### Post by alku1 on 2017-01-19
> **Temüjin said:**
> Why? You need to solve that issue. You're not going to get graphics acceleration using nomodeset. Try a newer kernel. Or maybe try a LiveUSB of Ubuntu 16.10 or the latest daily image of 17.04. Can you get it to start without nomodeset?

Thansk for your reply.
Well, Im aware that with the grub modification (radeon.modeset=0) I cant get the real deal. 

I just tried a live USB stick with 16.10. Unfortunately there I see the same issue that after the boot menu (try ubuntu without installation) I have a couple of purple seconds until my machine reboots without any notice.

I upgraded my kernel already to 4.9.4 following a guide I got here:
[https://docs.google.com/document/d/1HiIEPpPF9ycz7But8WafSO_Jaa_rS3wY53CURK9ciq8/edit](https://docs.google.com/document/d/1HiIEPpPF9ycz7But8WafSO_Jaa_rS3wY53CURK9ciq8/edit)

At this moment I simply dont know what else to try anymore and Im pretty fed up with my Ubuntu installation. I got everything else to work but having almost 80% CPU usage while using VNC remote is just a bad joke.

[EDIT] BUmp!
I cant believe that Im the only one with that issue and that there is no fix for Ubuntu?! :mad:

---

