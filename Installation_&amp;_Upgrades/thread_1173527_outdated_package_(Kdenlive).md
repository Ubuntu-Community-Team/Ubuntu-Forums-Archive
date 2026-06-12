---
title: "outdated package? (Kdenlive)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by oiio on 2009-05-29
hello everybody,

i just installed Kdenlive and installation went well (ubuntu 8.10, followed the instructions on 'http://www.kdenlive.org/forum/how-install-kdenlive-kubuntu-810')

when I start it up it shows some 'hello-what-preferences-would-you-like'-windows and then when the real program starts it crashes with the message:

> A Fatal Error Occurred
The application Kdenlive (kdenlive) crashed and caused the signal 11 (SIGSEGV).

i searched the web a bit and found the following:

> Thank you for your report!

However, processing it in order to get sufficient information for the
developers failed (it does not generate an useful symbolic stack trace). This
might be caused by some outdated packages which were installed on your system
at the time of the report:

libgd2-noxpm: installed version None, latest version: 2.0.36~rc1~dfsg-3ubuntu1
libavcodec52: installed version None, latest version: 3:0.svn20090303-1ubuntu4
libavutil49: installed version None, latest version: 3:0.svn20090303-1ubuntu4

Please upgrade your system to the latest package versions. If you still
encounter the crash, please file a new report.

that first one is ok in my synaptic,
the *libavcodec52* and *libavutil49* though have a 20081115-version. When i uninstall them and re-install them they keep getting the old version. How do I solve this ?

---

### Post by harlock59 on 2009-09-13
Hello,

i wonder if there could be a website to report outdated ubuntu apt/repositories packages

for example, midori is also outdated (0.1.2) latest is (0.1.10)

i don't know who updates the packages, i don't know if those packages have to be verified/modified to fit with apt tools (treatment/adaptation to get installed from command lines, bug verified) i guess that depends also on which repositories they are put in (official /or side repositories)

---

### Post by snowpine on 2009-09-13
Hi oiio, the answer is simple: You need to install kdenlive from the official Ubuntu repositories. This will automatically satisfy all "dependencies" and you will not get the error message.

```
sudo apt-get update
sudo apt-get install kdenlive
```

You are getting the error message because you're trying to install software with 2009 dependencies on an older version of Ubuntu; 8.10 means it uses whichever versions of packages were stable in October 2008.

---

### Post by snowpine on 2009-09-13
> **harlock59 said:**
> Hello,

i wonder if there could be a website to report outdated ubuntu apt/repositories packages

for example, midori is also outdated (0.1.2) latest is (0.1.10)

i don't know who updates the packages, i don't know if those packages have to be verified/modified to fit with apt tools (treatment/adaptation to get installed from command lines, bug verified) i guess that depends also on which repositories they are put in (official /or side repositories)

Harlock, you will get a newer version of Midori (0.1.09 I believe) when you upgrade to Karmic next month. Ubuntu never upgrades software once a release has been finalized, except for minor bug fixes and security upgrades.

---

