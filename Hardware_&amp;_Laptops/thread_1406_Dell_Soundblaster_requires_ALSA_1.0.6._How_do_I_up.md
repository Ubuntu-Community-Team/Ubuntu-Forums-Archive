---
title: "Dell Soundblaster requires ALSA 1.0.6. How do I upgrade?"
date: 2004-10-20
forum: Hardware &amp; Laptops
---

### Post by akadajet on 2004-10-20
Hi,

I've recently gotten the itch to give Linux a try, and I was reading great things about Ubuntu on other message boards. And so far, mostly everything is working pretty well. Unfortunatly sound isn't.

Turns out that my Dell desktop computer has a "special" version of the Soundblaster Live card (emu10k1x) which isn't even well supported in Windows. After doing some research, it looks like support for my card has just recently been added to ALSA 1.0.6. Problem is, the only package I can find for Ubuntu is 1.0.5, which doesn't help me much at all.

So I've been banging my head against this problem for a couple of weeks now, and I've even tried other distributions to see if I can get sound working. No such luck.

I also tried re-compiling the kernel using a patch I found in the bugzilla repository. That didn't work either, and gave me a bunch of errors.

Does anybody know what I'd need to do to get ALSA 1.0.6 with the snd-emu10k1x module on Ubuntu? I'm not opposed to trying to re-compile the kernel again, but I'd need to know how to properly upgrade or patch it.

Thanks!

---

### Post by Hunter on 2004-10-21
I don't have a solution for you, but I wanted to let you know that I am in a similar dilemma.

Basically I experience occasional sound crackling/distortion using the onboard ALC655 in Ubuntu.  This is not a hardware problem since the problem doesn't occur in windows.

I would like to  upgrade to ALSA 1.06 or later however I'm at a loss at how to do this.   Do I have to compile custom kernel from scratch or can I just replace the old kernel modules with the newly built ones (from alsa-driver)?   Does this require alsa-lib as well as alsa-driver?  What lines do I have to modify in module.conf (which states "do not touch, this is automatically generated").  The documentation is silent on all these issues.

---

### Post by JProgrammer on 2004-10-21
You cannot replace modules under Linux you will have to replace the kernel yourself in the 2.6 series you don't need alsa-driver only alsa-lib because the alsa drivers are now in the kernel

---

### Post by akadajet on 2004-10-21
Well, for now I just enabled the onboard soundcard throught the BIOS. So right now I've got sound working. Hopefully Ubuntu will get ALSA 1.0.6 support sometime soon-ish.

---

### Post by iwasbiggs on 2004-10-22
[http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI+X+%28Dell+OEM%29.&chip=SB0200&module=emu10k1x](http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI+X+%28Dell+OEM%29.&chip=SB0200&module=emu10k1x)

That should tell you how to install.

I think you can skip the part about compiling the soundcore and sound modules into the kernel.

It looks like a bit of work but not that bad.
Just waiting for the update won't be too bad either.

---

