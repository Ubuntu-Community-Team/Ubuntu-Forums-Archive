---
title: "Dpkg stucks on postrm"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by paradigmatic on 2006-01-19
Hello,

I tried to install some gst plugins and the install process froze during post-install. The culprit seems to be a 'gst-compprep-0.8' process which I cannot kill since it is stuck on IO (ps status D, confirmed by 'lsof').

If I kill the dpkg process and I try apt-get again, I get the msg:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

If I run 'dpkg ...', as told above the configuration process freeze again. If I try to remove the package with 'dpkg --remove...' same problem...

Is there a way to remove a package avoiding the postrm stuff ?

Thanks,

jl

---

### Post by paradigmatic on 2006-01-24
I fixed the problem, rebooting the machine and launching dpkg from a console login. I think that 'gst-comprep' stucks in my install when I'm using some gstreamer parts.

---

