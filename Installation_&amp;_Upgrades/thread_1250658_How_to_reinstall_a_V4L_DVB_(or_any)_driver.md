---
title: "How to reinstall a V4L DVB (or any) driver"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by derekweber on 2009-08-26
Howdy,

As part of setting up a MythTV box I started Ubuntu 8.10 and found that my tv tuner card (DVICO Dual Digital 4 version 2) wasn't supported and so I built and installed the drivers directly from the v4l-dvb mercurial repository.

When 9.04 came out I upgraded and everything worked fine, except that I noticed that with the kernel upgrade my v4l-dvb drivers stopped working, and I had to rebuild and install them again. And, in fact, with the recent upgrade of kernel drivers and headers I had to rebuild and reinstall them again.

Now, my understanding is that 9.04 now supports my tv tuner out of the box, so I'd like to know how can I revert my v4l-dvb drivers back to whatever 9.04 gives me, rather than my custom-built-and-installed drivers.

I've searched the forums and the web and nothing has come up.

Thanks for the help.

Derek.

---

### Post by mal on 2009-11-08
> **derekweber said:**
> Howdy,

As part of setting up a MythTV box I started Ubuntu 8.10 and found that my tv tuner card (DVICO Dual Digital 4 version 2) wasn't supported and so I built and installed the drivers directly from the v4l-dvb mercurial repository.

When 9.04 came out I upgraded and everything worked fine, except that I noticed that with the kernel upgrade my v4l-dvb drivers stopped working, and I had to rebuild and install them again. And, in fact, with the recent upgrade of kernel drivers and headers I had to rebuild and reinstall them again.

Now, my understanding is that 9.04 now supports my tv tuner out of the box, so I'd like to know how can I revert my v4l-dvb drivers back to whatever 9.04 gives me, rather than my custom-built-and-installed drivers.

I've searched the forums and the web and nothing has come up.

Thanks for the help.

Derek.

Derek,

It's been a long time since you submitted this request and you have undoubtedly already solved your problem, however, for the record, I have the same problem with 9.10 and the Dual Digital 4 not working properly, so I unsuccessfully tried to install the latest drivers and then had to revert to the original drivers.  As these drivers seem to be part of the kernel package, I simply reinstalled the kernel using Synaptic and this seemed to do the job.

Mal

---

### Post by derekweber on 2009-11-09
> It's been a long time since you submitted this request and you have undoubtedly already solved your problem, however, for the record, I have the same problem with 9.10 and the Dual Digital 4 not working properly, so I unsuccessfully tried to install the latest drivers and then had to revert to the original drivers. As these drivers seem to be part of the kernel package, I simply reinstalled the kernel using Synaptic and this seemed to do the job.

Mal

Hi Mal,

Thanks for the tip. I hadn't found a fix and had simply recompiled the drivers every time I updated the kernel. So the trick is to simply reinstall the kernel?

I'm upgrading to 9.10 right now, so I'll see if the new kernel does the trick for me.

Thanks very much, I appreciate the help.

---

### Post by mal on 2009-11-09
Derek,

I hope this works out for you.

Note, that I also uninstalled the compiled drivers before I reinstalled the kernel.  I can't recall exactly what the command was for the uninstall, but it's given in one of the "readme" or "install" text files in the source tree.  I'm not sure if this was really necessary, but it's probably good practice.

Mal

---

