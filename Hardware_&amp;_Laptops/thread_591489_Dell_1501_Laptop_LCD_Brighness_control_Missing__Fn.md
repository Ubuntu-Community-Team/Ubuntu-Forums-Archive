---
title: "Dell 1501 Laptop LCD Brighness control Missing / Fn unworking"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by TwiceOver on 2007-10-25
I've been fighting this problem since 7.04.  I am trying to fix the brightness issue with this laptop.  I was hoping 7.10 would fix the problem, however, it actually got worse.

Problem:  There is no brightness slider in Gnome Power Settings, and my Fn keys will not change the brightness.  Compared to Windows my brightness is always at about 70% when in Ubuntu.

I've changed settings in the Gnome Config Editor with no help.  I found one solution online that recommended adding "blacklist video" to the modprobe.d/blacklist file.  This actually made my screen 100%+ brightness continuously.  

Battery or AC does not make a difference.  In 7.04 I was able to use the function keys to change only one level.  I basically had the choice between ~40% & ~80% brightness.  This didn't always work when hitting the keys, but it was better than nothing, which is what I have now.

Specs:
Dell 1501 15.4"
Ati xpress 1150 Video
AMD TL-56 Turion X2
Dual Boot Vista

OS:
Ubuntu 7.10 Gutsy
Fully Patched
Fresh install + Some apps (Otherwise, unchanged config pages)

Let me know if you have any ideas or if you need me to dump some log files.

---

### Post by TwiceOver on 2007-10-28
Just wanted to give this a nudge.  I've been Googling to no avail.

---

### Post by Baby Boy on 2007-10-28
If you don't already know about Ubuntu1501 blog, you should definitely take a look at it. The link is in my sig.

About those two issues, from what I've read on that blog brightness does work, but only with BIOS 1.7 (you have to downgrade). And the suspend/hibernate worked for me in Feisty, but not in Gutsy. You should take a look at this page. 

[http://ubuntu1501.blogspot.com/2007/09/ubuntu-710-gutsy-gibbon-beta-overview.html](http://ubuntu1501.blogspot.com/2007/09/ubuntu-710-gutsy-gibbon-beta-overview.html)

---

### Post by TwiceOver on 2007-10-28
> **Baby Boy said:**
> If you don't already know about Ubuntu1501 blog, you should definitely take a look at it. The link is in my sig.

About those two issues, from what I've read on that blog brightness does work, but only with BIOS 1.7 (you have to downgrade). And the suspend/hibernate worked for me in Feisty, but not in Gutsy. You should take a look at this page. 

[http://ubuntu1501.blogspot.com/2007/09/ubuntu-710-gutsy-gibbon-beta-overview.html](http://ubuntu1501.blogspot.com/2007/09/ubuntu-710-gutsy-gibbon-beta-overview.html)

Yeah I have read his blog.  Unfortunately I can't seem to find this 1.7 bios.  Kinda sucks to have to downgrade to fix this.

---

### Post by Baby Boy on 2007-10-28
> **TwiceOver said:**
> Yeah I have read his blog.  Unfortunately I can't seem to find this 1.7 bios.  Kinda sucks to have to downgrade to fix this.
Yeah, I know. You can still adjust your brightness with Fn key while booting in GRUB menu (at least that worked in Feisty, haven't tried it in Gutsy yet).

---

### Post by TwiceOver on 2007-10-28
> **Baby Boy said:**
> Yeah, I know. You can still adjust your brightness with Fn key while booting in GRUB menu (at least that worked in Feisty, haven't tried it in Gutsy yet).

Nope, that doesn't work now.

I've been trying to flash my bios to the 1.7 however, when I run the utility in Vista, the screen corrupts and the system reboots.

I've been trying to find a way in DOS, but the image is too big for a floppy.

---

### Post by x-point on 2007-10-30
> **TwiceOver said:**
> Nope, that doesn't work now.

I've been trying to flash my bios to the 1.7 however, when I run the utility in Vista, the screen corrupts and the system reboots.

I've been trying to find a way in DOS, but the image is too big for a floppy.

Here is temp workaround on how to adjust brightness in Gutsy:

[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/]("http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/")

---

### Post by Baby Boy on 2007-10-30
> **x-point said:**
> Here is temp workaround on how to adjust brightness in Gutsy:

[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/]("http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/")

Thanks a million, *any* way to adjust brightness without screwing it up and making it go 100% is worth it's weight in gold for me. BTW, tinkering with Fn keys in Feisty only made it 100% irreversibly, so technically, upgrading to Gutsy was no loss for me brightness-wise.

---

### Post by TwiceOver on 2007-11-07
> **x-point said:**
> Here is temp workaround on how to adjust brightness in Gutsy:

[http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/]("http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/")

Yeah I had seen this, sorry I didn't get back to the community.  Anfortunately for me, the only numbers that work are 50 and 100.  50 isn't bad, but still wish I could use increments in between.

---

