---
title: "accidentally suspended my desktop machine"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by allans on 2007-11-18
I realise that this is generally for laptop trouble shooting, but my problem is to do with a desktop machine that has been suspended...when I come to power the machine back on, the computer does not recognise my usb mouse, ps2 keyboard or monitor.

The hard drive lights up for a couple of seconds, and I can open my dvd drive - but I cannot stop it from doing this when starting up even after unplugging the computer from the mains, it still tries and fails to wake up.

Does anyone have any ideas?

Thanks in advance,

Allan

---

### Post by nick_h on 2007-11-18
Are you saying that you can't even see the BIOS screen or access the BIOS settings?

---

### Post by allans on 2007-11-18
yeah - which is what's worrying as I can't change any settings etc.  I've got no signal to my monitor, no keyboard and no mouse! Anyone have any experience of this?

allan

---

### Post by nick_h on 2007-11-21
Did you manage to get it working?

---

### Post by allans on 2007-11-25
yeah i did thanks - simply remove all of the ram from the machine and then put it back in again.  How user friendly!  If this had happened on a laptop I'd have been really stuck.  I'm a big fan of ubuntu but shocked that something like this could happen in a final release - will be filling a bug on launchpad I think.

---

### Post by nick_h on 2007-11-25
It doesn't sound like an Ubuntu problem to me.  It might just be a coincidence that the RAM got unseated slightly.  Running a memtest would be a good idea.

---

### Post by Bigbird999 on 2007-11-25
This is exactly what happens on my laptop trying to resume from suspend.      My only way out is to unplug and remove the battery.  This resets the CSMOS.  When you removed the RAM, you caused your BIOS to revert to defaults and allow you to boot again.  You could have accomplished the same thing by removing the battery and jumper to reset the defaults or maybe by leaving it unplugged for a longer time (and hour)  before rebooting but YMMV on unplugging.  If you check your mobo or computer user manual it should explain how to reset your default bios settings

I am sure that the guys at Ubuntu are working really hard to solve this really annoying suspend/hibernate issue.  For most laptop users it is a killer concern.  For desktops, not so much.  Unless, of course, you accidentally suspend you desktop and it won't resume.  

BB

---

