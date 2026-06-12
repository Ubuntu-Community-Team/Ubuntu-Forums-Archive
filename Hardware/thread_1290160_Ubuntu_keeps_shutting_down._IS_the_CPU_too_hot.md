---
title: "Ubuntu keeps shutting down. IS the CPU too hot?"
date: 2009-10-13
forum: Hardware
---

### Post by Lord Stig on 2009-10-13
Hi all.
Hopefully I am posting in the right area. I have posted elsewhere but had no joy as yet.

My friend has a E5200 processor which doesn't appear to be running too hot (although I am no expert). He tried Intrepid which installed successfully through windows (Wubi, I think it's called?) but it would restart either during boot up (the progress bar would move left to right, then right to left in the familiar powering down way) and other times it'd boot Ubuntu ok but he'd get a couple of minutes out of it before it shut down. No message was given as to why.
He's just tried Jaunty which has the same problems but does apparently report why this time - it says the CPU temperature is too hot and reports 25C. That doesn't sound that hot to me (but see first set of brackets, above). He's checked the BIOS which says the maximum running temperature cut off is 90C (too hot I would guess??).
He doesn't have any temperature-measuring Windows programs but he doesn't have this restarting problem in it. Puppy is also affected in the same way as Ubuntu.
Reading these forums and others I understand the problems in Linux interpreting the temperature data it gets. Is there a command line switch on bootup or something in the BIOS he can try? If sensible, is there a way to force the BIOS or Ubuntu to ignore temperature readings?

I should be able to get some specs of his machine if this is helpful.

---

### Post by Lord Stig on 2009-10-14
[-o< Any ideas?

Thanks.

---

### Post by nzadLithium on 2009-10-14
Have you tried running straight from the livecd? Do you still have the same problem?

---

### Post by Lord Stig on 2009-10-14
Thanks for replying! Yes, same problem unfortunately.

---

### Post by Giblet5 on 2009-10-14
What happens if you run the memtest86 diagnostic for an hour or two?

Any modern Intel CPU will slow itself down when it overheats.

That'll make your system slow, but it won't crash or reboot just because the CPU overheated.

It's possible that your memory timing is off, or that your motherboard chipset is overheating, or that your power supply is flaky/overtaxed...

---

### Post by carlosqueso on 2009-10-15
I've noticed the same problem, but only when I'm using something 3d or large flash videos....graphics card issue perhaps? It also happened after switching to the opensource radeon driver. Is there a way to diagnose that?

---

### Post by nzadLithium on 2009-10-16
carlosqueso, if you think its possibly an issue with the radeon driver perhaps you should head to the xorg forums and ask there about it?

on this page:
[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)
It lists ways you can get in touch with xorg dev's, they should be able to give you a hand on getting any information they need to fix any bug that may exist. It would probably be a good idea to try another video driver first though and see if the problem persists.

---

### Post by Lord Stig on 2009-10-21
Doesn't appear to be a hardware issue as he's installed XP on it and that works fine. It's my friend's machine that's affected, not mine (I use Xubuntu Jaunty and Ubuntu Intrepid on my machines and no Windows).

Strange.

He seems happy with XP; can't convince him to use Ubuntu now.

Thanks to those who read and those who replied.

---

