---
title: "Ubuntu 8.04 installs but 8.10 doesn't?"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by ConicalLinuxHead on 2008-12-29
Well, actually the last Ubuntu that worked out of the box was 7.10. I have a Dell Inspiron 530s that came with Vista... Ugh. I am typing this from the 8.04 live CD, which I was able to boot by changing a bios setting as I found from a google. 8.10 doesn't boot even if I change that setting, I've also tried to upgrade to 8.10 with the updating tool, it upgrades fine, but after the loading bar it just shows be a black screen. I can hear the drums, so it must be a graphical error? Without changing the bios setting, I should mention it's something about the SATA mode, from IDE to RAID, everything after 7.10 gives me the black screen. Fedora gives me the same thing, OpenSuSE is the only Linux that works. But Ubuntu is better than any one of those, right? :P Can I get any help with this? Thanks!

Also, I should mention that I'm a fairly knowledgeable Linux user, I can use the terminal and stuff, write a bit of code, yeah.

---

### Post by ConicalLinuxHead on 2008-12-29
What, 800 people online and nobody can answer this?

I see threads that have been posted for 10 minutes with 20 replies!

Anyway

I should clear up a few things

System: Dell Inspiron 530s, didn't come with Ubuntu. Came with *vomit* Vista.

Ubuntu 7.10 was the last one that worked out of the box, everything after Feisty Fawn doesn't work.

I am able to get 8.04 to install by changing my SATA setting from IDE to RAID.

8.10, Fedora, etc won't boot, gives me a black screen, I think when loading X.

I heard that 8.10's livecd booting process was messed up? Is this true?

When I dist-upgrade to 8.10 from 8.04, thinking that it was only the LiveCD, it doesn't work either. I get a black screen, with my monitor's "No signal" message, but I can hear the drums of the login screen.

PLEASE help. I don't want to have to use an out of date Ubuntu, or OpenSuSE.

---

### Post by ConicalLinuxHead on 2008-12-29
Would my graphics card drivers have anything to do with it?

Wait, all this multiposting, is it bad? It wasn't in the rules, was it?

Anyway, I've installed my graphics card drivers. I guess I'll try dist-upgrading again. :(

---

### Post by d8a on 2008-12-29
Hi!

I'm not sure if I'm able to help, but I'll try. 

Do you by any chance have a nvidia graphics card? I remember having the exact same issue (but I can't remember how I solved it). 

Anyway even if you don't have a nvidia graphics card, this is still worth a shot: Try booting to your blank login screen. Then CTRL+ALT+F1 to the terminal. That should work. Then edit your xorg.conf by typing

```
sudo nano /etc/X11/xorg.conf
```

and find the "Section "Device"", it should look similar to this:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection

Then change the Driver to "vesa" and restart the xserver or reboot and see if that solves it. Afterwards you can try to install the proprietary driver (because you probably won't be very happy with the vesa driver) and/or tweak your xorg.conf.

---

### Post by ConicalLinuxHead on 2008-12-29
Whoops, should have mentioned this, but I have an ATI Radeon HD 2400 pro. Thanks, I'll dist-upgrade again, and see what happens when I try this.

---

### Post by mikewhatever on 2008-12-29
> **ConicalLinuxHead said:**
> 
I heard that 8.10's livecd booting process was messed up? Is this true?


NO.
Just posted to make you feel better, I don't really know what's wrong.):P

---

### Post by ConicalLinuxHead on 2008-12-29
Thanks all you guys, I figured it out.

I had to install 8.04, install the ATI drivers, dist-upgrade to 8.10, and it worked. My problem was that 8.10 didn't support my card out of the box, but 8.04 did. Fix please?

Well, I'll probably not be on the forums at all now, so bye.

---

