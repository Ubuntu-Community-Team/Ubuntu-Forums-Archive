---
title: "Loud Squealing Noise"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by gerowen on 2007-11-06
I just recently bought myself a brand spanky new Toshiba laptop, and proceeded to install the latest version of Ubuntu since I've been out of the computer scene for a little while. I'm impressed, it picked up everything right off the bat, including my wireless card, even though it's not showing up, it's closer than any linux distro has ever gotten. ANYWAY, I just got orders to Fort Lewis, WA, and I was to drive. So I packed up my ACUs and put my laptop in the passenger side floorboard of my car and took off. My laptop operated fine before the trip. Upon stopping at the end of my first day of driving I pulled my laptop out to listen to some good old Ozzy, and the left speaker made a loud squealing noise. The computer operates fine, and sound comes from the right speaker just fine. However the left speaker squeals really loud, and if I try to adjust the volume at all, I lose all sound until I restart the computer. Can anybody help me out with this issue? I was thinking maybe a blown speaker since it was sitting next to the speaker in the passenger side door, and I turn the music up pretty loud while I'm driving. Could the vibrations of the car speaker have blown the speaker in my laptop next to it?

---

### Post by z0phi3l on 2007-11-06
Reinstall Windows and send it in for repairs :)

---

### Post by mbradlcu on 2007-11-07
Hi,
couple questions,
does the squealing start right away, ie as soon as you log in?
what happens if you run:
```
 sudo /etc/init.d/alsa-utils
```
I'm not sure it it's installed by default but you may want to check out:
```
alsamixer
```
there's a bunchO setttings that you can tweak, maybe see if you're getting a feedback look with the recording source.

If you'd like to try the shotgun approach you may want to create a new user, log in with the account and see if you still have the issue.

good luck!

---

### Post by weblordpepe on 2007-11-07
> **marcusdean.adams said:**
> I just recently bought myself a brand spanky new Toshiba laptop, and proceeded to install the latest version of Ubuntu since I've been out of the computer scene for a little while. I'm impressed, it picked up everything right off the bat, including my wireless card, even though it's not showing up, it's closer than any linux distro has ever gotten. ANYWAY, I just got orders to Fort Lewis, WA, and I was to drive. So I packed up my ACUs and put my laptop in the passenger side floorboard of my car and took off. My laptop operated fine before the trip. Upon stopping at the end of my first day of driving I pulled my laptop out to listen to some good old Ozzy, and the left speaker made a loud squealing noise. The computer operates fine, and sound comes from the right speaker just fine. However the left speaker squeals really loud, and if I try to adjust the volume at all, I lose all sound until I restart the computer. Can anybody help me out with this issue? I was thinking maybe a blown speaker since it was sitting next to the speaker in the passenger side door, and I turn the music up pretty loud while I'm driving. Could the vibrations of the car speaker have blown the speaker in my laptop next to it?

I don't mean to be rude here (ok maybe just a little) but you should not put a laptop on the floor of your car and drive. Your laptop is most probably broken/damaged. It smells like a hardware problem rather than a software problem.

In fact I'm amazed the thing even boots. Your hard drive & DVD must be in a bad state.

---

### Post by Rhubarb on 2007-11-07
There's a good chance it's a hardware problem.
But, just to make sure, put in the ubuntu live cd and check if it still makes the bad noises.

---

### Post by gerowen on 2007-11-07
There was nothing else in the floor with it, so I didn't think there would be any issue.  And yes, the noise is still produced if I boot from the LiveCD.  One reason I thought maybe it was software though is because it does it even with headphones in.

---

### Post by weblordpepe on 2007-11-07
Does the noise occur when Ubuntu starts? Or does the noise start as soon as you hit the power. 

When exactly does the noise start?

Maybe try booting to Windows to see if you still get the noise.

---

### Post by gerowen on 2007-11-07
When Ubuntu starts, and only when it tries to produce sound.  It's not a constant noise.

---

### Post by weblordpepe on 2007-11-07
was it working fine before you put the laptop in the car? damnit my cat keeps drooling.

---

### Post by gerowen on 2007-11-07
Yes it worked fine before I put it in the car.

---

### Post by mbradlcu on 2007-11-07
this to me sounds like regenerative feedback. if you haven't already tried my suggestion of using alsamixer and looking at all the slider settings (gnome-mixer doesn't show a fraction of what alsamixer does) I would look into it.. + maybe try another live distro,, smothing small like dsl-not it's around 60megs.
good luck!

---

