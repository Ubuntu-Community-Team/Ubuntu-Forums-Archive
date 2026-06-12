---
title: "Screen dims even though it is set to never dim"
date: 2009-01-10
forum: Hardware
---

### Post by Jerrac on 2009-01-10
My screen dims every 5-10 minutes even though it is set to never dim. I've checked an unchecked the "Dim display when idle" box in both tabs multiple times. 

I am using Ubuntu 8.10 on a Sony Vaio VGN FE-880E.

What can I do?

---

### Post by Jerrac on 2009-01-23
It's been a week since I posted...

Anyone have any ideas of what I could try? Or what other information I could post to help diagnose the problem? I have tried searching the forums, but couldn't find any topics that helped.

---

### Post by iggykoopa on 2009-01-24
I can't help you fix the issue but wanted to say it happens to me too. If I'm running most apps like totem it won't dim, but if I'm watching hulu in firefox or ogle it will. Same as you I uncheck anything in powermanagement that said to dim the screen.

---

### Post by Jerrac on 2009-01-24
With Hulu, it dims because ubuntu doesn't detect activity from flash. I assume at least...

That I could understand if I had set the screen to dim. But when I have set to never dim...

---

### Post by Jerrac on 2009-01-28
> **iggykoopa said:**
> I can't help you fix the issue but wanted to say it happens to me too. If I'm running most apps like totem it won't dim, but if I'm watching hulu in firefox or ogle it will. Same as you I uncheck anything in powermanagement that said to dim the screen.

What hardware are you using? Maybe that will help someone figure it out.

I created a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/321756") for this, since no one has helped us on these forums.

---

### Post by GandG on 2009-02-03
Assuming that there is no Monitor hardware setting which is kicking-in, it may well be that the Screensaver is set to Blank and the "Regard The Computer As Idle After" slider is set too aggressively.

The 'dimming' effect which occurs is similar to the one that Power Management function produces and the Screensaver also is definitely invoked when viewing the BBC IPlayer programmes which - being Flash-based - is probably much the same as Hulu?

---

### Post by Jerrac on 2009-02-03
Thank you! It was the screensaver! I hadn't even thought about checking that... :D

---

