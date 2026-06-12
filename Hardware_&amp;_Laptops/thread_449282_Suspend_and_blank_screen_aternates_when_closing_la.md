---
title: "Suspend and blank screen aternates when closing laptop lid"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Abdi110 on 2007-05-20
Hi. So in the past week I've been having this weird issue where Gnome will only suspend every other time I close the laptop screen. If I make the machine go into suspend through the quit menu it works fine every time. Any chance anyone heard of this before?

I'm running a ThinkPad T41 with a radeon 9000 mobile, Feisty.

---

### Post by racekarl on 2007-06-27
I have the exact same problem on my Thinkpad T42 running 7.04.  Did you ever find an answer to this?

---

### Post by Abdi110 on 2007-06-27
Sadly no, from what I can tell gnome-power-manager isn't picking up on half of the acpi messages. I'm wondering if this is because of dbus. If anyone can recommend a neat way of going back a few versions of dbus, I'd really appreciate it.

My work around right now is to just leave lid shut at kill screen, and go into sleep through FN+F4. You can also setup the same thing through the power button on one of the tabs in gpm.

---

### Post by racekarl on 2007-06-28
Happily, I did find a solution to this, at least one that works for me.  

Apparently if you've turned on proposed changes in synaptic, a HAL upgrade broke suspend for many people.

I found this thread: [http://ubuntuforums.org/showthread.php?p=2655073](http://ubuntuforums.org/showthread.php?p=2655073)

And rolled back the HAL updates as described, now suspend works on lid close every time for me.  Hope that helps you too

---

### Post by Abdi110 on 2007-06-28
Yay thanks!

---

