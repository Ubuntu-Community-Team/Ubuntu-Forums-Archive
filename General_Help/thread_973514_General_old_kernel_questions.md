---
title: "General old kernel questions"
date: 2008-11-06
forum: General Help
---

### Post by ezramorris on 2008-11-06
Hi,
After upgrading to Intrepid, I decided to do some cleaning up of old kernels, etc, however, I do have some outstanding questions.

1.) How do I get Intrepid's "Last Known Boot" feature to work, since I upgraded rather than did a fresh install?

2.) Is there a particular reason why the current generic kernel is 2.6.27-**7**-generic, but the current rt kernel is 2.6.27-**3**-rt?

3.) If I got "Last known boot" working, would it still allow me to select between the generic and rt kernels, as well as my other operating systems?

4.) Finally, I think there are still some traces of old kernels around. Occasionally I have to resize or reformat my swap, which involves running
```
sudo update-initramfs -uk all
```
but I get the following output:
```
$ sudo update-initramfs -uk all
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
update-initramfs: Generating /boot/initrd.img-2.6.27-3-rt
update-initramfs: Generating /boot/initrd.img-2.6.24-zen4
update-initramfs: Generating /boot/initrd.img-2.6.20-16-lowlatency
Cannot find /lib/modules/2.6.20-16-lowlatency
update-initramfs: failed for /boot/initrd.img-2.6.20-16-lowlatency
```
I have neither the lowlatency or the zen4 kernel installed, or at least shouldn't. Any ideas how I can get rid of the traces?
```
$ apt-cache policy linux-image-2.6.20-16-lowlatency
linux-image-2.6.20-16-lowlatency:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.6.20-16.33 0
        100 /var/lib/dpkg/status
$ apt-cache policy linux-image-2.6.24-zen4
linux-image-2.6.24-zen4:
  Installed: (none)
  Candidate: (none)
  Version table:
     i386 0
        100 /var/lib/dpkg/status
$ apt-cache search linux-image*
alsa-base - ALSA driver configuration files
linux-image - Generic Linux kernel image.
linux-image-2.6.25-2-386 - Linux kernel image for version 2.6.25 on i386
linux-image-386 - Linux kernel image on 386.
linux-image-debug-2.6.25-2-386 - Linux kernel debug image for version 2.6.25 on i386
linux-image-debug-386 - Linux kernel debug image for 386 kernel image
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
linux-image-2.6.27-3-rt - Linux kernel image for version 2.6.27 on Ingo Molnar's full real time preemption patch (2.6.26.5-rt9)
linux-image-rt - Rt Linux kernel image
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
linux-image-2.6.27-7-generic - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-7-server - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-7-virtual - Linux kernel image for version 2.6.27 on x86/x86_64
```

Any help would be much appreciated; I've been meaning to tidy up for a while.

Thanks in advance.

---

### Post by drs305 on 2008-11-06
Yes, you can specify menu.lst to use the 'last used' kernel or OS, and still retain the option to select another kernel or OS during boot. You seem comfortable with the command line, but to be honest, it's just easier to explain with StartUp-Manager. Install 'startupmanager' then crank it up via System, Admin, StartUp-Manager. In the boot options, in the Default operating system, scroll down to 'last used'. If you leave the timeout value intact, the menu will still display for that many seconds before continuing.

(As for what the above does in menu.lst, it changes "default 0" to "default saved" and then places a "savedefault" line in the section of the kernel/OS last booted.

Have you checked in synaptic under "linux-image-XXXX" to see what kernels might be remaining there. Since the status reflects that no old ones are installed they shouldn't be listed there but you might as well check. I'd recommend keeping the current kernel plus one old one that works.

If you have any questions about StartUp-Manager there is a link in my signature line.

---

### Post by ezramorris on 2008-11-06
> **drs305 said:**
> Yes, you can specify menu.lst to use the 'last used' kernel or OS, and still retain the option to select another kernel or OS during boot.
Hi,
Thanks for your reply. I actually meant the whole new Intrepid concept of Ubuntu automatically removing all old kernels apart from the current one and the previous one. However, as I was looking for a [_link for you_]("https://wiki.ubuntu.com/KernelTeam/removing-old-kernels"), I found the answer...

> **drs305 said:**
> Have you checked in synaptic under "linux-image-XXXX" to see what kernels might be remaining there.

I have. The zen4 and lowlatency kernels are listed there, although they are marked as not installed, and they do not have a candidate.

---

### Post by drs305 on 2008-11-06
Thanks for the link. I knew it hadn't been implemented by default in Intrepid but hadn't seen the link you posted.

---

### Post by ezramorris on 2008-11-06
> **drs305 said:**
> Thanks for the link. I knew it hadn't been implemented by default in Intrepid but hadn't seen the link you posted.

Yeah, I was the other way round. I've been following it but didn't realise it hadn't been implemented by default in Final.

---

