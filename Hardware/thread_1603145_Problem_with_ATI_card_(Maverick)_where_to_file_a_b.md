---
title: "Problem with ATI card (Maverick): where to file a bug?"
date: 2010-10-22
forum: Hardware
---

### Post by André Oliva on 2010-10-22
I have a Dell Inspiron 1721 laptop, that includes an ATI Radeon RS690M Radeon X1200 series. In Lucid I have good (but not perfect) 3d acceleration, but in Maverick I have almost no 3d acceleration working properly. When I try to run glxgears, a blank window appears, and when I run *glxinfo | grep rendering* I get *direct rendering: Yes*. 3d acceleration *must* be working, but it doesn't. 2d acceleration is perfect. I use the default drivers xserver-xorg-video-ati and xserver-xorg-video-radeon. I have no choice of installing any proprietary drivers (ATI says that they "are no longer supported").

I have searched many times for a solution unsuccesfully. My question is: where is the right place to file a bug? X.org? Kernel.org? Launchpad? In case that is Kernel.org or X.org, what information can give to them (because they are not directly related to Ubuntu)?

I want to file a bug because I still have 10.04 LTS in one partition and 10.10 in another one. The same drivers in Lucid are working acceptably well.

---

### Post by Fafler on 2010-10-22
Launchpad, as it seems to be Ubuntu specific. All of us with theese cards seem to have really bad 3D performance.

Try these drivers instead:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

But expect your machine to crash or stop working. It's fixable if you know your terminal.

---

### Post by André Oliva on 2010-10-22
Thanks, I'll try them and post here my results.

---

### Post by André Oliva on 2010-10-23
I added the PPA's to my software sources, then I updated all the packages via update manager. But it didn't worked. I still can't see anything when I run glxgears, or compiz. I don't understand why a driver that is suposed to work better and better in each Ubuntu release, suddenly becomes unusable. I will try now to file a bug here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bugs?start=75](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bugs?start=75), and I'll post here if I get a better result...

---

### Post by André Oliva on 2010-10-24
I filed a bug in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991)

I hope that this problem will be solved soon. While this happens I have to use Lucid.

I invite everybody that has the same problem to mark "this bug also affects me" in launchpad.

---

### Post by André Oliva on 2010-11-07
The problem **is not** the radeon driver, but the kernel mode-setting. (see comment #6 of the [bug that I reported]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991") in Launchpad). When I turned off the kernel mode-setting, 3d acceleration finally worked.  The instructions for how to turn off the KMS are here: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) . I will file a bug against Linux Kernel in Launchpad.

I wanted to try the Unity interface on Maverick. Even with 3d acceleration enabled and working, *it is still not working*. In the release notes of Maverick it is clarified that Unity may not work on some ATI cards. However, I hope that in the next release (11.04), that will be using Unity for the desktop edition by default, this issue may be solved (I read that Unity-desktop will use compiz, and compiz works on my card).

---

