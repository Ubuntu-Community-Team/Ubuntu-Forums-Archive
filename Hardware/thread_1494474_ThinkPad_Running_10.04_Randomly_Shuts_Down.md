---
title: "ThinkPad Running 10.04 Randomly Shuts Down"
date: 2010-05-27
forum: Hardware
---

### Post by seagullplayer77 on 2010-05-27
I had originally thought this was an Ubuntu issue, but now, I'm not so sure. Here's what I've got:

I was browsing the Web last night, when all of a sudden, my ThinkPad T60P died. It didn't shut down---it just powered off instantly. I thought it was kind of odd, but I figured it was Ubuntu shutting down because the battery was low. I thought "Whatever," tinkered with the power management settings, and called it a night.

A little while ago, the exact same thing happened. I plugged into the AC adapter, booted Ubuntu again, unplugged the AC adapter, and a little while later, it died again. Did the experiment one more time and got the same exact outcome. 

This isn't very scientific, but I've found that the laptop will shut itself off when, according to Ubuntu, the battery has about a 25% charge. I've also found that upon shutting down, the laptop won't fire up again on battery power. If it does, it'll get to the BIOS screen and die again, after which point it won't start at all.

After doing some Googling and thinking it through, I'm starting to think that the battery is bad. If one of the final cells in the chain---say, the one that's around the 25% mark---is toast, that would explain why it keeps dying in approximately the same "place," and it would also explain why after dying, the laptop won't start again. Bad battery cell = no juice = no boot sequence. 

And FWIW, I've been running on AC power for the past 24 minutes with no issues. The most I was able to get on the battery was about 12, but that's because I kept hovering around the 20% to 30% range to diagnose the issue. I've had it running (sleeping, mostly) since this morning and it ran fine until it the charge got into the mid-twenties.

The original battery went dead a few months ago and I replaced it with a knock-off I bought on Amazon. Could the knock-off have gone bad this quickly?

What say ye?

---

### Post by tgalati4 on 2010-05-27
Your battery is made of catfood.

---

### Post by seagullplayer77 on 2010-05-27
> **tgalati4 said:**
> Your battery is made of catfood.

I take it that's a poetic way of telling me that my battery needs replacing?

I guess I could just keep using this one, and remember to plug it in when it gets to 30% ](*,).

Update: Been running on AC power for fifty minutes with no issues. Looking more and more like a bad battery . . . any way to test it, to make sure?

---

### Post by seagullplayer77 on 2010-05-27
Another update:

I fired the laptop up and let it sit on the BIOS configuration screen until the battery died. I plugged it into the AC adapter and started it up, and I got a flashing orange battery light, which means that the battery is very low. That's a good sign, since I wasn't getting that before. Also, the Ubuntu battery manager reads the battery as only having a 1.5% charge, which is also a good thing.

It seems like for whatever reason, the battery and the computer weren't communicating properly and now, it seems like they are.

---

### Post by mindpowerz on 2010-05-27
Your battery really needs to be replaced in this case. It's pretty obvious.

---

### Post by tgalati4 on 2010-05-27
Where was your battery made?

---

### Post by gradinaruvasile on 2010-05-27
I've seen an R61 (or is it T61?-its the more expensive model) with a semi-dead battery after less than a year. It was running Windows XP BTW.
The battery discharged to a certain extent and then it just powered off despite the power manager having shown 30 or so % left.

---

### Post by seagullplayer77 on 2010-05-27
China, I believe. Isn't that where everything is made these days?

FWIW, I'm guessing that the original battery was several years old. I bought the computer used on Craig's List, and I've got the feeling that the battery it came with was probably the original IBM battery.

Oh well. Ever since letting the battery run dry in the BIOS, everything seems okay. Then again, I suppose letting that happen may have just reset everything into believing that 25% is really 0%. I don't know. 

Lesson learned: don't buy aftermarket batteries.

---

