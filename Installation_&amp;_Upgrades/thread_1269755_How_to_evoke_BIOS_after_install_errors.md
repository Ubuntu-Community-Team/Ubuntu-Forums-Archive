---
title: "How to evoke BIOS after install errors"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by wizardchef on 2009-09-18
I tried to install Xubuntu on a 700 MHz Pentium Dell Latitude laptop, 256 MB, using a CD. After about 45 sec the install crashed and shut down the laptop. Now I get a series of error messages for about 1.5 s when I try and boot, and the laptop shuts down with a "shutting down ALSA ..." message.

My question: How do I access the BIOS now? The computer no longer tries to boot from the install CD. I am stuck. Any advice appreciated.

---

### Post by HavocXphere on 2009-09-18
Huh? The install doesn't touch the BIOS at all.

To get into the BIOS configuration, you need to press a key. Right at the start, before the actual linux part begins.

Unfortunately the key differs depending on the manufacturer. (Google will help find it). Usually its one of the following:
DEL
F8
SHIFT-F2
CTRL-ESC

---

### Post by wizardchef on 2009-09-18
Right. But the F2 key doesn't seem to do anything on boot. That's the key that is assigned to kick one into the BIOS on boot with the Latitude.

---

### Post by earthpigg on 2009-09-18
> **wizardchef said:**
> Right. But the F2 key doesn't seem to do anything on boot. That's the key that is assigned to kick one into the BIOS on boot with the Latitude.

what is the exact model of the laptop?

we will help you out where we can, of course, but entering BIOS is entirely dependent on the model+make of your laptop, and the BIOS it comes with... has nothing to do with any operating system. in fact, BIOS can be considered its own mini operating system - and *each company has completely its own completely unique mini operating system called "BIOS"* with its own problems, issues, features, quirks, etc. 

and to make matters more complex, a single laptop maker may include *a completely different BIOS on different models of laptops*.

and to make matters *even more complex*, laptop makers very rarely let you know before purchase exactly which BIOS comes on that laptop.

google search "problems entering bios Latitude (exact model number here)" and see if you can find an answer there.

if you can't find the answer after 15 minutes of looking around in google, post back here with what you have found and tried, and we will try to help you out.

---

### Post by raymondh on 2009-09-18
> **wizardchef said:**
> Right. But the F2 key doesn't seem to do anything on boot. That's the key that is assigned to kick one into the BIOS on boot with the Latitude.

Dell - XPS, Dimension, Inspiron, Latitude. OptiPlex, Precision, Vostro

    * Press F2 when the Dell logo appears. Press every few seconds until the message Entering Setup appears.
    * Older Dell desktops and laptops may instead use Ctrl+Alt+Enter or Del to enter BIOS.
    * Older Dell laptops may use Fn+Esc or Fn+F1.

[Copied from pcsupport.com.]("http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm")

Good luck.

---

### Post by wizardchef on 2009-09-18
Very, very strange. I tried Ray's instructions using F2 many times, and it just ran right through the BIOS and crashed on ALSA fail. So, I began a kind of random search on the function keys, and it seemed that Fn-F11, which means "pause," suddenly vaulted me back to a Windows bootup! So, the Xubuntu OS was never really fully installed, I guess. Anyway, my next thing is to try and check the BIOS setting to boot from the CD (should already be set), then try the installation again. Strange. I'll post back for others who may be following this thread.

---

### Post by wizardchef on 2009-09-18
The weirdness continues. After getting back to a situation where the laptop (Dell Latitude, 700 MHz Pentium, 256 MB of memory) would boot from the CD, this time I tried the "Try Xubuntu on this computer ..." instead of "Install Xubuntu". The CD whirred and ground for about a minute, loaded the system, and then everything went totally dead like before. Off.

Has anybody ever successfully loaded xubuntu on this laptop? I don't think it wants to run this OS.

---

### Post by raymondh on 2009-09-19
> **wizardchef said:**
> The weirdness continues. After getting back to a situation where the laptop (Dell Latitude, 700 MHz Pentium, 256 MB of memory) would boot from the CD, this time I tried the "Try Xubuntu on this computer ..." instead of "Install Xubuntu". The CD whirred and ground for about a minute, loaded the system, and then everything went totally dead like before. Off.

Has anybody ever successfully loaded xubuntu on this laptop? I don't think it wants to run this OS.

Assuming CD has been checked for defects and MD5 matches .... try the safe graphics mode (press F4) as I am inclined to doubt your graphic card and its' compatibility (but I may be wrong as well)

You may want to try crunchbang (ubuntu-based) or, an alternate install.

Raymond

---

### Post by wizardchef on 2009-09-20
Given up on ubuntu and now trying to get an install with puppy. I am close, but still have boot errors I am dealing with.

---

### Post by presence1960 on 2009-09-20
try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by wizardchef on 2009-09-20
Tried that. That one doesn't work either. I've given up on xubuntu and trying puppy.

---

