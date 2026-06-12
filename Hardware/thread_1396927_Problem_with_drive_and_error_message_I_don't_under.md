---
title: "Problem with drive and error message I don't understand..."
date: 2010-02-02
forum: Hardware
---

### Post by hortstu on 2010-02-02
I've taken my wifes hard drive from her computer and hooked it up to mine via usb.

The problem in her computer was that it would start to boot then restart before it finished... seemed like it was looped.

Anyway now when I try to access the boot partition via my hardy heron laptop I get a long error message that I'm going to partially paraphrase... I'll get more specific if someone needs me to...

> CANNOT MOUNT VOLUME 
unable to mount the volume 'volume name'.

details

$logfile indicates unclean shutdown (0,0) failed to mount /dev/sdb2': operation not supported mount is denied because NTFS is marked to be in use.

> Choose 1 action: choice 1... if you have windows.. I DONT SO I WONT BOTHER TYPING THIS PART"

> 
Choice 2: If you don't have windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g/dev/sdb2/media/(volume name) -o force

I tried this putting this in the terminal and it didn't seem to help.

> Or add the option to the relevant row in the /etc/fstab file: /dev/sdb2/media/ (volume name) ntfs -3g force 0 0

Can anyone help?

What is the relevant row and how do I get to the /etc/fstab file?

Thanks

---

### Post by hortstu on 2010-02-02
What is the best forum for this question?

---

### Post by MobiusJedi on 2010-03-29
> **hortstu said:**
> What is the best forum for this question?

I'll do you one better: [http://ubuntuforums.org/showthread.php?t=836409]("http://ubuntuforums.org/showthread.php?t=836409&highlight=cannot+mount+volume")

I just had the same problem, but I just had my friend plug it back into his laptop and eject it properly.

---

