---
title: "pm-suspend does not work"
date: 2019-02-26
forum: Hardware
---

### Post by zeke2135 on 2019-02-26
I have a gygabyte brix mini pc running ubuntu 16.04.6, on which pm-suspend is not working presently. The command gets partway through and seems to hang on a step related to video. BTW I don't know if it's related, but occasionally I've noticed that vbetool is running and taking up 100% cpu time according to top.

I would appreciate any help getting this to work if possible. 

Here are the last two entries from pm-suspend.log:

```

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
No quirk database entry for this system, using default.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0 
```
Here are some details of my system:
Intel(R) Core(TM) i3-4010U CPU @ 1.70GHz

VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

4.15.0-45-generic

thanks

---

### Post by TheFu on 2019-02-26
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) might be helpful.  Don't know.

I'd check that the correct driver, i915, is being used.  I have a slightly newer i915 setup and suspend works perfectly every time, out of the box.
* 4.15.0-45-generic
* 16.04.6
* i3-5015U (Broadwell GT2)

---

### Post by zeke2135 on 2019-02-26
Thanks for the suggestions. It looks like i915 is used. 

```
i915                 1630208  1
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
drm                   401408  3 drm_kms_helper,i915
video                  45056  1 i915
```

I am not sure I followed the info in the link. However, when I used the command implementing pm_trace, all I found out is that yes, pm-suspend hung up. There didn't seem to be any lines of output from dmesg after the initial one warning that pm_trace alters the system clock. I had to interrupt w/ ^C after a couple of minutes of the command not returning. pm-suspend.log had the same output as I included in the original post.

---

### Post by TheFu on 2019-02-26
Brix seems to have some issues. [https://bbs.archlinux.org/viewtopic.php?id=192821](https://bbs.archlinux.org/viewtopic.php?id=192821) has some grub and BIOS options to try out.

---

### Post by zeke2135 on 2019-02-26
So, the problem is definitely related to vbetool. If I uninstall it, the problem goes away. I don't know if it's vbetool that's the problem, or the bios and/or kernel that are causing problems for vbetool. 

I am willing to do w/o vbetool.  My understanding is that "[COLOR=#333333][FONT=Ubuntu]vbetool exists primarily in order to increase the chances of successfully recovering video state after an ACPI S3 suspend.".  See  [/FONT][/COLOR]https://launchpad.net/ubuntu/+source/vbetool  

This machine actually boots into multi-user.target and is a "headless" server, so I am guessing I will not have problems. Altho that is truly a guess, as I don't know how this stuff works. Anyway, I am going to declare victory for now, and move on. 

Thanks TheFu for your suggestions.

---

