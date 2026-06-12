---
title: "grub2 and AHCI"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by phekdra on 2009-10-31
Hello all,

  I've just done a clean install of 9.10 rather than an upgrade, and now I can't boot. GRUB2 just hangs there saying 'Grub loading.' or something similar. Curiously, it worked the first time I booted after installing, but not subsequently. Occasionally the hard drive burps, but I've waited 10 minutes so I doubt anything more is going to happen.

  My hard drives are set to AHCI mode in the BIOS, and when I disable this is boots perfectly happily. Now if I have to do this to get it to boot then I'll go back to GRUB1. Does anyone have any ideas? :(

  I've done both a forum and a google search and it seems I'm not alone, but nobody appears to have an answer. I'd switch back right away if it hadn't booted first time - I'm clinging onto that as a possibility I might eventually get it working. :)

  Andrew

---

### Post by dino99 on 2009-10-31
my config is like yours & i have the same problem to boot.

how i can boot: 
i unplug power cord, wait 5 seconds & try to reboot. Usually, grub menu pop up
i edit the boot line (ctrl e) & remove the first 2 lines (recorfail ... fi), then i can boot normally (ctrl x)


there is an other solution:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

### Post by phekdra on 2009-10-31
> **dino99 said:**
> 
[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

:p I'm glad it's not just me. I think your second suggestion might cause less hassle!

Andrew

---

### Post by phekdra on 2009-10-31
Well I've partially solved it. I noticed that my motherboard has another SATA controller that also supports AHCI, so I thought I'd try that. Both my hard drives plug in and...

GRUB loading.

....

:evil:

So I set the ICH? controller to disabled and Grub has booted perfectly happily every time since! :shock:

It appears it's not AHCI mode that Grub2 doesn't like, just the south bridge controller running in AHCI mode, even when no actual drives are plugged into it! It's quite happy with the onboard Gigabyte one.

As I said, it's not a solution, but it appears to be a partial explanation.

Andrew

---

### Post by GabbaGandalf on 2009-11-05
hello,

i have got the same problem.

i created a bug report at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/466906](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/466906)

---

### Post by lorentzr on 2009-11-09
If you're using an HP machine, the answer you're looking for might be here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by presence1960 on 2009-11-09
> **phekdra said:**
> 

So I set the ICH? controller to disabled and Grub has booted perfectly happily every time since! :shock:

It appears it's not AHCI mode that Grub2 doesn't like, just the south bridge controller running in AHCI mode, even when no actual drives are plugged into it! It's quite happy with the onboard Gigabyte one.

As I said, it's not a solution, but it appears to be a partial explanation.

Andrew

I withheld posting this until I saw the above. My drives are set to AHCI mode and have never had a problem with GRUB 2 booting. So maybe it is a problem with how your mobo is setup or something.

---

### Post by NHellFire on 2011-11-17
Seems to only happen with some chipsets. I've been through multiple installs of Ubuntu 11.04 and 11.10 because GRUB kept failing to load. Strangely... it worked fine with a 32bit install, it only failed to boot with 64bit. Definitely a GRUB issue though, SYSLINUX, NTLDR and Windows Boot Manager have no problems on it.

---

