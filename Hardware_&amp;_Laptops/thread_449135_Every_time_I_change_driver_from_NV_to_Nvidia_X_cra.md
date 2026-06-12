---
title: "Every time I change driver from NV to Nvidia X crashes"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by justinae on 2007-05-19
I have repeatedly installed the latest driver from the Nvidia website (after purging the nvidia-glx). 

The line in my xorg.conf file still says:

Driver     "nv"

instead of "nvidia".

Every time I change it myself it crashes X and I have to change it back to "nv" to get X back.

Am I missing something. I have both the nvidia install log and my most recent xorg log if those would be helpful.

many thanx!

ps. how do i post code into the thread as a scrolling text box so the thread isn't super long?

---

### Post by Djembe on 2007-05-20
> **justinae said:**
> I have repeatedly installed the latest driver from the Nvidia website (after purging the nvidia-glx). 

The line in my xorg.conf file still says:

Driver     "nv"

instead of "nvidia".

Every time I change it myself it crashes X and I have to change it back to "nv" to get X back.

Am I missing something. I have both the nvidia install log and my most recent xorg log if those would be helpful.

many thanx!

ps. how do i post code into the thread as a scrolling text box so the thread isn't super long?

I had that issue when I compiled a 2.6.21 kernel, and I couldn't figure out how to fix it, so I just trashed the new kernel.  and you can a text box by using code tags- put these: {code} {/code} (except with normal brackets) around the text you want in the box

---

### Post by justinae on 2007-05-20
I think i've determined that I am experiencing the bug where xorg version reported gets changed from 7.2 to 1.*. So the nvnews forum said this:

```
1.0-9755 and older on xorg-server-1.3 and its release candidates

The 1.3 series of the X.org server has a bug where the version reported changed from 7.2.* to 1.*. This confuses nvidia-installer into thinking that your X server is very old and it installs the X modules in the wrong place. To work around this problem, use the following options:

    # sh NVIDIA-Linux-version.run --x-module-path=`X -showDefaultModulePath 2>&1 | cut -d, -f1` --x-library-path=`X -showDefaultLibPath 2>&1`

```

Since I am pretty new to Linux, I typed in exactly what is there and it showed a text menu and brought me right back to my command prompt. Am I supposed to type exactly what is there or is "showDefaultModulePath" supposed to be something specific to my system? And if so what are those values supposed to be?

Also, my card is a GeForce 5200 and AGP. Does it make a difference that it's AGP?

many thanx!

---

