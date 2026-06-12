---
title: "deleted ubuntu partitions...but forgot to delete grub first...(help!!)"
date: 2010-12-26
forum: Hardware
---

### Post by fight2survive on 2010-12-26
Alright so i had ubuntu on my netbook (samsung n130), and i wanted to uninstall it cause it was being glitchy, and i just recently got a desktop computer and installed ubuntu on it and it's working fine so i didnt need ubuntu on the netbook anymore...
but, i made a mistake... i deleted the ubuntu partitions from windows 7 disk manager, without removing the grub first...
now i am almost 100% sure that next time i restart the computer, windows 7 won't boot up anymore...
is there any way i can fix this? PLEASE help me i need my netbook for school and can't afford to send it to repair for days...

---

### Post by wilee-nilee on 2010-12-26
> **fight2survive said:**
> Alright so i had ubuntu on my netbook (samsung n130), and i wanted to uninstall it cause it was being glitchy, and i just recently got a desktop computer and installed ubuntu on it and it's working fine so i didnt need ubuntu on the netbook anymore...
but, i made a mistake... i deleted the ubuntu partitions from windows 7 disk manager, without removing the grub first...
now i am almost 100% sure that next time i restart the computer, windows 7 won't boot up anymore...
is there any way i can fix this? PLEASE help me i need my netbook for school and can't afford to send it to repair for days...

Do you have a cd/dvd reader to plugin or Ubuntu on a thumb that can be booted? You say a netbook indicating no on-board cd/dvd reader.

---

### Post by fight2survive on 2010-12-26
i do not own an external dvd drive, but was planning on buying one tomorrow...
although the thing is that windows 7 came installed into the netbook when i bought it, so i wonder how i would be able to re-install/boot windows from an "original" cd if there was no cd to begin with? is there a way to do that?

---

### Post by wilee-nilee on 2010-12-26
> **fight2survive said:**
> i do not own an external dvd drive, but was planning on buying one tomorrow...
although the thing is that windows 7 came installed into the netbook when i bought it, so i wonder how i would be able to re-install/boot windows from an "original" cd if there was no cd to begin with? is there a way to do that?

You just need to reload the MBR=master boot record. Can be done with a recovery cd that can be downloaded. And one command.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
You would just down load this burn to a cd; boot it accept the language go to the repair command line and run.
bootrec.exe /fixmbr.

You could also use a bootable Ubuntu live thumb to load lilo that will boot Windows as well.

In either case the MS is fully explained the lilo is two commands just ask for help on that one f you decide that would work.

---

### Post by fight2survive on 2010-12-26
thank you! i'll try that as soon as possible.

---

### Post by fight2survive on 2011-01-07
AMAZING! the /fixmbr command worked like a charm. thank you!!!

---

