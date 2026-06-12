---
title: "Two sound cards, but cannot find first."
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by longship on 2006-03-29
A coworker and I are attempting to resolve a sound card issue.

He has an ASUS A7 motherboard which has a "via82xx" sound card on-board.  He's also added an M-Audio Delta 44 sound card (ice1712).  When he plugs in the Delta 44 sound card, the via82xx sound card disappears.  "lspci" doesn't even find it.  Both sound cards have VIA controllers, one is via8237 and the other is the ice1712.

What's the deal here?  Is this a hardware conflict problem, or is this an Ubuntu problem?

The guy wants *both* sound cards recognized.

If this is an Ubuntu issue we'd like to know before we go mad.  ;-)
Many thanks.

---

### Post by ispmarin on 2006-03-29
Stupid question (once done this! :-)) Are both soundcards habilitated on BIOS?

---

### Post by longship on 2006-03-29
[QUOTE=ispmarin]Stupid question (once done this! :-)) Are both soundcards habilitated on BIOS?[/QUOTE]

Yup.  First place we looked.  It seems that the one card is masking the other.  How do we resolve?  Could it be PCI slot issues?  I can't think that this is Ubuntu.  The kernel should recognize both cards, or so I would think.

---

### Post by ispmarin on 2006-03-29
Do both soundcards occupy the same pci interrupt when you boot with one or other and both? Don't know if it is Ubuntu, but appears so. Maybe you have to do a kernel recompilation with both drivers compiled against the kernel, and not as modules.

---

### Post by longship on 2006-03-29
[QUOTE=ispmarin]Do both soundcards occupy the same pci interrupt when you boot with one or other and both? Don't know if it is Ubuntu, but appears so. Maybe you have to do a kernel recompilation with both drivers compiled against the kernel, and not as modules.[/QUOTE]

Well, since "lspci" isn't even seeing the card, there's certainly no way that the sound drivers are going to see it.  I imagine that there's something going on with the IRQs.  Looks like we're going to have to play the swap PCI card slot game?

Any other ideas?

---

### Post by ispmarin on 2006-03-29
Sorry about my bad explanation. What I was looking was: when you unplug the soundcard, what is the pci slot that the onboard card occupies? is the same that the other card occupies when you plug it back? If it is the same, we will be more sure that there is a overlapping pci slot. If not, well, It can become more strange...
Start thinking about a kernel recompilation.

---

### Post by longship on 2006-03-29
[QUOTE=ispmarin]Sorry about my bad explanation. What I was looking was: when you unplug the soundcard, what is the pci slot that the onboard card occupies? is the same that the other card occupies when you plug it back? If it is the same, we will be more sure that there is a overlapping pci slot. If not, well, It can become more strange...
Start thinking about a kernel recompilation.[/QUOTE]

What I've asked him to do is pull the Delta 44 out and reboot.  See if the sound card is recognized by typing "sudo lspci".  If it is there, we'll put the Delta 44 in another PCI slot and see if the kernel can see both.

What I was trying to say in my previous post was this:
Until "lspci" sees both cards, I can compile sound into the kernel until I'm blue in the face and it won't do any good.  If the PCI drivers don't see the card, there's no way that the sound drivers are going to have anything to bind to.

---

### Post by ispmarin on 2006-03-30
Agreed. No more ideas now... just some ideas for testing; try with some live cds different from ubuntu, or maybe ubuntu dapper livecd and sees if both sound cards are found, try to plug on a different computer and sees if works, etc. Really, don't know. Sorry.

---

