---
title: "Strange RAM problem."
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by kutjara on 2008-04-02
This one is a real head-scratcher for me. I'm running 32bit Hardy beta on an Acer Aspire 4315. It came out of the box with 1GB of PC2-5300 RAM in the form of two 512MB modules.

I decided to upgrade the memory using some spare modules I have lying around. I first started with 2 x 2GB, but this caused the machine to freeze fairly early on in the boot cycle (after roughly twenty seconds of progress bar action). BIOS recognized the modules correctly, but Ubuntu clearly didn't like them. This is puzzling, since the 4315 uses the gl960 chipset that can accommodate Core2Duo CPUs (although it currently contains a 1.86MHz Celeron). Indeed, one of the reasons I wanted to upgrade to 4GB RAM was because I'm planning to install a T7100 CPU in the machine and run 64bit Hardy. That doesn't look like it's going to be possible now.

So next I thought I'd pair one of the 2GB modules with a 1GB one. This time I got a very alarming black stripe effect on the boot splash screen, before the machine gamely attempted to reboot, before once again freezing with the stripy screen. Strike two.

Next I tried a 2GB and a 512MB. Result: same stripy/freeze mess. Strike three.

1GB + 1GB? Stripy freeze. Strike...erm...four.

Finally, I put just one of the 2GB modules in one of the slots. Success!

I then tried a single 1GB module. That too worked.

So what seems to work is either 512MB + 512MB, a single 2GB module, or a single 1GB module. This seems very odd to me. I would have thought I could just slap in 4GB and the 32bit version of Ubuntu would address however much memory it could (3GB or whatever).

All of the modules work fine as do both of the memory slots (it doesn't matter which of the 2GB modules I put in which of the RAM slots; both work equally well).

Am I making some ridiculously obvious mistake here? I'm a relatively new Linux user, so I'm perfectly prepared to believe there's something else I need to do besides just slap the RAM in the slots and switch the machine on, but I can't think for the life of me what it is.

I'm grateful for any input.

---

### Post by jespdj on 2008-04-02
Did you read the manual of your motherboard if the RAM needs to be placed in a specific order? Maybe the RAM you've bought is not compatible with your motherboard? Your motherboard manual or the website of the manufacturer of your motherboard probably contains information about which types and brands of memory are compatible. Is the new RAM the same (same speed etc.) as the RAM you already had?

---

### Post by kutjara on 2008-04-02
> **jespdj said:**
> Did you read the manual of your motherboard if the RAM needs to be placed in a specific order? Maybe the RAM you've bought is not compatible with your motherboard? Your motherboard manual or the website of the manufacturer of your motherboard probably contains information about which types and brands of memory are compatible. Is the new RAM the same (same speed etc.) as the RAM you already had?

Yes I did. The RAM I used is, coincidentally, exactly the kind that Crucial recommend on their website for this machine. It's PC2-5300, 667MHz, and in every other way I can figure out is exactly what Acer specify. Actually, the RAM that came preinstalled was some super-cheap no name stuff, so I'm guessing the machine isn't too choosy about what it swallows.

I've installed all the modules in all the possible permutations, so it doesn't seem like installation order is an issue.

There's a dot release of the BIOS that I'm about to install now. It doesn't say anything about RAM in the release notes, but several people on other forums who are doing CPU and HDD upgrades are installing it first, so there may be something about it that I don't know. Yep, you guessed it, I'm grasping at straws.

Thanks for the suggestons, though!

---

