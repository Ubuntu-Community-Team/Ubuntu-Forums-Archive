---
title: "&quot;Live&quot; External Hard Disk Drive"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by jorgealfonso on 2007-06-03
The objective is to make a copy of your "home" Ubuntu System, that could load in any computer.

**Live Hard Disk**

I am wondering about the idea of making a "LIve Hard Disk". Means, to create a partition on an External Hard Disk Drive (HDD) and boot from it in the same way that a live CD does (detecting hardware, regardless the computer you are using) WHILE still having your personal data, customization, and installed programs from session to session.

Think on the possibilities of that! you could have your Ubuntu system TO GO, an run it from whatever computer


**Running it in your home computer, or somewhere else**

Now imagine your system has some sort of script installed that can detect if you are in your "home" computer (by getting some information specific to your hardware...) and then decide  if it should use your "normal" boot (without detecting hardware), or go though the "live" boot (and detect hardware).

Then, you could install that system in your INTERNAL hard disk drive, at home, and use it as a regular Ubuntu system... but making an exact copy of that partition to  an EXTERNAL hard drive would make it work in any computer too (the script would detect you are not "home" and go through the "live" boot).

That means you could always have your "home" ubuntu in your backpack (on your external hard disk), and "refresh it" from time to time (overwrite the partition on your External HDD with an exact copy of your INTERNAL hard disk ).

Note that I keep my personal data (working files, documents, etc...) in a separated partition, so copying the "Ubuntu partition" wouldn't mess-up  my data.


**How to do it**

I am a newbie in Ubuntu, but this should be theoretically possible, as Live CDs exist (and work great).

As far as I see, it would take:
[INDENT]1) Getting a copy of the "live" part of a "live CD" in your Internal HDD
2) Make an script that could detect if you are in your home computer or not (for ex,  checking the MAC address  from your ethernet card, that is unique, to determine if you are at home)
3) If you are at home, boot as before (NO hardware detection)
4) If you are NOT at home, boot "live"  (and detect hardware)
5) Maybe some mess-up with GRUB to make it boot regardless if your are using an internal or an external hard disk.
[/INDENT]
Then you will only need to:
[INDENT]6) Make a copy of your home "system" partition on an external hard drive. The "Gnome Partition Edition" should be able to do the trick.
7) Change the boot order on the "guest" computer's BIOS to "USB" before "local hard disk".  (This, of course, provided the computer could boot from USB... there are turnarounds if the it can't, but that's a subject that should exist in another thread and that I don't want to mix here)
[/INDENT]
The hard part, I think, would be to install the point number 1 (get the "live" thing in your current ubuntu install), and maybe the 5 (have to admit that GRUB is still a mistery to me...).

What do you guys think? do you think this is feasible? do you have some ideas to make it work?

---

### Post by viciouslime on 2007-06-03
Actually you'll find that you can just pull your hard drive out and stick it in another computer and it will boot anyway. The only problem you might come across is xorg, if you have installed binary nvidia/ati drivers and then boot on a computer without a nvidia/ati card then you'll have issues. In the next version of ubuntu though, there isn't even going to be an xorg.conf, so I think this will prety much do what you're after then :)

---

