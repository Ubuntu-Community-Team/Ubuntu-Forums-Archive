---
title: "PCMCIA NEC FastEthernet card (AX88190 chipset) not recognized by Ubuntu 6.10"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by mlauritse on 2007-04-03
Hello,

First of all, my system description: Ubuntu desktop 6.10 on a Sony PCG-F104K. (Standard Installation - I haven't changed anything - you can't do much without a network connection).

Myself: Java software developer, but always on windows, figured I'd learn something about how computers really work - which is much easier with Linux than with Windows. I know basic C, but I don't particularly want to recompile the kernel if I don't have to (yet). 

When I insert my NEC PCMCIA FastEthernet card, the syslog shows the following message:
-- 
this is an AX88190 card!
use axnet_cs instead
-- 

lsmod shows that only pcnet_cs is loaded, axnet_cs is not in the list. (axnet_cs does not seem to exist on the machine - there are no entries in /proc/modules).

I tried booting with the Knoppix 5.1 DVD, and it detects the card just fine. (I would prefer using a real distribution though, in the long term, I don't really want to work off a LiveCD).

1) How can I load axnet_cs? I guess I need a file I can load using "insmod"?
2) Why doesn't "cardmgr" seem to be available? I guess I need it (knoppix seems to be using it)? Is it just me who can't find it?
3) I found a note somewhere on kernel.org saying that the AX88190 chipset was supported from kernel 2.6.17-rc3 or so... I'll try to dig up that link again and add it here.

Thanks in advance - I spent quite a lot of time looking for the answer to these, but I haven't found anything, which probably means I don't know where to look. The hardware guides on various ubuntu sites didn't seem to contain information this detailed, but again, that might just be me looking in the wrong place.

Thanks for any help,
Morten

---

### Post by Jussi Kukkonen on 2007-04-03
Edgy (6.10) should have that driver, in kernel 2.6.17-10, accroding to packages.ubuntu.com

Try loading it by hand first: *sudo modprobe axnet_cs*. If it seems to work, add the module into */etc/modules* for automatic loading.

EDIT: I just realized that the current kernel in Edgy is 2.6.17-11. Weird. It's possible that the file is in the new kernel too, and packages.ubuntu.com is just broken. I suggest you try.

---

### Post by mlauritse on 2007-04-03
Thanks for the suggestion - I'll give it a try! :-)

---

### Post by mlauritse on 2007-04-03
Just another quick question:

I can't find neither axnet_cs nor cardmgr in

[http://packages.ubuntu.com/edgy/allpackages.en.txt.gz](http://packages.ubuntu.com/edgy/allpackages.en.txt.gz)

am I looking in the wrong place?

The kernel installed on my machine is 2.6.17-10-generic.

Am posting this from my windows machine, I still need to try out your suggestion.

Thanks!

---

### Post by Jussi Kukkonen on 2007-04-03
You are searching package names, but the driver is included in the linux kernel package. Search for the file axnet_cs.ko:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=axnet_cs.ko&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=axnet_cs.ko&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

---

### Post by mlauritse on 2007-04-04
OK - that looks like something I should be able to locate on my machine...

I'll try your suggestion this evening.

Thanks!

---

### Post by mlauritse on 2007-04-04
Hi again,

I tried "sudo modprobe axnet_cs", which worked, I now have the module loaded.

I added it to /etc/modules, rebooted, and it is indeed loaded at boot time. Cool!

I tried unplugging the pcmcia card and putting it back in, but I still get the "use axnet_cs instead" message, along with some more:

"
pccard: PCMCIA card inserted into slot 0
pcmcia: registering new device pcmcia0.0
pcnet_cs: this is an AX88190 card!
pcnet_cs: use axnet_cs instead.
pcnet_cs: unable to read hardware net address for io base 0x300
pcnet_cs: this is an AX88190 card!
pcnet_cs: use axnet_cs instead.
pcnet_cs: unable to read hardware net address for io base 0x300
"

How do I get the kernel to use axnet instead of pcnet?

Do I have to somehow unload the pcnet_cs module? I tried removing pcnet_cs ("sudo modprobe -r pcnet_cs"), which worked fine (it no longer shows up in lsmod), but reinserting the card reloads pcnet_cs.

--
Concerning "cardmgr":

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=cardmgr&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=cardmgr&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

seems to indicate that cardmgr should be available in 6.10, but I can't find it under /sbin/cardmgr - is there something I need to do to make it available?

Thanks,
Morten

---

### Post by Jussi Kukkonen on 2007-04-08
Try adding *"blacklist pcnet_cs"* into /etc/modprobe.d/blacklist. That should prevent the driver from being loaded.

---

### Post by mlauritse on 2007-04-09
Hi,

Blacklisting the pcnet_cs module effectively prevented it from being loaded.

Now, when I insert the card, I get the message
--
pccard: PCMCIA card inserted into slot 0
pcmcia: registering new device pcmcia0.0
--

but that's it. No error messages, but unfortunately, the network card still isn't recognized as such.

Is there somewhere I can instruct the kernel on which driver to use for the device?

Thanks agian,
Morten

---

### Post by ErikPoel on 2007-06-09
> **mlauritse said:**
> Hi,

Blacklisting the pcnet_cs module effectively prevented it from being loaded.

Now, when I insert the card, I get the message
--
pccard: PCMCIA card inserted into slot 0
pcmcia: registering new device pcmcia0.0
--

but that's it. No error messages, but unfortunately, the network card still isn't recognized as such.

Is there somewhere I can instruct the kernel on which driver to use for the device?

Thanks agian,
Morten

Hi,
Did you get any further on this? I'm having exactly the same problem.
Thanks,
Erik

---

### Post by ErikPoel on 2007-06-09
Problem solved. To get eth0, you need to run cardmgr. I've added 'cardmgr' to the /etc/rc.local file, it works fine now. Hope it helps you as well.

---

### Post by mlauritse on 2007-06-10
Hi,

Actually, I misstated my configuration a bit. :-(

I was running XUbuntu 6.10, not Ubuntu 6.10.

When Ubuntu 7.04 came out, I tried installing that, and my PCMCIA card worked without any interverntion on my part.

I never did figure out why it wasn't working, so I'm afraid I can't help you.

Try posting your own thread to this forum, stating your configuration more accurately than I did.

Good luck,
Morten

---

### Post by panda84 on 2008-03-22
If someone still has this problem please be sure to read this thread first:
[http://ubuntuforums.org/showthread.php?p=4563872#post4563872](http://ubuntuforums.org/showthread.php?p=4563872#post4563872)

NOTE: cardmgr is part of the obsoleted pcmcia-cs package!

---

