---
title: "Workable graphics configuration for R9 270"
date: 2016-12-18
forum: Hardware
---

### Post by tomgibson on 2016-12-18
Does anyone know of a workable graphics driver solution for Kubuntu (either 14.04 or 16.04) or KDE Neon for an AMD R9 270?

I have tried fglrx on 14.04 but after install the desktop is unusable as there is terrible screen tearing and low fps (I mean 2 or 3 fps). On 16.04 obviously fglrx is not supported but I can't get decent 3d performance and avoiding screen tearing is also not easy. Features like Displayport MST don't work on the open source driver either.

What setups are people using with Kubuntu and similar cards?

At the moment I'm so fed up of trying different things that I can't get to work, or reading about solutions that no longer exist (e.g. PPAs that aren't supported anymore) I'm just going to have to give up and use Windows.

Thanks.

---

### Post by mastablasta on 2016-12-19
Use Windows instead.

14.04.1 with fglrx should work.

---

### Post by mörgæs on 2016-12-19
The development at AMD's is going fast these days. Have you tried 16.10?

---

### Post by tomgibson on 2016-12-19
> **mastablasta said:**
> 14.04.1 with fglrx should work.

Thanks, I installed 14.04.4, shouldn't this supersede 14.04.1 or is there some sort of breaking change?

---

### Post by tomgibson on 2016-12-19
> **mörgæs said:**
> The development at AMD's is going fast these days. Have you tried 16.10?

Thanks for the suggestion, I usually stick to LTS releases because I prefer not to do the major upgrade every six months, however given the issues with both other versions I'll give this a go as if it works it will be worth the minor inconvenience of six-monthly updates!

---

### Post by mastablasta on 2016-12-20
> **tomgibson said:**
> Thanks, I installed 14.04.4, shouldn't this supersede 14.04.1 or is there some sort of breaking change?

14.04.4 has newer kernel along with xserver and a bunch of other GPU driver related stuff that no longer supports the fglrx.

16.10 would use the opensource AMD driver. upgrading to 17.04, 17.10 and finally to 18.04 LTS should not really be an issue with those. things can only be better. so if 14.04 or 14.04.1 do not work but 16.10 works then this would be a good option to take.

---

