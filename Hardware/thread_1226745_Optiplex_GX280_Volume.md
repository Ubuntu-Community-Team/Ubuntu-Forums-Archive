---
title: "Optiplex GX280 Volume"
date: 2009-07-29
forum: Hardware
---

### Post by Cajun_Lan_Man on 2009-07-29
Hello all. 

New Ubuntu user here. 

I just got my hands on a computer to dedicate to Ubuntu. It's running great so far. 

Dell Optiplex GX280
3GHz P4
2gigs RAM
Some ATI video card

I've got 2 questions if someone can help. 

1. This computer has an internal speaker mounted in the front.  It works, however I cannot control the volume with the controls in Ubuntu.  It only plays very loudly. 

2. Where to I go to find out what Ubuntu "thinks" my graphics card is? There are no drivers shown in the "restricted drivers" window.  But I must be running with some kind of driver, because it's handling the compiz cube and 3d windows with ease.

Thanks ahead of time for any help.

---

### Post by Cajun_Lan_Man on 2009-08-01
Bump

Anybody?

---

### Post by Prospero2006 on 2009-08-01
I've got a gx280 running Ubuntu in my classroom actually.

Sound:
Run alsamixer and see if you can't get the speaker to work that way.

Video:
```

lspci

```

It depends on whether you are using the onboard video or a video card.
Look for the words NVIDIA or ATI when you run that command.

If it's the integrated motherboard video, you won't get any acceleration.

I hope that helps,
Josh

---

