---
title: "Bad internal ath9k wifi card..."
date: 2016-02-23
forum: Hardware
---

### Post by bluesfreak72 on 2016-02-23
Hi there - I have a laptop running Ubuntu Wily.  As you can see in the title, it has a bad internal wifi card.  If I boot the laptop and try to login right away, I get a black screen instead of Unity.  If I wait 10-15 minutes after booting it, it logs in correctly.  Since the wifi card is the only issue in the laptop, I'm suspecting that the initial boot sequence is looking for it - and the CPU is given an error for several minutes before it figures out that it's bad and I have a USB wifi card plugged in.  On this laptop, it has a wifi switch that I've tried to turn off, but that doesn't allow the USB wifi card to work.  I have also tried turning the wifi off with the keyboard shortcut.

My question is this:  Is there a way to either trick the CPU into thinking the internal wifi is working properly or disable the check for it and be able to login right away?  I will be more than happy to post output to any commands to help in figuring this out.

bluesfreak72

---

### Post by weatherman2 on 2016-02-23
It's not clear to me why you think it's specifically the wireless card that is your problem.  But there is a really easy way to test that: unplug the wireless card.  OK, how "easy" that is depends on the make/model of laptop.  Often you can access the wireless card from the bottom of the laptop by removing a panel with a few screws.  Then you might find the wireless card near the RAM or in its own compartment.  It should be held in with a screw or a couple of clips.  There will be two (or three) antenna wires clipped on to it.  Carefully pull the wires off - take a neddlenose pliers and grab the metal end and kind of rotate the end and pull the wireless clip UP and pop off.  The antenna wires are just clipped on, not soldered or anything.

Sometimes the wireless card in a laptop model is buried inside under the keyboard and is a challenge to access.  Depends on the make/model of laptop.

(There are lots of demo videos on YouTube that show how to remove/replace the wireless card on various makes/models.  There are also "tear-down" guides for most models online, and you might even find a hardware manual showing you exactly step by step how to remove it.)

Then try booting again without the wireless card.  If you have the same paused boot, you know the wireless card had nothing to do with it.

FYI, if your laptop is NOT an HP or Lenovo (or IBM), you can replace that card with another one.  I like the Intel 6235 - dual band + bluetooth, has worked great for me in a couple of laptops.  Often about $10 USD on eBay.  But HP and Lenovo laptops "whitelist" their wireless cards and don't allow you to use any card but a few that are approved for that model.  So I do not buy HP or Lenovo laptops.   I've upgraded lots of laptop wireless cards over the years in other brands - Dell, Acer, Toshiba, etc. - successfully.

If you get the 6235, get a used one (not a "new" one from Asia - I've had bad luck with engineering samples and such) and get one NOT for HP or Lenovo.

---

### Post by bluesfreak72 on 2016-02-23
I guess another option would be to make the CPU think the USB wifi card is the internal.

---

### Post by weatherman2 on 2016-02-23
I'm not sure how you would do that, but I can remove the wireless card from the average laptop in about 2 minutes.

---

### Post by jeremy31 on 2016-02-23
It may be possible to disable the internal card in BIOS

---

