---
title: "Asus M2N-E Sli Motherboard and Pheonix BIOS issues (this doesn't relate to any OS)."
date: 2010-06-08
forum: Hardware
---

### Post by k3lt01 on 2010-06-08
Hi everyone.

I was given a few computers a couple of weeks ago that I have done up to give away to people who cannot afford to buy a PC. I have worked through various issues with most of them (e.g. flat CMOS 3 volt batteries) but have come across an issue that I cannot for the life of me explain what has happened to cause it. Let me explain.

One of the PCs come with an 2.6 GHz AMD64 CPU on an ASUS M2N-E Sli motherboard, it has 2GB of RAM  and a 250GB Western Digital SATA drive. The installation of Ubuntu went smoothly taking no longer than 10 minutes, I set up everything so the new user could just boot up and go. This PC has worked for a week and behaved without a hitch until a couple of days ago I booted it and nothing happened.

Aftr checking all the connections etc (without taking anything off) I found the internal speaker had a broken wire. I fitted a new speaker and I have now got the Pheonix BIOS beeping 1 long and 2 short on the POST test. I have checked on the net and some sites suggest there is no such beep signal while others say it is a faulty PCI Video card, and others still say that it is a bad checksum on the motherboard ROM which means I'll have to just chuck the motherboard out and get a new one.

SOOOOOOOO, now to my question for those of you knowledgeable people who deal with this type of thing more than I do. Is this motherboard salvageable? If yes what can I do for it? Is there a testing procedure I can go through apart from changing video cards (which I have already done)? It would be a real pity to just throw such a great setup out (which I wouldn't do I'd just get another motherboard).

---

### Post by Yellow Pasque on 2010-06-09
Have you tried clearing the CMOS by using the jumper?
See the jumper section in [http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M2N-E/e2830_m2n-e_sli.pdf](http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M2N-E/e2830_m2n-e_sli.pdf)

---

### Post by k3lt01 on 2010-06-09
> **Temüjin said:**
> Have you tried clearing the CMOS by using the jumper?
See the jumper section in [http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M2N-E/e2830_m2n-e_sli.pdf](http://dlcdnet.asus.com/pub/ASUS/mb/socketAM2/M2N-E/e2830_m2n-e_sli.pdf)Thanks for your reply. the answer to your question is Yes. I have also changed the battery to a known good one as well.

I also have that pdf, I download everything I can get for the computers I am given before I start working on them.

I'd update the BIOS if I could just get the thing to boot into something past the POST test.

---

### Post by cascade9 on 2010-06-09
From what I know, Phoenix changed the beep codes at one point, from the 'old' system with only about 40 beeps to the new system with over 100. The old system was pre1994 IIRC, so you've got the new system, but that could be the source of some confusion. 

If you are lucky, sometimes the error code will appaer on screen. That doesnt always happen though, which is a pity. 

About all I can think of at the moment is to try taking the RAM or CPU out, and see if that changes the error code. Not that helpful at the moment, but it should give you a bit more of an idea as to where the issue is.

---

### Post by k3lt01 on 2010-06-09
Thanks cascade, will try your suggestions tomorrow after I get back from town.

Nothing is coming up on the screen, that is one reason I changed the video card to a known good one. I have tried a PCI card and a GPU card neither changed anything.

I will try the RAM and CPU tomorrow.

Thanks again.

---

### Post by k3lt01 on 2010-06-13
I finally got back to this machine this morning. I took the CPU out, made sure everything was clean (good connections etc), did the same with the RAM stick and it still has the same beep code. I'm not at my wits end with the machine but I don't know what else I can try with the resources I have available so I would appreciate any other hints and ideas that anyone has.

---

### Post by cascade9 on 2010-06-13
Hmmm....sorry if I didnt make myself clear, or I have misread what you did k3lt01. 

I didnt mean 'take them out and make sure they are clean etc', I meant take the RAM and/or CPU out then try to boot. If you get the same error code with CPU and RAM out, then whatever is causing the error is probably unfixable.

---

### Post by k3lt01 on 2010-06-13
My fault cascade I didn't understand what you meant. Shall try it again later today, hopefully.

Have a good long weekend.

---

