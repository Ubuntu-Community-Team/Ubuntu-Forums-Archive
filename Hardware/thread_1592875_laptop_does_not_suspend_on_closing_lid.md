---
title: "laptop does not suspend on closing lid"
date: 2010-10-11
forum: Hardware
---

### Post by claracc on 2010-10-11
Hp compaq 6720 s laptop,  VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). kernel 2.6.32-25-generic

I have upgraded to Lucid Lynx from Karmic Koala, in power manager I have marked option on close the lid suspend laptop (general, battery, current adapter), but when close lid, laptop does not suspend. In karmic koala it worked (kernel 2.6.31-22)

I have to suspend laptop from xterm: sudo pm-suspend.

Where I can see to fix behaviour?, any script?, is it a kernel issue?

Thanks in advance

---

### Post by mok0 on 2010-10-11
I have the same problem, on a Dell Mini 10, with a freshly installed 10.04 Lucid Lynx.

There is another thread here in the forum discussion the issue:
[http://ubuntuforums.org/showthread.php?t=1490501]("http://ubuntuforums.org/showthread.php?t=1490501")

---

### Post by claracc on 2010-10-11
Thanks, I have read the thread you indicate.

It seems that there is not a working workaround yet and it seems a related kernel issue.

I have seen my sleep file in /proc/acpi and it is:

S0 S3 S4 S5

I don't know what does it mean, could someone explain please?

---

### Post by claracc on 2010-10-11
This is the bug found corresponding to the suspension problem: [https://bugs.launchpad.net/ubuntu/+bug/44058?comments=all](https://bugs.launchpad.net/ubuntu/+bug/44058?comments=all), unfortunately without any solution yet.

I hope a workaround will be find soon.

---

### Post by ERIC H on 2010-10-12
> **claracc said:**
> Hp compaq 6720 s laptop,  VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). kernel 2.6.32-25-generic

I have upgraded to Lucid Lynx from Karmic Koala, in power manager I have marked option on close the lid suspend laptop (general, battery, current adapter), but when close lid, laptop does not suspend. In karmic koala it worked (kernel 2.6.31-22)

I have to suspend laptop from xterm: sudo pm-suspend.

Where I can see to fix behaviour?, any script?, is it a kernel issue?

Thanks in advance

Was this working for you before the upgrade? I have an HP 6510 that suffers from this issue while on AC power, though when unplugged and running on battery it properly goes into suspension when lid is closed. Happened in both 10.04 and 10.10.

---

### Post by claracc on 2010-10-12
When I was on karmic koala, laptop suspended when close lid on AC power and also when running on battery.

I have tried what you have said, to unplug laptop, running on battery, close the lid and laptop suspends (lucid lynx), but if running on AC power, when I close lid it doesn't suspend.

---

### Post by Hack.The.Pow. on 2010-10-29
bump.  any solution for this?

Im running 10.10 with kernel 2.6.35-02063507-generic on a dell studio xps 1640.

I can suspend normally when I select the option from the shut down menu but when i just shut the lid my screen goes black and i can't access anything

---

### Post by frogotronic on 2011-02-17
Hello,

  I've been digging around for a solution to this bug.  I think its a bug in PM-UTILS and **not** a kernel bug.  I've filed/updated the bug report here: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/372824](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/372824)

There is also a discussion of laptop-mode-tools & pm-utils package here: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)

---

### Post by lpwaqas on 2011-09-16
> **cement_head said:**
> Hello,

  I've been digging around for a solution to this bug.  I think its a bug in PM-UTILS and **not** a kernel bug.  I've filed/updated the bug report here: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/372824](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/372824)

There is also a discussion of laptop-mode-tools & pm-utils package here: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)
You sure that from the battery/power preferences, you have already selected "Suspend" for the when the laptop lid is closed.

---

### Post by utnubuuser on 2011-09-16
the only thing that's worked on my thinkpad is setting the "nomodeset" kernel parameter.

The easiest way to test it is to interupt the grub-menu at boot by pressing "e", then using the arrow keys to navigate to the end of the line beginning with "linux... and adding "nomodeset", (without the quotation marks), after "quiet splash", then follow the onscreen instructions to resume boot.

---

