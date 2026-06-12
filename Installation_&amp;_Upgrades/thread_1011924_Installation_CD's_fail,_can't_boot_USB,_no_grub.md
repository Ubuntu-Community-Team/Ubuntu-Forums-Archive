---
title: "Installation CD's fail, can't boot USB, no grub"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by jorfanakis on 2008-12-15
I have a Dell Inspiron 8200. The HD has been totally wiped.
The live and alternate CD installs fail at random points during the copy file phase. I have tried to clean the lens.

I can boot Ubuntu from the CD in trial mode, after what seems like forever and it is "usable". What is easier is to boot SystemRescueCD. I have networking going.

I tried the following methods:
1. Created partition to copy iso or to install the network install, that works but I can't install grub to get it to boot.
2. Created a small partition to just get grub installed no luck there.
3. I found some procedure to get grub installed by choosing to manually partition during the ubuntu install process, but don't format which causes the install to fail and allows one to select to install grub. I can't get that to work because it seems to me on the Ibex install it will not allow you to leave the Partitioner without formatting the / partition.
4. Can't boot from USB, not supported.

The machine only has 256MB Ram. I read a couple posts suggesting this may be an issue. I don't know. The error says could not copy file and suggests it is a bad CD. This CD works fine on other computers and as I said I tried the live CD and alternate and got the same error.

I must be missing something because I can't find a way to boot from CD and then install from another location. I can mount a USB flash with the iso or contents of the iso. Is there a way to start the install from this?

TIA
JO

---

### Post by snowpine on 2008-12-15
I would recommend the Xubuntu alternate install CD in your case. It should run fine with only 256mb of ram. Also check out the instructions in the Ubuntu wiki on how to burn a CD and test the md5sum for errors.

---

### Post by jorfanakis on 2008-12-15
Thank you for the reply.

I actually did check the checksums, they were fine. Sorry I forgot to mention that.

I have also used both discs to install on other computers with no issues.

JO

---

