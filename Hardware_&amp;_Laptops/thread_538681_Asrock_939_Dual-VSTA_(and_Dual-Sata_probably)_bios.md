---
title: "Asrock 939 Dual-VSTA (and Dual-Sata probably) bios choice issues"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Handssolow on 2007-08-30
This mobo (Asrock 939 Dual-VSTA) doesn't seem to show the usual Post messages at boot up so usually the first thing I see is the point where Grub kicks in. I've noticed recently that occasionally at the start  I see a brief glimpse of a screen of few lines with two lines of "capable but not configured". My guess is that I haven't set the bios optimally, probably for the hard drives. How does "it" know that some setting isn't optimal and who or what is it?

Mostly I use 32 bit Feisty on an IDE drive but I've 64 bit Feisty on a Sata2 which I can select using boot priority in the bios. Yesterday I'd had enough of my Belkin rt2500 wireless card and wired an ethernet link to my router which with me seems to work well with the onboard nic. Incidentally I tried removing my Audigy sound card to see if I could get anywhere with the on board sound chip but made no progress, so the sound card has gone back in.

Any suggestions and how also might I reveal the Post messages?

---

### Post by Handssolow on 2007-09-02
Eventually I've seen the message that SMART monitoring of my hard drives is capable but not enabled (in the bios). Not sure I want to. In the past with an earlier PC, I enabled SMART then every time I booted up it would halt to report a SMART error. Only one parameter was abnormal, all hard drive tests I subjected the drive to were normal but once activated I couldn't override the halt.

Still not seeing any Post messages prior to grub so I guess it's a feature lacking with this motherboard.

I've had another look at my IDE bios settings and I hadn't enabled 32 bit Data Transfer, now enabled my initial impression it that things seem faster. (though I understand I've still got only 16 bit transfer across the hard drive ribbon cable. LBA option incidentally is set at auto.

---

