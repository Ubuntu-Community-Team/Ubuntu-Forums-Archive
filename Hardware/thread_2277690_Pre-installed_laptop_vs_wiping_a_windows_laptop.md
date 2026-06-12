---
title: "Pre-installed laptop vs wiping a windows laptop"
date: 2015-05-10
forum: Hardware
---

### Post by Jason_Walsh on 2015-05-10
Hey everyone, so I have an Asus gaming laptop currently that runs on Windows 8.1/Ubuntu dual boot and I am also planning on building a pc for at home use running windows. My laptop right now however is about 10 pounds and so I wanted a much lighter laptop with Ubuntu installed on it so I can take that on the go. I then want to remove the ubuntu partition on my Asus, so 1 laptop with Windows, and one with Ubuntu. 

So my question is, what are the pros and cons (if there are any) of getting a laptop pre-installed with ubuntu from a site like this: [https://system76.com/laptops](https://system76.com/laptops)
as oppose to just getting any windows laptop, formatting it, and then installing ubuntu on it?

Thanks!

---

### Post by mastablasta on 2015-05-11
the pro is that Linux definitelly works on that laptop and it Wil work.

the issue of windows laptop is that while linux might work at current verison of ubuntu there could be a kernel update/upgrade that would make it not work. and no one will actually work towards a fix. even if you file a bug it will just remain open. then another thing will stop working etc. or it might all work as it is supposed to. so it's a gamble.

Mine was certified. worked well with 12.10. (as it was certified for it) then i upgraded to 13.04, and already some thigngs didn't work as they should. I then went via 13.10 to 14.04 to be able to stay on LTS. Some Fn keys don't work annymore, had to find some other workarround, prt sc key doesn't work. in general it is usable, but never as it is in windows. and no one is willing or capable to debug the bugs that were not there before.

---

### Post by Jason_Walsh on 2015-05-11
> **mastablasta said:**
> Mine was certified. worked well with 12.10. (as it was certified for it) then i upgraded to 13.04, and already some thigngs didn't work as they should. I then went via 13.10 to 14.04 to be able to stay on LTS. Some Fn keys don't work annymore, had to find some other workarround, prt sc key doesn't work. in general it is usable, but never as it is in windows. and no one is willing or capable to debug the bugs that were not there before.

Just to double check, did yours come pre-installed with it and you updated it and it stopped working? Or did you have a windows laptop that you wiped and put linux on it?

---

### Post by SeijiSensei on 2015-05-11
I've never owned a Dell, Lenovo or ASUS that was not happy with Linux.  I'm on an HP laptop right now which works fine, though posed a couple of installation problems since there were no free primary partitions on the hard drive.  That was a problem trying to set up dual boot.

I've never bought a machine with Linux pre-installed.

---

### Post by Jason_Walsh on 2015-05-11
> **SeijiSensei said:**
> I've never owned a Dell, Lenovo or ASUS that was not happy with Linux.  I'm on an HP laptop right now which works fine, though posed a couple of installation problems since there were no free primary partitions on the hard drive.  That was a problem trying to set up dual boot.

So you just had issues with dual booting? I'm assuming it would be much simpler if I formatted the pc completely and installed only Ubuntu?

---

### Post by Mark Phelps on 2015-05-11
> the issue of windows laptop is that while linux might work at current verison of ubuntu there could be a kernel update/upgrade that would make it not work. and no one will actually work towards a fix. even if you file a bug it will just remain open. then another thing will stop working etc. or it might all work as it is supposed to. so it's a gamble.
Unhappily, I can confirm personally that this happens.  I had an older Fujitsu laptop that worked GREAT! with Ubuntu 8.04.  I had replaced Windows XP on that and couldn't be happier.  Then, there came along a kernel update, and it didn't work after that.  A key function was the special keys on the bezel -- as it was a first gen tablet PC.  Without those keys working, it was useless in tablet mode.  I tried various patches for a long time to get it working again, and eventually gave up and reinstalled Windows on it.

I later tried a similar "conversion" on an HP laptop -- and had to give up on it because of hardware that would not work.

---

### Post by SeijiSensei on 2015-05-11
> **Jason_Walsh said:**
> So you just had issues with dual booting? I'm assuming it would be much simpler if I formatted the pc completely and installed only Ubuntu?

Yes.  

It has a dual video adapter, Intel plus AMD/ATI; I'd prefer an NVIDIA.  The dual Intel with NVIDIA or ATI combos can still be a bit tricky.  On the HP, I force the ATI card on through a BIOS setting.  I like the design of my daughter's Lenovo better.  There's slide switch on the front of the machine that will enable or disable the add-on NVIDIA card.  

Bog-standard all-Intel equipment will pretty much always work with Linux.

---

### Post by Jason_Walsh on 2015-05-11
> **Mark Phelps said:**
> Unhappily, I can confirm personally that this happens.  I had an older Fujitsu laptop that worked GREAT! with Ubuntu 8.04.  I had replaced Windows XP on that and couldn't be happier.  Then, there came along a kernel update, and it didn't work after that. I later tried a similar "conversion" on an HP laptop -- and had to give up on it because of hardware that would not work.

Ok this was what I was worried about happening, that's why I was looking into pre-installed laptops that way I know for a fact it would all work. Not that I couldn't figure out how to install it on a windows machine, since I've done it dozens of times, but I do want a laptop that has been and always will be strictly linux.

Would wiping a pc and installing linux void any warranties that the PC might have? That was my other concern

---

### Post by SeijiSensei on 2015-05-11
Run the distribution of your choice from its DVD and choose the "Try" option.  See if anything fails to work.

As for warranties, it depends on the manufacturer and the provider of the warranty if it is a third-party.  If this machine is more than a year old, it's unlikely to be covered by warranties unless you bought an extended one.  If the machine has been working fine up until now, it shouldn't have any problems continuing to work with Linux.

---

