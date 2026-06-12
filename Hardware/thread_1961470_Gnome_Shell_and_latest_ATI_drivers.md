---
title: "Gnome Shell and latest ATI drivers"
date: 2012-04-19
forum: Hardware
---

### Post by paradajz on 2012-04-19
Few months ago I installed ati linux drivers in Ubuntu and my gnome shell went nuts, driver release after that (I don't know which anymore) broke my complete system, so, is the latest ati driver any good with latest gnome shell?

---

### Post by Mark Phelps on 2012-04-19
IF your ATI card is one of the unfortunate "legacy" cards, installing ANY recent ATI restricted drivers is going to trash the display and possibly the OS as well.

If you don't know the make and model card, open a terminal, enter "lspci" and look for the line containing "VGA".  Then, post that information back here. We'll be able to tell you if that is a "legacy" card.

---

### Post by paradajz on 2012-04-19
```
igor@igor-ubuntu:~$ lspci
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]

```

---

### Post by Mark Phelps on 2012-04-19
All we needed was the VGA line -- which says you have a Mobility Radeon HD 4200 -- which is NOT a legacy card.

So, it should work fine with the latest (v12.3) Catalyst drivers.

---

### Post by paradajz on 2012-04-19
Okay, I've edited the output. I need someone to verifiy that since I dont' want corrupted system after I do it.

---

### Post by MonkeyPaw on 2012-04-19
> **Mark Phelps said:**
> All we needed was the VGA line -- which says you have a Mobility Radeon HD 4200 -- which is NOT a legacy card.

So, it should work fine with the latest (v12.3) Catalyst drivers.

Actually, I had issues with my 4250 IGP with the latest catalysts. The screen was pixelated, and if I went into CCC, it said "no compatible hardware found." Maybe AMD dropped support or there's an issue with the 12.3s and the 880G IGP.

It ran fine with the non-proprietary drivers, but I put in a 8800GTS instead for the long run.

Perhaps try searching AMD.com for the 12.2s and see how it goes? You'll need to uninstall the 12.3s first.

---

### Post by MonkeyPaw on 2012-04-19
support.AMD.com does offer older catalyst versions. Just fill in your hardware type, pick 32 or 64bit, and when it shows you the 12.3 download,  click on "Previous Drivers and Software" down below.

---

### Post by QIII on 2012-04-19
Gnome shell does not work well with the proprietary ATI driver.

Notice the order in which I wrote that.  This is on the Gnome end and it is a known issue that is being worked on.  I have one machine that has a 4200 series that works fine with Xubuntu and Kubuntu.  I have another with a 58xx series, booting the same, and it also works fine.  Gnome does not work on either machine.

The issue is NOT that the card is old.  The 42xx series is still supported.  The legacy driver would not work in this case.  The 12.3 driver from the repo is fine other than for Gnome.  I am finding the same with Precise.  

Edit:  As an important note, I must say that I don't fault the Gnome devs.  They hqve an aweful lot on their plates and they are working hard.

---

### Post by paradajz on 2012-04-26
Thanks for the info, one more question: so Gnome Shell doesn't work with ATI drivers, what about Unity? I'm actually starting to like to so I'm curious.

---

### Post by cabez0n on 2012-11-28
> **Mark Phelps said:**
> All we needed was the VGA line -- which says you have a Mobility Radeon HD 4200 -- which is NOT a legacy card.

So, it should work fine with the latest (v12.3) Catalyst drivers.

Actually, that is a legacy card. At least when you fill up the info on amd site it takes you to the legacy driver download. 

I also have the same card and it is not supported by non-legacy drivers.

---

