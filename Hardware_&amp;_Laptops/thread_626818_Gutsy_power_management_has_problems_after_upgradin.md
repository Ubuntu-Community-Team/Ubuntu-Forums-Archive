---
title: "Gutsy power management has problems after upgrading"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by rrwo on 2007-11-29
I've upgraded to gutsy, and am having some problems with power management.

[LIST]
[*] The battery life now seems to have halved (from four to two hours!), despite claims of better power management under gutsy.
[*] The screen on my laptop doesn't dim when it's on battery. But dimming the screen doesn't affect reported battery life
[/LIST]

Any idea how to fix these?

---

### Post by puikku on 2007-12-08
Hi,

I've had similiar problems. I have IBM X40 laptop.  I haven't really measured battery performance but at least some power management functionality isn't working. Laptop screen isn't anymore recognized, so power manager doesn't automatcally adjust its brightness on when on ac or battery (7.04 recognizes). Also dimming doesn't work. And power display and suspend power management timers don't work for me. 

Very irritating and dull problems. I've been already thinking on trying 7.04 as 7.10 seems regression over it. Based on what you say about battery performance it sound even more tempting. I just wonder is there any other ditribution with beter support for laptops.

puikku

---

### Post by osiris2258 on 2007-12-08
I am also having trouble, but my video card is NVIDIA. with me, suspend just pops right back to the password prompt, no motion from me it just comes right back up. Hibernate dumps the whole computer. I filed a bug report but no word other than it has to do with the kernel.

---

### Post by rrwo on 2007-12-09
Here's something I found: I use Xfce, so decided to see what Xfce's battery monitor applet said. It claimed I had about 3.5 hours, where Gnome's Power Manager applet at the same time claimed I had less.  As my computer idled, Xfce's power applet increased it's estimated battery life.

If it wasn't for the fact that GPM is connected to the power daemon and will hibernate or suspend the system when I close the laptop lid, I'd just use Xfce's. (It's a pain to set up other software to do this, but if the problem isn't fixed, I just might do that.)

---

### Post by HokeyFry on 2007-12-09
You can tell XFCE to hibernate or suspend the laptop when you close the lid. I think it's in the power settings, and I used to go i there to tell it to do nothing on close. But Hibernate and Suspend were definitely options in that menu.

---

### Post by rrwo on 2007-12-19
What Xfce power settings? I only see Gnome power settings.

---

### Post by Awperator on 2008-01-20
> **rrwo said:**
> What Xfce power settings? I only see Gnome power settings.

I too am looking for power management settings for Xfce (mythbuntu 7.10). If someone can please help that would be appreciated.

Thank you so much

---

### Post by rrwo on 2008-03-08
I think there are no Xfce power settings. Just the Gnome Power Manager.

---

