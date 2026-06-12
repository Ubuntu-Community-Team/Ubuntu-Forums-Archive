---
title: "Odd Problem with Inspiron 1501/Gutsy"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by durrell on 2007-10-29
I have read several threads about various suspend/resume issues in Gutsy, but I'm having a problem getting Gutsy to start at all. I installed it and after installing, and ejecting the Live CD, then restarting to try to boot into my install, I was greeted by a black screen after GRUB. No error, no nothing..just a black screen. It appeared the screen was on, though, so I tried switching over to tty2 to see if I could get a terminal running. It showed part of the boot process, so I switched back over to tty1 to see that it was saying "PCI: BIOS BUG #81 [49435000] found, "PCI: Cannot allocate resource region 7 of bridge 0000:00:05:0".

The main thing that catches my eye is this:

```
[14.196000] Attempting manual resume

[14.196000] swsusp: Resume from partition 8:7

[14.196000] PM: Checking swsusp image.

[14.196000] PM: Resume from disk failed.

```

Does this sound like the same issue as the suspend/resume problem? I would assume not, since essentially it will not start on its own at all. I'd say it's pretty odd that switching to tty2 then back to tty1 "unfreezes" it and lets it boot. I guess since obviously "swsusp" looks like it is related to "Suspend", it may be related to the bug. Any input/ideas would be appreciated.

Thanks.

---

### Post by durrell on 2007-10-29
No one has any comment/ideas? That's unusual for this forum. haha.

---

### Post by whitesox on 2007-11-01
heh
nope, those errors really don't mean anything, especially the one about swap.  what happens is every time you boot, it checks to see if theres something to resume.  nothing to worry about if it doesnt find anything, it just means its a normal boot not a resume.

as for the other error: i dont know if it means anything, i get it too, but i get it booted and everything
if i were you i'd check the install disk and check grub
maybe try safe mode (or whatever ubuntu calls it)

---

### Post by whitesox on 2007-11-01
ya know, i was thinking
what bios version are you running? i have 1.7 and have no problems, but i just noticed I don't get the first bios error message, and ive had problems with other bios versions

i'd try upgrading the bios if you have a spare windows install to do it on.

---

### Post by taggat on 2007-11-01
I have the same Machine and I get some of those same errors.
PCI: Cannot allocate resource region 7 of bridge 0000:00:05:0
I also get PCI: Cannot allocate resource region 8 of bridge 0000:00:05:0

My Bios is 2.6.3 I think or maybe 2.3.6 either way just updating the bios doesn't get rid of the errors

---

### Post by whitesox on 2007-11-02
its not the PCI: Cannot allocate resource region 7 of bridge 0000:00:05:0 error im worried about, its the PCI: BIOS BUG #81 [49435000] one i am.
upon googling it i found this thread
[http://ubuntuforums.org/showthread.php?t=499811](http://ubuntuforums.org/showthread.php?t=499811)

they say its normalish, and to try pci=route irq
i'd also suggest trying 'acpi=force irqpoll', since an earlier bios had that bug that would prevent the hard drive from being found, and thus not booting

if you want to try them, in grub, hit 'e' when you have ubuntu highlighted, go down to the 'kernel' line, hit 'e' again, go to the end and add 'acpi=force irqpoll', hit enter, and hit 'b' to boot

worth a try.

---

### Post by durrell on 2007-11-04
Yeah I had noticed the same thing about pci=route irq and tried it, though it appeared to simply move the errors around instead of prevent them.

I did e-mail someone at Ubuntu after talking in the Ubuntu IRC channel for awhile and he said this was normal on this laptop, and that he had the same problem on his Compaq. I suppose it isn't a big deal, but it is a strange bug..especially considering it won't boot at all unless I interfere by switching to tty2.

---

