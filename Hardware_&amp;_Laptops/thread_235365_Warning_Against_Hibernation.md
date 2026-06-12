---
title: "Warning Against Hibernation"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by threethirty on 2006-08-13
I'm running Dapper on my Compaq V2000, and I was a hibernation junkie untill two things happened.  The first was I corrupted my root file system when I was using Breezy.  Then a Dist upgrade later worse... I have ruined my laptop, There is a problem with the power now.  I cant get it to post.  The power indicator light comes on and the optical drive spins up, but it wont go any further.  I talked to Tech support and I now Hve to send the whole thing in, I'm gonna love being with a laptop for at lest 2 weeks.

---

### Post by patrickfromspain on 2006-08-13
I don't think it's a dapper problem. But a hardware failure.

---

### Post by threethirty on 2006-08-13
I think it might be too, I just thought I should give fair warning, When I get it bck if I can hibernate for a while (how about a month) with out problems I'll post that here, and if not, I'll also post that

---

### Post by lexxonnet on 2006-08-14
Its quite interesting... I do believe some things are simple hardware failures, but I've had too much trouble with acpi so far.

Firstly... for unknown reasons, both my internal and external harddrive died within a week. This was when I first started using suspend. Suspend itself was a bit of a hit and a miss. Some times, it woke up perfectly, other times it refused to wake up, and some times, It'd wake up and I'd lose my mouse's scroll wheel capability, my fglrx drivers might suddenly conk out(leaving MESA stuff), and sometimes, the computer would just lag. 

Then, once, I was trying out standby(would sometimes work, would sometimes firget to turn off the backlight), and after a few times, my backlight on my lcd just mysteriously stopped working. 

Recently once again, every time I try suspend, and resume, my hard disk goes crazy... it refuses to allow me to browse any directories and goes into a repetitive loop or read... stop... read... stop... read... stop every few seconds..

Finally, I decided not to risk another hdd crash, and stopped suspending my system. As for hibernation, it was always a hit and a miss, so I patched the kernel to use suspend2, and its working like a charm so far. fingers crossed.

---

### Post by anasofiapaixao on 2006-08-14
I am currently not using neither suspend nor hibernation, but let me tell you: In Windows many times the system would just freeze upon rebooting and I would lose all my unsaved data, so... my guess is that hibernation without quirks is more a question of luck than anything else.

---

### Post by kaens on 2006-08-14
I've been running Dapper on a Thinkpad T30 for a couple of weeks now - I started trying out hibernate a day or two ago, and I've noticed a few things.

1: When it comes out of hibernate, the screen flashes around like it's trying  to load the correct video drivers. I can briefly see a little "wrong chipset" error on the screen in between a few of the flashes.

2: Audio programs do not like being put into a state of hibernate while playing (sortave makes sense) Amarok doesn't freeze, but it does hang for a bit then give me an error about the audio file (sorry I don't remember these specific error messages right now - I really don't want to try and recreate them either) and then goes about it's business fine, other than having to restart the song that was playing.

Other than those two things, I haven't had a problem with hibernate.

---

### Post by scenestar on 2006-08-15
> I think it might be too, I just thought I should give fair warning, When I get it bck if I can hibernate for a while (how about a month) with out problems I'll post that here, and if not, I'll also post that

Quit spreading Fud. Just because you F*cked up doesn't mean you should go around scaremongering.

It's hurtfull to the reputation of linux

---

### Post by lexxonnet on 2006-08-15
Mate, just because we complain about a few things doesn't mean we're trying to kill the reputation of linux. You just ruined your reputation big time by saying what you did.

Feedback is what improves linux. If you're worried about hurting Linux's reputation, go look at the bug reports, thats far more "incriminating".

---

