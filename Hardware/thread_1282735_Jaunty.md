---
title: "Jaunty"
date: 2009-10-04
forum: Hardware
---

### Post by dyess002 on 2009-10-04
Guys I hope you can help me out. I have installed Ubuntu on a dv 7 and everything works but the sound and it works only on the right speaker. The headphone doesn't work. while it is pluged in the right speaker is on. This is the only thing holding me back from going all Ubuntu.

---

### Post by ermeyers on 2009-10-04
Nobody's answering you, so let me see ...  What's a dv 7?  May have a mono audio problem, but I haven't heard a mono problem on my machine, which is also 9.04.  How's your speakers and headphone plugged in?

---

### Post by falconindy on 2009-10-04
> **ermeyers said:**
> Nobody's answering you, so let me see ...  What's a dv 7?  May have a mono audio problem, but I haven't heard a mono problem on my machine, which is also 9.04.  How's your speakers and headphone plugged in?
dv7 is an HP laptop.

---

### Post by ermeyers on 2009-10-04
You have a left and right out of you laptop, so are you plugging your speakers and headphone is separately, or are they both connected somehow?

---

### Post by dyess002 on 2009-10-06
Sorry abou t the delay. This is a laptop and the 3 jacks are  Mike line in and to the right is headphone.

---

### Post by ermeyers on 2009-10-06
OK.  I take it that your L/R speakers are integrated into the dv 7 laptop, and you said that only the right speaker is active.  And when the headphone is plugged-in to the headphone jack, the headphone doesn't work and the right speaker is still active.  IS that a correct summary?  Did they work normally with Windows installed?

---

### Post by dyess002 on 2009-10-06
Thanks Ermeyers
Yes the headphon works great with Vista. But when I boot into Buntu the headphones are ignored and I only get sound from the right side.

---

### Post by ermeyers on 2009-10-06
There's a command called aumix that is very easy to use.  Applications->Sound & Video->aumix to open up a aumix terminal.  This shows L/R Balance:
```

aumix P++++++++O+++++++++++++++++<Vol            ++++++++++++O+++++++++++++
       ++++++++++++++++++++O+++++ Pcm            ++++++++++++O+++++++++++++
Quit  PO+++++++++++++++++++++++++ Line           ++++++++++++O+++++++++++++
Load  R++++++++++++++O+++++++++++ Mic  
Save  P++++++++++++++++O+++++++++ CD             ++++++++++++O+++++++++++++
Keys   O+++++++++++++++++++++++++ IGain          ++++++++++++O+++++++++++++
Mute  PO+++++++++++++++++++++++++ Line1          ++++++++++++O+++++++++++++
Only  P+++++++++++++++++++O++++++ PhoneIn
Undo  P++++++++++++++++++++O+++++ PhoneOut
      P+++++++++++++++++++++++++O Video
       0         Level        100                L        Balance         R

```

---

### Post by ermeyers on 2009-10-06
Typically, IN THE OLD DAYS, when you plugged in some headphones, it was a HARDWARE THING that disabled (bypassed) the speakers, while the headphones were plugged in.

PS: I can't stand Windows.

---

### Post by dyess002 on 2009-10-06
Ok all mine has is Vol,Pcm2,IGain and Digital. that is all that it shows.
I don't know how to put the picture in this post.
Thanks

---

### Post by ermeyers on 2009-10-06
> **dyess002 said:**
> I don't know how to put the picture in this post.

Press the # icon, to wrap CODE around the text, so you can keep its formatting.  Run xaumix, Edit->Select All, and Edit->Copy.  Then paste it into the CODE block.

How did the L/R Balance look?  Centered?

---

### Post by cogier on 2009-10-06
Is it not easier to left click on the speaker in the System Tray and select Volume Control?

I have been caught out by settings set so low that you can't hear anything.

---

### Post by dyess002 on 2009-10-07
I was using that method before our conversation and that way shows the headphone and shows it on high.  but the AUMIX doesn't show the headphone at all.

---

### Post by dyess002 on 2009-10-07
aumix  +++++++++++++++++++++++++O<Vol            
       +++++++++++++++++++++++++O Pcm2           ++++++++++++O+++++++++++++
Quit   +++++++++++++++++++++++++O IGain          ++++++++++++O+++++++++++++
Load   +++++++++++++++++++++++++O Digital1
Save   0         Level        100                L        Balance         R
Keys
Mute
Only
Undo


here is what mine looks like

---

### Post by apparle on 2009-10-07
See if everything is alright in 'alsamixer'

---

### Post by dyess002 on 2009-10-07
yes everything is ok    sound just don't come out through headphones

---

