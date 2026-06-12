---
title: "Wireless keyboard problems"
date: 2008-08-27
forum: Hardware
---

### Post by gemmala on 2008-08-27
I've got a wireless keyboard (a cheap one - Turbo-Media KB-9801R+), with the receiver plugged into the USB. Works fine with XP, but with Ubuntu (8.04 Hardy Heron, but the problem existed with Gutsy Gibbon as well) occasionally the keystrokes aren't recognised. More commonly (and more annoyingly) one key 'sticks' - so I get a long string of one letter. The driver disk lists only Windows as an OS, but I was wondering if there was something I could do to improve the situation, or if this is a result of me saving a few pounds on hardware....

---

### Post by gemmala on 2008-10-08
I'm beginning to use Ubuntu more often now, and the problem persists - currently running the latest version. Any tips?

---

### Post by geester on 2008-10-09
if the keyboard is wireless, I presume it's run on batteries, have you tried changing them? I did this and my keyboard misbehaves when new batteries are needed.

Failing that, it could be the wireless sender unit.

---

### Post by Tomatz on 2008-10-09
Try going into *system, preferences, keyboard.*

Then **move the "repeat keys" up**.

You can even turn repeat keys off.

That may solve your problem ;)

---

### Post by gfxguy on 2008-10-10
I have a wireless keyboard problem and found this thread (did a search before posting, of course).

My problem is that I am using an ASUS M2N motherboard with built in USB.

The USB works fine until it's been idle for some time.  I tried a bunch of suggestions on Slashdot; from reloading kernel modules to adding IRQPOLL to boot options (which had the terrible effect of making the system pause every few seconds).

So one suggestion was to get a USB add-on card, because motherboard manufacturers, apparently don't implement the spec right.

So I got an add-on card (reviews on Amazon said it worked with Linux), and turned off the built-in USB.  But now when I boot up, the keyboard is not recognized.  So I get the grub menu, and can't select anything.

What I've discovered was that, using a normal keyboard, after selecting Ubuntu from grub, one of the first things it does is load the USB drivers and everything works great.  But I'm supposed to have two keyboards?  One for booting and one for everything after?  Very annoying.  At least I can use the mouse and my older keyboard (there was nothing really wrong with the old one anyway).

This is not a Linux problem, of course... BIOS reports "no keyboard found" when booting up (but still goes to grub).  If I was using Linux only, and had no boot menu, it'd work great.

---

### Post by Tomatz on 2008-10-10
> **gfxguy said:**
> I have a wireless keyboard problem and found this thread (did a search before posting, of course).

My problem is that I am using an ASUS M2N motherboard with built in USB.

The USB works fine until it's been idle for some time.  I tried a bunch of suggestions on Slashdot; from reloading kernel modules to adding IRQPOLL to boot options (which had the terrible effect of making the system pause every few seconds).

So one suggestion was to get a USB add-on card, because motherboard manufacturers, apparently don't implement the spec right.

So I got an add-on card (reviews on Amazon said it worked with Linux), and turned off the built-in USB.  But now when I boot up, the keyboard is not recognized.  So I get the grub menu, and can't select anything.

What I've discovered was that, using a normal keyboard, after selecting Ubuntu from grub, one of the first things it does is load the USB drivers and everything works great.  But I'm supposed to have two keyboards?  One for booting and one for everything after?  Very annoying.  At least I can use the mouse and my older keyboard (there was nothing really wrong with the old one anyway).

This is not a Linux problem, of course... BIOS reports "no keyboard found" when booting up (but still goes to grub).  If I was using Linux only, and had no boot menu, it'd work great.


You just need to enable "legacy USB support" in the bios ;)

---

### Post by gfxguy on 2008-10-19
> **Tomatz said:**
> You just need to enable "legacy USB support" in the bios ;)

Hmmm... I was under the impression that that only worked for the built in USB, which was the problem to begin with, but I'll give it a whirl.

---

### Post by Tomatz on 2008-10-19
> **gfxguy said:**
> Hmmm... I was under the impression that that only worked for the built in USB, which was the problem to begin with, but I'll give it a whirl.

Worked for me ;)

---

