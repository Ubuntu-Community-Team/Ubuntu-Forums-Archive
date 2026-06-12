---
title: "sound on HP OmniBook 4150"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by bernardfrancois on 2005-12-27
Hi,

I'm trying to make the sound on my HP Omnibook 4150 laptop working.
I found more information on this site: [http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html?page=1)

A quote:
> Using The Kernel Modules (OSS/Free)

Following the advice of other 4150 owners, I first set up the OSS/Free sound modules built from the 2.2.19 kernel sources. I configured the audio system by adding these lines to /etc/modules.conf:

alias sound-slot-0 ad1848
options sound dmabuf=1
alias synth0 opl3
options opl3 io=0x388
options ad1848 io=0x530 irq=5 dma=1 dma2=0

This configuration gave me PCM and CD audio, along with the well-known OPL3 FM synthesizer.

So, what I did is creating a file /etc/modprobe.conf (which is the equivalent for /etc/modules.conf on ubuntu - which I found in 'man modprobe' and 'man modprobe.conf') with the contents from the site.

After rebooting, I noticed that the system beep when executing **echo -e '\a'** doesn't work any more, but no other changes occured (the sound still doesn't work).

To ensure you that I have the same audio controller as discussed in the article:
```
ber@ubuntu:~$ lspci | grep audio
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)

```

Can anyone help me out how I need to make the sound work? I'm unexperienced at installing hardware which wasn't auto-detected. I think I need to replace the Enlightement Sound Daemon by another one, but I don't know how to do this or how to enable and configure it.

It would be great if someone could help me out to have a little more understaning of configuring sound in linux, and to make the sound on my laptop work.

---

### Post by bernardfrancois on 2005-12-27
I posted this thread twice by accident. Can a moderator please remove this duplicate?

---

