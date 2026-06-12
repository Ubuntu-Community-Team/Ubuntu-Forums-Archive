---
title: "Accidentally purged my main kernel"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Mr_Pag on 2009-01-12
Hi all,

I need a bit of help. I bought a Dell 1525N with 8.04 preinstalled and it's been a joy to use, so much so it's replaced my vista desktop for pretty much everything I need a computer for. Anyways...

I recently upgraded my kernel to 2.6.24.23-something and decided to remove the existing kernel with the command -

sudo apt-get remove --purge 2.6.24-22*

Unfortunately it was interrupted for whatever reason. I set about repairing the interrupted apt-get job with --configure -a and issued the above command a second time.

It somehow ate every kernel on the system and has left me with only memtest and the dell recovery utility in the grub entry. I would repair grub but obviously there's no trace of any kernels in /boot and I'm screwed bar this live CD.

What I need to know is if I can chroot into the hd and use apt-get to reinstall the latest kernel from my 8.04 LTS live CD? I remember a similar operation during a Gentoo install years ago. I'm not sure whether the kernel upgrade came from Canonical or Dell, can anyone shed any light on this?

This was a really dumb mistake, I'd appreciate any help anyone can bail me out. Thanks for your time.

Best regards,

Alan

---

