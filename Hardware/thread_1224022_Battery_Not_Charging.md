---
title: "Battery Not Charging"
date: 2009-07-26
forum: Hardware
---

### Post by sdlynx on 2009-07-26
Hello all,

My battery (HP dv5-1251nr) refuses to charge.  Its very strange, only charges when it's off.  Thing is, it'll charge on Windows also, so it can't be the bios (which I have still taken the liberty to update).  I tried the live disc and it doesn't charge there either.  Also tried recovery mode, not charging.  I tried discharging completely and then plugging it in but while the computer is in Ubuntu it stays at 0.0% forever.

I posted something about this earlier but with no responses and this is more vivid.

Does anybody know a fix for this (or has anyone encountered it too?)?

Please note I'm am about 100% this is not a hardware issue (since the battery works fine on Windows and while off).

sdlynx

---

### Post by ZaHACKieL on 2009-07-27
Are you sure is not charging? I mean, maybe the Ubuntu is telling you that but it's actually charging. Let me know

ZL

---

### Post by sdlynx on 2009-07-27
No no I'm sure.  I drained the battery down to 0 and then turned it onto Ubuntu (on AC), and the battery never got past 0.0%.  Figured it might have been the meter is lying so I unplugged it, and the computer shut off.  So I'm sure.

---

### Post by Dawei87 on 2009-07-27
just wanted to say im having this problem in jaunty 32-bit. when my battery is fully charged it never reads above 86%. and whiles its on i let it discharge down to 10%, but when i plug it in it never charges past that and the hardware light for the battery will stay on saying its charging forever. it will only charge when off. if i find anything out ill post here but i'd love to find a solution to this.

p.s.: everything worked fine in intrepid

edit: my pc is also a hp-dv5 laptop

---

### Post by sdlynx on 2009-07-27
hmm so intrepid worked fine?  I ran the live disc and had the same problem.  Actually today for the first time I did some testing and the battery actually did charge.  Strange cuz every other day it doesn't, and I did nothing different.

And yes, I agree I don't think it is a conky issue (dunno y the battery was changing whether it was charging or not based on if it was running, since it no longer makes a difference).

Have you updated your BIOS? I'm sure its been suggested and might be worth a try if you haven't.  Also, I think its possible your battery might be about to fail.  Mine now takes about an hour to begin charging on Windows, aside from its going good today.

---

### Post by Dawei87 on 2009-07-27
> **sdlynx said:**
> hmm so intrepid worked fine?  I ran the live disc and had the same problem.  Actually today for the first time I did some testing and the battery actually did charge.  Strange cuz every other day it doesn't, and I did nothing different.

And yes, I agree I don't think it is a conky issue (dunno y the battery was changing whether it was charging or not based on if it was running, since it no longer makes a difference).

Have you updated your BIOS? I'm sure its been suggested and might be worth a try if you haven't.  Also, I think its possible your battery might be about to fail.  Mine now takes about an hour to begin charging on Windows, aside from its going good today.

its been a bit since i updated the bios, i think it was january or maybe even december when i did. i dont have windows anymore so im not sure how to update again lol. i may have just fixed it though, this is what i did exactly. i turned on the laptop with 100% battery (although it only showed it had 86%). i let it discharge to about 10%. then i plugged it in. obviously, it did not charge. i had it plugged in for about 30-60 min and then i removed the battery. i left the battery out for 10-20 min and then put it back in (the computer was running on AC the whole time, i never turned it off). after i plugged it back in it began charging again. i am now at 67% and still charging and i have suspended the computer twice. i will post back if i actually reach 100%. i hope this helps some

EDIT: no go. it charged but it stopped at 83.5%. so something is still wrong...

---

### Post by sdlynx on 2009-07-28
Ah, unfortunate.  Haha yesterday I too felt a glimmer of hope, but alas no.  Perhaps I will get a replacement battery and see whether it is Ubuntu or the battery that is causing the problem.

---

### Post by Dawei87 on 2009-07-28
ive gotten mine to work a little better. after doing what i posted previously, i killed gnome-power-manager, deleted all the files in ~/.gnome2/gnome-power-manager, then rebooted and let it discharge all the way, then charged it again. when it discharged it said it had about 20% when the battery died, but when i turned it back on it said 0% and charged up to 98.9% before it stopped. im gonna keep working at this and let you know what happens. i really do think a bios update would help, but i cant figure out how to get it done with an hp computer in linux still...

---

### Post by sdlynx on 2009-07-28
yeah thats a little bit of a problem.  I'd say try Wine but its too risky.  BTW I seem to have traced my problem back to overheating.  I think the battery refuses to charge when it heats up enough.  Today I kept the laptop in a cool place and starting around 20% it charged completely.  I'm pretty sure that'll keep it going, problem is I'm not sure whether this is supposed to happen or if I should contact HP.

---

### Post by philcamlin on 2009-07-28
> **sdlynx said:**
> yeah thats a little bit of a problem.  I'd say try Wine but its too risky.  BTW I seem to have traced my problem back to overheating.  I think the battery refuses to charge when it heats up enough.  Today I kept the laptop in a cool place and starting around 20% it charged completely.  I'm pretty sure that'll keep it going, problem is I'm not sure whether this is supposed to happen or if I should contact HP.

contact hp its  a hardware issue most likely :D

---

### Post by Dawei87 on 2009-07-28
sdlynx, just curious, how old is the pc? and also, it doesnt really seem like something to contact hp about, only because you said it was working fine in windows for you. i could be wrong though. in the end i did try wine to flash my bios, but the .exe crashes just after it extracts and nothings gets done at all.

---

### Post by sdlynx on 2009-07-28
yeah I figured it wouldn't work.

my laptop is only about  a month old actually.  also, sometimes it actually does mess up on windows w/ the charging, but its much less, and I figure it'll be enough lol.  They told me they'd send me a replacement =]

---

### Post by Dawei87 on 2009-07-28
thats good news! i hope the replacement works for you. please post back and let me know! cause if thats the case, i just might get a new one too

---

### Post by Dawei87 on 2009-07-29
well i flashed my bios. it didnt help at all. just thought i'd let you know.

---

### Post by sdlynx on 2009-07-29
yeah I figured, didn't help me either

did you use Windows? if you did, try to get the HP Battery Check and see what it says.

---

### Post by Dawei87 on 2009-07-29
i already wiped windows. i dont think i'll put it back on. i could go back to intrepid, but i couldnt get a few things working right in it. its lame that jaunty works perfectly with all my hardware and software except the battery. if it werent for that, i mght say its better than the compatibility with windows.

---

### Post by sdlynx on 2009-07-30
yeah that sucks

---

### Post by vipulgolchha on 2010-04-29
my laptop is also HP-dv5 
i have been the same problem.

my battery works perfectly in windows Vista

but i donot know what happened top it now wont charge in ubuntu 9.10(which is used to)

HP people won't listen as battery work fine in VISTA .when fully charged(by either switching off or working in vista ) it give 1:15 backup in Ubuntu too.

what the problem ??
please help

---

### Post by vipulgolchha on 2010-04-29
Dawei87
method of putting batt back while in operation does the trick for now.

but lets come up with more practical solution .

---

### Post by sdlynx on 2010-04-29
> **vipulgolchha said:**
> my laptop is also HP-dv5 
i have been the same problem.

my battery works perfectly in windows Vista

but i donot know what happened top it now wont charge in ubuntu 9.10(which is used to)

HP people won't listen as battery work fine in VISTA .when fully charged(by either switching off or working in vista ) it give 1:15 backup in Ubuntu too.

what the problem ??
please help

I could really only narrow the problem down to overheating, because the seemed to be the reason why at least my laptop wouldn't charge.  Try placing the laptop in a cool and letting it charge.

Otherwise, try to cash in on a warranty if you have it.  I got my battery replaced, and all they require is that you run the battery checking software, which, if you get lucky, will report that your battery is failing (try running it while on battery power or something hah).  Every once in a while the battery check would report failure, and I just screenshotted it.

---

### Post by isbiyanto on 2010-05-18
i still confuse :(

---

