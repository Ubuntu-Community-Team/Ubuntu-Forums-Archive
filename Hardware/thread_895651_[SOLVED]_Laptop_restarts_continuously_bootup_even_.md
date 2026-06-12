---
title: "[SOLVED] Laptop restarts continuously bootup even after ubuntu reinstallation"
date: 2008-08-20
forum: Hardware
---

### Post by Coward on 2008-08-20
I own a hp dv6000z. It's worked fine with Ubuntu for over a year (with some minor fixes of course) and I installed Hardy fresh from a disk months ago.

On Monday my laptop's screen stayed blank after I opened the laptop lid as it sometimes does, so I turned it off by holding the power button. Bad, I know, but the usual key combinations weren't working.

Then the laptop could not turn on. The lights came on, it waited for a few seconds, then restarted. The lights would come on, and this repeated until I held the power button to turn it off.

It worked once the next day, so I managed to backup my most important files. I thought maybe the laptop had just been overheated, but then the next time I tried turning on my laptop I got the repeating restart again. I see a blank screen on restart and hitting ctrl+alt+f1 or f1 or f8 does nothing.

So I started looking up reasons this might happen on the internet and talking to the local computer store guy. The internet suggested maybe bad ram, but trying to turn it on with one ram stick followed by trying it with the other got the same results. I don't have extra ram sticks around to test. The employee at the local computer store suggested bad drivers, but I've reinstalled Ubuntu completely so I don't know if that rules bad drivers out since the problem persists.

Occasionally it randomly loads and all is fine. It still has all the defaults since I just reinstalled it. This means I can run commands if you want me to. It does it's repeated restarting even with a live disk in, I managed the install just because as I said sometimes it randomly works.

Any ideas of what I should try next? By posting this in the Ubuntu forums I am not implying this is Ubuntu's fault, maybe it's hardware. I don't know.

---

### Post by libra1780 on 2008-08-24
if it's a ram problem you can try memtest.
it's an option in the boot menu (hit esc) found in the live cd boot menu as well

it does does reboot before showing "hit esc for boot menu.." as well, right? (=hardware)

---

### Post by Coward on 2008-08-30
I called hp and they had me do some hardware testing in the bios. It was the motherboard. Thanks for your help.

---

