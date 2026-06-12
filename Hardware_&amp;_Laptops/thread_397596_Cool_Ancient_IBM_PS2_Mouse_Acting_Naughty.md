---
title: "Cool Ancient IBM PS/2 Mouse Acting Naughty"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Ireclan on 2007-03-30
Hello all. My HP PS/2 mouse works smooth as silk with Ubuntu. Unfortunately, I've been smitten with an ancient IBM PS/2 mouse. I say unfortunately because it works like garbage in Ubuntu- it's slow, slightly "skips" across the screen, and sometimes fails to respond properly to my clicks. I've ruled out a hardware failure in the mouse, as it works PERFECTLY with Windows 2000 on another machine. The weirdest part is, if I boot using the HP mouse, then hot-swap for the IBM one, the ancient one works just as the HP one did (in other words, like a dream). I've already tried troubleshooting this by looking at the xorg.conf file for both mice, and the entries are identical. It seems the only difference between the two as far as Ubuntu is concerned is in the Device Manager, where it detects the HP mouse as an "Intellimouse" (from what I can remember) and the IBM one as a "Generic PS/2 mouse". If at all possible I would like to be able to use this mouse with Ubuntu. Thankyou.

---

### Post by Ireclan on 2007-04-01
Well, in the two days since I posted this topic, it has been buried by six pages worth of content due to lack of replies. My problem hasn't been solved yet, and I'm not about to give up. I've decided to bump this topic whenever it sinks below three page mark, operating on the assumption that if my topic is too deeply buried, I'm never going to receive the help that I need, as I'm sure even the most dedicated of community helpers don't have the time or patience to wade through more than three pages or so.

---

### Post by Gilgad Drumheller on 2007-04-03
I understand the feeling...
I had some problems with a ps/2 mouse that were solved by adding "usb-handoff" to the boot options:
> **equestodo said:**
> ](*,) I'm new to Ubuntu... just installed 6.10 and got the same keyboard problem.
No amount of pressing the keys helped.
Keyboard is recognized all during install, setup, bios, and grub boot loader but the moment I hit 'enter' to select Ubuntu to load the keyboard locks. NumLock light is light solid and doesn't change by hitting the num-lock key.
Keyboard also works on other machines and XP on this machine and works in recovery mode.
Even did a complete re-install and same thing.

I can't even get into the server because it asks for my login and I can't type anything.

Please save my sanity... ](*,) 

BTW... it's a P/S2 Keyboard on a Pent. 4  2.4Ghz w/ 1gb RAM.

Other than that, i know that the xorg.conf file has some important information involving how the mouse is handled.  Have you tried hacking around in there?
I'm going from memory, but i'm pretty sure that there is an option somewhere in there to change both drivers and how the computer interprets the mouse commands.  This link has someone changing drivers: [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

Other than that, in searching to resolve my problem i found this: [http://ubuntuforums.org/showthread.php?t=179818As](http://ubuntuforums.org/showthread.php?t=179818As)
maybe it can be of some use to you.  Specifically, i believe there are other options besides imps that you would want to try, but i can't find where i got that information.

---

