---
title: "Installing 8.10 on eMac w/ cdrom not autodetecting"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by alcane on 2009-01-26
I'm using the 8.10 disk and it boots up to the terminal and everything, but when it gets to auto-detecting the cdrom, it can't find it. I looked into /dev and there's no cdrom or dvd. I don't even care if I won't be able to use the cdrom. I just need linux on this thing, lol. The internet is all that it'll be used for.

---

### Post by julian265 on 2009-01-28
try modprobe ide-scsi, then repeat the step, and it will detect it.   (sudo required??? I can't remember, I'm new to this).

You're probably in for a few xorg fiddles after you install. I've just got 8.04.1 working on my emac 700, 8.10 should  be fine too.

---

### Post by sepaphastro on 2009-02-19
Thanks, julian265!

I had the same problem trying to install Ubuntu 8.10 on a Powerbook G4.

Fn-option-F2 brought up another console.
Enter to activate the console.
entered at the busybox prompt:
~ # modprobe ide-scsi
~ # exit
Fn-option-F1 to go back to the installer, repeated the cdrom step and it auto-detected!

---

### Post by tobemorecrazy on 2009-03-11
This worked perfectly!  Thank you!

---

