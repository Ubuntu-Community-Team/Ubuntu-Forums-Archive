---
title: "Installing on Intel ICH10R Raid 0"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by spasm on 2009-07-20
Hi all,

There's been a lot of discussions regarding the use of so-called "FakeRAID" setups with 9.04.  I've been reading them for the last 5 hours and none of them seem to address the problem I'm having (many seem to be having similar types of issues but none of the fixes have worked).  None of the specifics included my hardware so maybe that's part of my issue, which is:

I got 9.04 to install on my raid after some work.  However, when rebooting I get dumped to initramfs shell and have to manually start dmraid.  The messages I see just before doing so are usually different.  Sometimes dmraid seems to have started (I get the message that a raid array was found on /sdb and using "isw" etc etc), other times I just get a big chunk of messages stating no block devices are found.

It seems to be a timing issue, but using rootdelay has no effect.

Other solutions include adding a udev settle command to the dmraid initramfs script - but I don't have one, it seems to have been removed from the latest version of dmraid.

It's a minor inconvenience, but I'd like to fix it nonetheless.

Thanks~

---

