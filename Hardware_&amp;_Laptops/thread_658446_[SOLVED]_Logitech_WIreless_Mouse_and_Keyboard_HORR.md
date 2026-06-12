---
title: "[SOLVED] Logitech WIreless Mouse and Keyboard HORRIBLE lag"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Nerdriot on 2008-01-04
Hello :)

This is my first post. I'm still a noob, so bear with me...

Recently, I decided to dual-boot a machine for a friend, not only to show them the better sides of Linux (and to hopefully make them decide to switch over completely), but so I would have a decent, working OS to run when I was around.

Everything worked fine for a while. I installed Gutsy, had no problems at all (the worst issue I had was installing Flash, which took about 15 seconds to resolve). Then, suddenly, the machine appears to be lagging HORRIBLY, as if there are a ton of processes going all at once, eating away at the machine.

I did a few random little tests, to see if it was the machine lagging, or maybe just the keyboard and mouse. Turns out, it was just the keyboard and mouse.

There is seemingly no pattern to it. It either happens after 15 minutes of use, or 4 hours. I've noticed it occuring more often after having used Firefox (though, it's probably just because I use Firefox all the time, and it's incidental).

Anyone have any idea what might be causing it?

I've changed the kernel boot options, and added "Irqpoll", then tried "acpi=noirq", at the request of some others here on the board, but nothing seems to help.

Thanks in advance :)

---

### Post by Nerdriot on 2008-01-10
Ok, hopefully, this is a fix for it. After testing a little more, I added **noapic** in  /boot/grub/menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4195995d-914f-4478-a7a0-2cd911e20166 ro quiet splash **noapic**
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

It's been running just fine ever since then, and it's been about a week. I hope this helps someone.

---

### Post by zeusalmighty on 2008-01-11
Sorry to barge in your thread, but could let us know how you managed to get Logitech wireless combo to work in the first place? Mine both work, but i don't have the extra buttons on my mouse or keyboard.

---

### Post by Nerdriot on 2008-01-12
Well, honestly, I couldn't even tell you, hah. I know that's pretty lame, but once I installed Ubuntu 7.10, it automatically did everything for me, I suppose, because I didn't have to do any tweaking to get the mouse and keyboard functioning properly.

I looked around on Google for an answer to your problem, but couldn't find anything so far.

Hmm... what isn't it doing? Just the extra buttons won't work?

---

### Post by clong83 on 2008-02-01
For what it's worth, I had the same type of problem with my laptop keyboard (hp dv5000), and I tried this (among many other things) to no avail.  I fixed the problem by uninstalling bcm43xx-fwcutter (broadcom wireless drivers).  I'm glad it worked for you, I just thought I'd post to alert people of another possible culprit...

---

### Post by shan420 on 2008-02-18
Hi there, I've tried this fix, it doesn't really work for me, there's one weird thing i've noticed, when I enable the Advanced Desktop Effects Settings, there's no delay or lagging problem with the keyboard, when i switch back to Normal Mode in Advanced Desktop Effects Settings, I get the same delaying in typing (Keyboard response) as if processor is really over loaded with applications...

Any help would be appreciated. thanks

[My System configuration Dell Inspiron 9200, ATI Radeon 9700, 100 GB Hdd ]

----------------------------------------------------------------------------------------------------------
> **Nerdriot said:**
> Ok, hopefully, this is a fix for it. After testing a little more, I added **noapic** in  /boot/grub/menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=4195995d-914f-4478-a7a0-2cd911e20166 ro quiet splash **noapic**
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

It's been running just fine ever since then, and it's been about a week. I hope this helps someone.

--------------------------------------------------------------------------------------------------------------

---

