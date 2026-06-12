---
title: "Ati 4870 radeon driver blank screen after resume"
date: 2012-11-03
forum: Hardware
---

### Post by syncmasterpt on 2012-11-03
I've tried several solutions to my issue, but I'm having no luck.

This issue is also recent, and not sure what might be causing it.

So the issue:

I have an AT 4870 graphics card on a ASUS P6T motherboard and non overclocked I7 920 processor.

I'm using the open source Radeon driver.

If I boot from a "cold" start, it seems that everything works fine.

But now I use heavily the suspend/resume capabilities.

What is happening is that the machine wakes up fine from the suspend/hibernation, works fine for around 5 minutes and then it hangs:
The screens (I have dual display) go black, keyboard stops responding, and I have to do a hard reset to get back up. Some times it happens again from the hard reset, and to clear things completely I'll have to power cycle completely.

I'm using the 3.2.0-32 kernel:

Linux kecortex 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

And I was using the Ubuntu's radeon driver and now the X-org edger's PPA driver (more recent). The issue happens with both versions.

The log is in here: [http://pastebin.com/t3VFQZRe](http://pastebin.com/t3VFQZRe)

Any help is appreciated.

Edit: I'm using 12.04 fully updated, with Kubuntu backports.

---

