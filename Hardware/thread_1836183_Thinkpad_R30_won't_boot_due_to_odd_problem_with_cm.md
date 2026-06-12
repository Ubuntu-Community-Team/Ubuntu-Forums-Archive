---
title: "Thinkpad R30 won't boot due to odd problem with cmos battery"
date: 2011-08-30
forum: Hardware
---

### Post by Antarctica32 on 2011-08-30
Ok, well it all started when my theology teacher gave me his old laptop (thinkpad R30, Pentium 3, 128 mbs ram, rather old) So I could install linux and use it for my eagle scout project:
 [http://ubuntuforums.org/showthread.php?t=1676724]("http://ubuntuforums.org/showthread.php?t=1676724")

So i took it home and booted it and happened to notice that he had created a supervisor password. It prevented me from accessing the bios setup, which really wasn't that big of a problem because I could find the exact specs from inside linux eventually. Nevertheless i took it back to school the next day and asked if he remembered the password, he didn't. I spent a few weeks trying to find a reasonable way to reset the supervisor password with no luck. In the end I attempted to install lucid with no luck (it was worth a shot).  after that the R30 spent a few months untouched in my basement, until yesterday when i decided to try to install xubuntu. I wanted to boot into windows 1 last time so i started it and the ibm thinkpad screen came up with the "F1 for setup, F12 for temporary boot device"after that I expected to see the windows 2000 boot screen but instead saw 2 error messages 1:[SIZE="2"]System battery is dead replace and run setup[/SIZE] 2: [SIZE="2"]real time clock error.[/SIZE] So i figure it would just boot into 2000 with the stupid cmos battery being wrong and I really wouldn't care. But instead a password prompt came up. I figured that it wanted me to reset the clock in bios, but to access bios i need the password. So after about 3 hours of me and my dad trying passwords and different things to get around having to reset the time my dad discovered that you can just press enter without entering a password and it will take you to bios, but you can't do anything important ie: change the time or change the password. I think I am really stuck on this one. I now turn to you all here at the ubuntu forums, you are my only hope. I offer a reward of 3 Kudos and 5 Internets to the user that either solves my problem or helps me the most.

---

### Post by Antarctica32 on 2011-08-30
aren't there ways of replacing the bios with a new one? I will look into that.

---

### Post by Antarctica32 on 2011-08-30
bump

---

### Post by Redblade20XX on 2011-08-30
Did you try and remove the actual cmos battery inside the laptop (requires disassembling the laptop and removing the battery for a minute or two)? If I remembered correct, that was a way to remove bio passwords.:p

- Red

---

### Post by Antarctica32 on 2011-09-02
Sadly i can not find where the actual battery is. I have looked under the rechargeable battery, where it usually is on thinkpads. I have taken apart the whole back side and still can not find it. I did hear someone say it was under the keyboard, but i don't know how to get under there.

---

### Post by trundlenut on 2011-09-02
I wouldn't be surprised if it's under the top of the case to the left of the touch pad.  However access will probably require dismantling the whole thing.

---

### Post by Antarctica32 on 2011-09-03
Ok, well I did find the battery (under the keyboard) and i did take it out. I then booted the machine and it gave me 2 different errors. Something like : cmos battery not detected, reverting to default settings. and another that said something about some pci problem.

---

### Post by Redblade20XX on 2011-09-03
Forgive me if I sound cynical but did you reinsert the cmos battery? :confused:
-Red

---

### Post by .... on 2011-09-03
Your laptop probably doesn't have enough RAM for Xubuntu.  I would try Lubuntu, or better yet, something really light like Crunchbang Or Deli Linux.

Resetting the password sucks and involves soldering and building circuits: [http://www.allservice.ro/forum/viewtopic.php?t=47&start=0](http://www.allservice.ro/forum/viewtopic.php?t=47&start=0)
The author says it's easy but I've personally never had success soldering anything (maybe I didn't have the right tools).

---

### Post by Antarctica32 on 2011-09-04
> **Redblade20XX said:**
> Forgive me if I sound cynical but did you reinsert the cmos battery? :confused:
-Red

Wait! Your supposed to put it back!? Sorry I'm new to this whole hacker thing. I will be right on that after I finish replacing the graphics card on this old p3 my friends dad gave me

---

### Post by Antarctica32 on 2011-09-04
I put it back and its still the same.

---

### Post by trundlenut on 2011-09-05
You need to fit a new battery as the current one has run out of juice!

---

