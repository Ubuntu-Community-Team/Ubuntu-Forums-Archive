---
title: "Low screen resolution on Lenovo ThinkPad T460s"
date: 2018-02-20
forum: Hardware
---

### Post by gstover on 2018-02-20
I had a screen resolution problem with my T460s.  I found a work-around by re-installing Ubuntu 16.04.  Here's what happened in the hopes that someone knows how to fix it, or at least debug it, if it happens again (which I'm afraid it will).

Thanks ahead of time for any solution or future debugging help you can provide.

Computer = Lenovo ThinkPad T460s
OS = Ubuntu 16.04 LTS / 64-bit
CPU = Intel Core i5-6200U @ 2.30Ghz x 4
Graphics = Intel HD Graphics 520 (Skylake GT2)
Memory = 19 GiB

Computer is about 1.5 years old.  Came with Windows 10, but I've run Ubuntu 16.04 on it for the last few months.  (Single boot, not dual-boot.  Blew away Windows 10.)

Up to when I shutdown on Sunday night, built-in screen resolution was 2560 * 1440 as expected & as always had been.

When I booted on Monday, resolution was much lower.  Based on how terminal window, Settings window, Shutdown dialog, & some others nearly filled the screen, I estimate the resolution was maybe 1440 * 900.

SYMPTOMS & WHAT I TRIED

The Settings / Displays dialog claimed that the resolution was 2560 * 1440, but it wasn't.  I could lower the resolution, but anything lower was unusable (couldn't even see the buttons to accept the new resolution).  Allowing the change to timeout & return to "2560 * 1440" stayed at the low resolution (not 2560 * 1440).

Rebooted into BIOS.  Ran check on screen.  Passed.
Increased graphics memory from 256 MiB to 512 GiB.  Rebooted into OS. No change.

Plugged in external monitor via HDMI.  It displayed at its resolution (1920 * 1080), but resolution of built-in monitor was still low.

Searched web for people with similar problems.  Found some similar stuff, but solutions either didn't work for me (didn't even seem applicable) or their descriptions assumed knowledge of graphics that I don't have, so I did it wrong.  (My knowledge of X11 is minimal & maybe outdated.  For example, I expected to see an /etc/X11/xorg.conf, but there's none.)

RELEVANT EVIDENCE (MAYBE)

I use the computer heavily, frequently.  Until booting on Monday, screen resolution has always been 2560 * 1440.

It did some Ubuntu updates over the weekend.  Maybe one of them caused the problem.  However, I thought I had rebooted after them with no problem.  (I could be wrong.  Maybe the only reboot after one of the updates was when I shutdown on Sunday night, booted on Monday.)

I have other Ubuntu machines.  They also did updates & reboots over the weekend but didn't encounter problems.  But they aren't T460s.

When problem was happening, /var/log/Xorg.0.log had earlier sections that showed a bunch of Modeset lines including 2560x1440, but a later section did not include that resolution.  Highest resolution in the later section was 1920x1440.  (But I know nearly nothing about graphics, so I don't know whether that log file is created anew each boot, appended to, or what.)

Thanks again for your time.

---

### Post by tinylagarto on 2018-02-20
What is the output of:

```
uname -a

```
from a terminal?

That will tell us what kernel is in use.

---

### Post by gstover on 2018-02-21
```

[FONT=courier new]$ uname -a
Linux november 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ 
[/FONT]
```

---

### Post by tinylagarto on 2018-02-21
Maybe it is not your case but you could try to boot into an older kernel to see if it works normally.

Do you have older kernels on your system?

```
dpkg --list | grep linux-image
```

The command above will show what kernels are installed. Type it into a terminal and later post the output here in CODE tags.

---

### Post by gstover on 2018-02-21
```
$ dpkg --list | grep linux-image
ii  linux-image-4.10.0-28-generic              4.10.0-28.32~16.04.2                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-32-generic              4.13.0-32.35~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic        4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-32-generic        4.13.0-32.35~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04              4.13.0.32.52                                 amd64        Generic Linux kernel image
$ 
```

Thank you for your help, ivanovnegro2.  So I have both the 4.10 & the 4.13 kernels installed?  I'm surprised; since it's a recent (re)install, & I didn't allow it to run updates, I thought there would be just one.

If I needed to boot into the older kernel, how would I do that?
If the problem happens again, are there clues or debugging information I could get from X11?

---

### Post by tinylagarto on 2018-02-22
> **gstover said:**
> 

If I needed to boot into the older kernel, how would I do that?


Yep, that is what I wanted you to do. 

Now let's try that.

Reboot your computer and at boot press the shift button, you should see the Grub menu, now select an older kernel entry from there, preferably the 4.10 kernel and report back.

---

