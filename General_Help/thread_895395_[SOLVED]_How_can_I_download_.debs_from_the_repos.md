---
title: "[SOLVED] How can I download .debs from the repos?"
date: 2008-08-20
forum: General Help
---

### Post by kerryhall on 2008-08-20
Hey all,

I would like to be able to download .debs from the repos, and browse the repos with http. There is probably a super easy way to do this, but I don't know what it is.

Cheers!

---

### Post by elasto1mania on 2008-08-20
you can get debs from getdeb.com
but repo doesn't have .deb

---

### Post by Archmage on 2008-08-20
Why should you do this? Use Synatec to see what is there.

---

### Post by Vivaldi Gloria on 2008-08-20
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by kerryhall on 2008-08-20
Ehh I need to load some packages onto a machine that doesn't have a working network card or optical drive.

I am considering attempting to set up some sort of ethernet over serial link if I can find out how, but for now, I'm going to download packages and copy them over via floppy.

You heard me. :P

---

### Post by Kevbert on 2008-08-20
The only problem you may get is that some extra files (dependencies) may be required (such as drivers and library files). If you just download debs you may not find all of them will run.

---

### Post by Vivaldi Gloria on 2008-08-20
There is this:

[http://ubuntuforums.org/showthread.php?t=887904](http://ubuntuforums.org/showthread.php?t=887904)

but I haven't tried it.

---

### Post by kerryhall on 2008-08-20
Yeah, it's gonna be a headache to sort out deps, but I am really only trying to load gcc and svgalib.

Do you know anything about setting up ethernet over serial? Or perhaps debugging PCMCIA ethernet card problems? I got a PCMCIA ethernet card here that worked yesterday, and today the kernel is deciding to disable IRQ 11 every time on boot up.

The card is detected, but does nothing beyond that.

---

### Post by kerryhall on 2008-08-20
Ooo thanks, will give that a shot.

---

### Post by Vivaldi Gloria on 2008-08-20
> **kerryhall said:**
> Do you know anything about setting up ethernet over serial? Or perhaps debugging PCMCIA ethernet card problems? I got a PCMCIA ethernet card here that worked yesterday, and today the kernel is deciding to disable IRQ 11 every time on boot up.


Sorry, I don't know anything about that. Try opening a new thread in the Networking & Wireless subforum.

---

### Post by angry_johnnie on 2008-08-20
Assuming you know what you're looking for, you could use aptitude to download it.

Just do

```
sudo aptitude download package-name
```

It will be downloaded to your home folder.

---

### Post by kerryhall on 2008-08-21
Thanks to everyone! Hmmm on boot up THIS time the kernel decided to enable IRQ 11. So I have internet access on that computer now. It would be nice to figure out the IRQ thing at some point.

Thanks again all!

---

