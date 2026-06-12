---
title: "[SOLVED] WTF?!  Malicious Code in Ubuntu?!"
date: 2008-07-24
forum: General Help
---

### Post by lupinesoul on 2008-07-24
Okay, if you read the thread a few threads below, you'd know that I've been downloading media players like mad, trying to get an avi file to work(it turned out to be a fake).  I just noticed a few minutes ago that my Firefox Google Bar and Address bar are totally screwed up.  I think it might be a virus or some malicious code(never thought I'd say that with ubuntu).

[IMG]http://i39.photobucket.com/albums/e160/lupinesoul/Screenshot-1.png[/IMG]

Edit: BTW, had to use Opera to upload the image.  It's just not my thing...

---

### Post by lupinesoul on 2008-07-24
Anyone have any insight?  Please?

---

### Post by bodhi.zazen on 2008-07-24
Browsers can be hacked / cracked regardless of base OS.

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by lupinesoul on 2008-07-24
Thank you.  Umm... should I try to avoid logging in anywhere?

---

### Post by aysiu on 2008-07-24
Have you tried safe mode? I think you can reach it by closing Firefox and using the command ```
firefox -safe-mode
``` If that works, you could just have a corrupt Firefox profile.

---

### Post by bodhi.zazen on 2008-07-24
I am no expert, but I can not tell from the information you posted exactly what the problem is or your concerns. It could be a simple glitch in your profile. I do not think you have been affected by any kind of virus or malware.

I would just delete your firefox profile and create a new one.

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by gunashekar on 2008-07-24
If any suggestion given here solves your problem please mark the thread SOLVED. May I also recommend a little more care while making a title for your thread / support question.

---

### Post by eragon100 on 2008-07-24
Nice fonts, where did you get those? :wink:

---

### Post by ByteJuggler on 2008-07-24
An assertion failure is a software error, usually.  The rest of the info is basically the call stack at the point where it happened.  An assertion failure indicates some internal validation rule was found to be broken, possibly implying some problem in the program.  It can occassionally be caused by bad data (but then, the software should ideally be modified to not choke on said bad data.)  I highly doubt it's any type of malware/virus or anything like that.

---

### Post by lupinesoul on 2008-07-24
> **eragon100 said:**
> Nice fonts, where did you get those? :wink:

They came with the system.  It's called Open System...  You're the second person to ask that. xD

---

### Post by lupinesoul on 2008-07-24
> **aysiu said:**
> Have you tried safe mode? I think you can reach it by closing Firefox and using the command ```
firefox -safe-mode
``` If that works, you could just have a corrupt Firefox profile.

If I could hug you, I would!... Is there a hug command for use in the Terminal?:biggrin:

---

### Post by gunashekar on 2008-07-24
> **eragon100 said:**
> Nice fonts, where did you get those? :wink:

The font appears to be Comic Sans ( a microsoft font)

---

### Post by ByteJuggler on 2008-07-25
> **lupinesoul said:**
> If I could hug you, I would!... Is there a hug command for use in the Terminal?:biggrin:

No, but try:

```
banner *hug*
```

Make sure your terminal is maximized (or at least about 130 columns wide)  :)

---

