---
title: "Lenovo ideapad 320 touch pad stops working after 5 seconds"
date: 2017-09-07
forum: Hardware
---

### Post by Crayboff on 2017-09-07
I believe the issue I'm having is a linux kernel/driver bug after all of the research I've performed so far. I hope you guys will be ok with me asking if anyone has any workarounds while I wait for smarter people than I are able to figure out a permanent fix. Here is my bug report: [https://bugzilla.kernel.org/show_bug.cgi?id=196863](https://bugzilla.kernel.org/show_bug.cgi?id=196863)

Device: Lenovo Ideapad 320-15ABR  
OS: Ubuntu 17.04  
Kernel: 4.13.0-041300-generic

When I tried fresh installations of Ubuntu 16.04, 17.04, and 17.10 beta daily build, my trackpad was undetected and completely unresponsive: [https://pastebin.com/raw/qdrjg2xD](https://pastebin.com/raw/qdrjg2xD)

Tried several fixes on the ubuntu forums and from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1708852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1708852) but the only thing that has seemingly made any progress was installing the latest mainline kernels. After installing 4.13.0-041300-generic (released Sept 3, 2017), the trackpad is not identified in the xinput results: [https://pastebin.com/raw/j8XwhV1A](https://pastebin.com/raw/j8XwhV1A)

My results are identical for the daily kernel build linux-image-4.13.0-999-generic_4.13.0-999.201709062201 (released Sept 7, 2017).

The issue now is that the trackpad only lasts a little over 5 seconds after starting up before it stops working entirely. You can see this happen in the syslog: [https://pastebin.com/raw/TgtAsXjh](https://pastebin.com/raw/TgtAsXjh)

Here is a snipped down version of the syslog to what I'm assuming is relevant. I believe the trackpad is only working when we see the error messages then stops once those end: [https://pastebin.com/raw/ckMteHhH](https://pastebin.com/raw/ckMteHhH) Though I could be missing something important.

I suspect the issue is similar to this submission: [https://bugzilla.kernel.org/show_bug.cgi?id=196761](https://bugzilla.kernel.org/show_bug.cgi?id=196761) but I have no idea how to attempt to implement this guy's fix.

I've tried several workarounds already including [a suggested DKMS patch](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1708852), adding [something about i8042.reset to a default command](https://askubuntu.com/a/764885/734266),

---

### Post by googleplex2 on 2017-10-14
I purchased this laptop at Best Buy 10/11/17, installed latest kernel and I experienced the exact same issue. I have done exactly everything stated above same issue. You get 5 seconds then the curser freezes and the trackpad no longer works.

Available to help troubleshoot... Advice needed. 

Device: Lenovo Ideapad 320-15ABR 
OS: Ubuntu 17.04 
Kernel: 4.13.0-041300-generic

---

### Post by jerome1872 on 2018-03-17
I third, also have levono ideapad 320s with same issue, trackpad works for about 5 seconds after logging in then stops working all of a sudden.

---

### Post by mörgæs on 2018-03-18
How does it work in a live boot of 18.04 (beta)?

---

