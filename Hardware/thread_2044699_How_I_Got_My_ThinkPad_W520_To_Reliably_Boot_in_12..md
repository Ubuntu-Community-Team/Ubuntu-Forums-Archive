---
title: "How I Got My ThinkPad W520 To Reliably Boot in 12.04"
date: 2012-08-19
forum: Hardware
---

### Post by Kirk Schnable on 2012-08-19
Good afternoon Ubuntu Community

I'd just like to share a piece of wisdom I picked up today.  I've been troubleshooting Ubuntu 12.04 LTS on my ThinkPad W520 in my spare time for the past month.  I ran 10.04 LTS reliably for a year, then after installing 12.04 I had all manner of issues.

My ThinkPad has an nVidia Quadro 2000M discrete graphics card, which I had been blaming partially for the problems, especially with all the contradictory resources regarding nouveau vs. nvidia-current and nVidia Optimus.  But I digress.  I am running the Nouveau driver, and it's working great so far.

The laptop would not reliably boot.  It would sometimes show a blinking cursor, or a purple screen, or a black screen.  After awhile recovery mode didn't even work, it would freeze at the "starting udevd" phase.

The way I fixed my ThinkPad boot process was by editing /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="nox2apic quiet splash"
```

Then, obviously, running update-grub.

After adding the nox2apic switch, my laptop seems to reliably boot again.

A few other sources on the Internet confirm that this is an ongoing problem, not just with Ubuntu:
[https://bbs.archlinux.org/viewtopic.php?id=142191](https://bbs.archlinux.org/viewtopic.php?id=142191)
[https://bugzilla.redhat.com/show_bug.cgi?id=827164](https://bugzilla.redhat.com/show_bug.cgi?id=827164)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/776999](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/776999)

I hope to see this issue resolved soon, but I also hope that someone else out there with a ThinkPad W520 comes across this thread and it saves them some time.

Cheers,
Kirk

---

