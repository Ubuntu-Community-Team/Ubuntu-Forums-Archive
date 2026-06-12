---
title: "Fan in a Dell 1501 under Gutsy"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by lolcese on 2007-10-02
I made a fresh copy  of Gutsy-64 in my Dell Inspiron 1501, everything works fine except that the fan is always working. Any ideas?
Thanks

---

### Post by tgm4883 on 2007-10-02
sounds like maybe your scaling isn't working and your processor is always at 100%

---

### Post by josephcherng on 2007-10-08
actually, i'm having a similar issue...it seems that the fan DOES turn off...only after a long long time.
Does anyone else with a 1501 notice that the laptop is unusually hot? 
Although gutsy runs beautifully, it probably still needs these last 10 days to iron out some problems.

A few minor problems i've encountered on 7.10:

Display: cannot adjust screen brightness
Sound: Cannot turn System beep off.
Fan: Does not seem to turn off.
Also, it seems to have somewhat caused some audio problems on Vista. i can no longer hear the error sounds...

---

### Post by jpittack on 2007-10-08
Here is what is up.  I think the fan just turns on to keep it all cool.  Scaling is fine for me.  CPU is fairly cool, everything else is hot.  Feel around and use the finger test.  I think the IGP, hard drive, and mabye RAM get hot.  Fan just keeps running.

Display: BIOS related.  I hear 1.7 works.  I use 2.6.1.  Why?  no real reason beyond I want the latest and Dell listed it as urgent.

Sound: I think system bell is app controlled.  I wouldn't turn it off though.  If something goes horribly wrong, don't you want to be freaked out and have your adrenaline pump?

Vista should be apart.  My vista is fine.  But I don't use it beyond e-mail and online radio until I get those in ubuntu.  Mabye I have never cause an error.

If anyone opened their 1501, could they let me know.  I want to know if a second fan is in there.

Try a post in the dell forum.  Mabye another 1501 user knows more.

---

### Post by jpittack on 2007-10-09
An added note.  I am using a laptop cooling fan from targus.  And the system fan still runs.

---

### Post by mivo on 2007-10-09
Assuming you didn't have the same problem in Feisty, turn off Tracker and see if there is an improvement.

---

### Post by tgm4883 on 2007-10-09
> **mivo said:**
> Assuming you didn't have the same problem in Feisty, turn off Tracker and see if there is an improvement.

Heh, I had forgotten about that.  Yea, turn tracker off.  I had the same problem in feisty, turned out to be beagle.

---

