---
title: "Caught in no man's land"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2009-05-06
I have a Dell Inspiron 1501 laptop that came with Windows. Using Wubi, I installed Ubuntu v 8.04 and have used it since as my default OS.

I decided I'd like to upgrade to v 9.04. I understood that that had to be done by first upgrading to v 8.10 and then upgrading from it to v 9.04.

I upgraded to v 8.10. I then began the upgrade to v 9.04, but was warned against continuing the upgrade, so didn't.

The warning was that my computer was currently using the AMD 'fglrx' graphics driver and that no version of that driver was available that works with my hardware in v 9.04.

I don't know what to do now.

Upgrade anyway? Stay where I am now, either temporarily or permanently? Downgrade to where I was (assuming that's possible)?

Is a version of the driver that works with my hardware in v 9.04 likely to become available?

As between versions 8.10 and 8.04, my understanding is that 8.04 will be supported for longer than 8.10. Is that a sufficient reason to go back to where I was before, assuming that's possible?

If it matters, before attempting the upgrade to v 8.10, I copied my entire home directory to /host as some kind of insurance.

I'd appreciate any advice.

---

### Post by Mark Phelps on 2009-05-07
> **lesliek said:**
> Upgrade anyway? Stay where I am now, either temporarily or permanently? Downgrade to where I was (assuming that's possible)?

If you upgrade, you will have to use the open source drivers.  Would be best for you to remove the fglrx drivers first, before you do an upgrade.

The link below tells you about the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

> 
Is a version of the driver that works with my hardware in v 9.04 likely to become available?

No -- AMD/ATI has dropped support for older cards, both in Linux and in MS Windows.
> 
As between versions 8.10 and 8.04, my understanding is that 8.04 will be supported for longer than 8.10. Is that a sufficient reason to go back to where I was before, assuming that's possible?

There's no simple way to "go back", so I would suggest you boot from the 9.04 LiveCD and see how well it works with your hardware before you do the upgrade.

---

### Post by lesliek on 2009-05-07
Thanks for your reply.

I'm typing this while running the v 9.04 live cd.

I used the lsmod command and confirmed that the radeon module was loaded. I don't SEE any difference between that and running v 8.04 or v 8.10 with the fglrx module, just typing this, but are there some tests I can run that will give me comparative figures?

One thing that does strike me is that running both v 8.04 and v 8.10, I had to use ndiswrapper and the Windows driver to get my wireless card to work reliably. Running this live cd of v 9.04, my wireless seems to be working perfectly with whatever Linux driver's been loaded automatically.

Thanks again.

EDIT: On thinking about it, I don't want "comparative figures". What I want is to know whether the radeon driver, running on my hardware, will meet a generally-accepted minimium standard, assuming there is one. Are there tests for that?

---

