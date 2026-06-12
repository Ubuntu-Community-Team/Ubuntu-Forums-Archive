---
title: "HP G6000 booting problem"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by Akria on 2008-01-03
Whoa, nice emoticons. I like the guitar one a lot. :)
Sorry. Momentary distraction.

Anyway, I hate to have to write this post, but Linux is more important than my pride (I hate starting off accounts by asking for help).

Anyway, I got an HP G6000 laptop for Christmas to replace my old one, which had lasted me for four years or so. The last one was pitiful (192 MB of RAM, 1.7 GHz processor) but I nonetheless managed to get a triple-boot system of Windows XP Home Edition, Kubuntu and Puppy Linux (although the last one didn't work very well; neither did Kubuntu, for that matter, but it at least booted fine).

Anyway, this laptop's currently running Windows Vista Home Premium Edition (boo, hiss, glare) and, understandably, I want to move to a Linux distribution in place of yet another insecure and non-open source Windows OS. My first thought was Ubuntu, of course, and that was the one I tried first.

I tried two LiveCDs - one 32-bit, one 64-bit - and came across a problem I haven't experienced before: neither would boot.
Well, that's inaccurate - they would boot, but upon the point where they would normally enter the graphic environment (which I can't seem to stop on the LiveCDs, which seems strange to me; there should at least be the option to just boot into a CLI) I don't actually see anything, or at least nothing that should be there. It doesn't go to a black screen, but instead to what I can only describe as a screen which looks like it's had a hammer taken to it and then had liquified seaweed poured down it.
In short, there is massive screen corruption, mostly green, which looks uncomfortably as if the screen is damaged (it isn't, of course).

I've tried this with both Feisty and Gutsy, both 32-bit and 64-bit editions, and the same thing happened each time.
I haven't tried an alternate install CD yet so that I can actually install, but I have used the Windows executable which installs Debian which does the installation after a reboot using more or less the same thing, as I remember from my old laptop's Kubuntu installation.
However, even this attempt at a Debian installation has not ended in success, as the exact same thing occurs once the installation is complete and I try to boot into Debian. This is four versions of Ubuntu and one of Debian which have failed to boot properly on this laptop, and it's incredibly annoying.

I can't seem to find a thread which offers help useful to this situation, as most of them seem to be based on fixing other problems once you've actually booted successfully.

I wonder, then, whether the community can help a poor open-source and Linux advocate who's stuck without a Linux installation to speak of? 
I do have Ubuntu running successfully in a virtual machine, but that is of course incredibly slow and hardly convenient.

The laptop's specs:

BIOS: Phoenix 4.0, Release 6.1

AMD Athlon 64 X2 dual-core processor, 1.7GHz per core
2GB RAM
GeForce Go 6100 (I think it has 64 megs of dedicated memory and then I'm sharing about 256 megs of RAM)

Thanks in advance.

---

### Post by Akria on 2008-01-04
Having experimented a little more, I managed to get it to boot successfully (yay!) by adding the following:

> noapic nolapic noapci noirqpoll nosmp

This coming from here: [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)?highlight=%28dv6000%29#head-ce0f5e4f0f860d0d499cfc5001182f9b77e46c0c](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)?highlight=%28dv6000%29#head-ce0f5e4f0f860d0d499cfc5001182f9b77e46c0c)

Everything I tried worked quite well, although the partition editor crashed a few times while scanning for devices after I changed some partition flags. It nevertheless applied the changes which, in fact, turned out to be pretty essential as at some point while in Ubuntu my Vista partition, current lifeline connecting me to help, had had the boot flag removed.

Having succeeded in at least booting, and having tested the installation wizard somewhat (it seems to have no problems, although I did not test it beyond the manual partitioning), it would appear that I will be able to run Ubuntu after all.

I now have three questions, then, if you would be so kind:
[LIST=1]
[*]What do the boot options listed earlier do, exactly?
[*]Can they cause any notable problems?
[*]Will my wireless work with them?
[/LIST]

If you could answer these for me then I would be very grateful.

---

### Post by ChrisNiemy on 2008-05-02
Hi,

with the options mentioned above for me cpu frequency scaling and brightness adjustment is broken.

Try only ```
noapic ht=on
``` (this worked well on gutsys 64bit) or just ```
noapic
```. Since ubuntu hardy I don't need any specific boot options.

"noirqpoll" might help also. Somewhere I read about "irqpoll", but this option produces overhead and no real advantage for me. The wiki-Page in the post above is also very good.

Is it working?

---

