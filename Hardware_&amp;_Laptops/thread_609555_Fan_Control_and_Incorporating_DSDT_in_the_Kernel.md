---
title: "Fan Control and Incorporating DSDT in the Kernel"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by millsy on 2007-11-11
Hi all

Hope someone can help.  I have just got a Fujitsu-Siemens V3515 laptop from work and I'm trying to get the Fan control to work.  I've read the post [here]("http://ubuntuforums.org/showthread.php?t=482900&highlight=AMILO+Pro+V3515") and tried to follow the instructions but I've got terribly stuck.

1.  I'm running Feisty 7.04 and the post says that I have to "patch the kernel for DSDT".  I'm running Kernel 2.6.20-16 on my laptop (at least that's what Grub says - I don't really understand it that much).  How do I patch the Kernel to include DSDT or anything else for that matter?  I've googled till I dropped and can't find a simple guide to how to do this.  Please can someone provide an 'idiots' guide to 'patching the kernel' or is is simply not something that an 'idiot' can do?

2. If I try to view the contents of /proc/ I can't see anything.  Is this normal?  Does /proc not contain any files that can be viewed?

3.  I'd really like to *understand* how the linux kernel works - can anyone point me in the direction of a book or a website that can help?

---

### Post by santoxyz on 2007-11-26
[http://ubuntuforums.org/showthread.php?t=482900&highlight=v3515](http://ubuntuforums.org/showthread.php?t=482900&highlight=v3515)

---

### Post by mysticrider92 on 2007-11-26
I can't really help with the fan control problem, but santoxyz's guide should help with that.

About /proc: I am not a Linux expert, but I think /proc is a special setup that is not readable by the user. On my Arch Linux system, I can not see the contents of /proc either.

O'Reilly publishes some very good books about how Linux works ("Understanding the Linux Kernel" and "The Linux Kernel in a Nutshell" are two examples). There are also many good free books about this on the internet. [Here]("http://tldp.org/LDP/tlk/tlk-toc.html") is a slightly old one, but should still give you a good start. [Kernel Newbies.org]("http://kernelnewbies.org/") might have some of what you are looking for.

---

