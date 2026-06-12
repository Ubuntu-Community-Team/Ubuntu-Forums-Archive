---
title: "Power management broken"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by clarkey on 2007-06-04
At first power management ran perfectly on my Acer travelmate 3200 but I installed some update when it poped up in the top right hand corner about a week ago said something about linux kernel and the power management was suddenly broken ie it wouldnt recognise that the computer is a laptop and stopped showing battery related info and warnings. Also i am not completely sure if it was working beforehand but I think Hibernate function also broke at the same time now all it does is try to hibernate and then go back to the locked screen where you have to re enter your password. Oh and i forgot to mention I am running feisty

Thanks in advance


P.S As you probably guessed by now im a newbie so please be nice lol

---

### Post by clarkey on 2007-06-06
anyone have any ideas

---

### Post by twrock on 2007-08-24
No help from me, but I do have a similar problem. Dell 700m. Something went wrong a couple of weeks ago, and now there is no automatic shutdown or warning for a low battery state. Unless I'm watching carefully, the machine just turns off (not shutdown) instantly with no warning whatsoever. It's no fun. So if anyone can point us in some kind of direction, I'd appreciate it.

---

### Post by tagrat on 2007-08-25
same issues on my Aspire 3050 - just started happening

---

### Post by twrock on 2007-08-26
So, I had a little time yesterday and just decided to do the "ultimate fix": a fresh install. But, alas, it was no use. I will say that I regret not testing things before I installed all the updates (particularly the kernel update and a few others). It would be good to know if some update along the way broke something.

As I recall (a dangerous thing to rely on some times), when I first started using Feisty, I was able to set the time until Suspend (or other actions) to as low as six minutes. Now the lowest value is eleven minutes. So something must have changed somewhere along the line. Maybe that same something broke my power management.

For the record, my Dell 700m will no longer suspend, hibernate, or shutdown based on the power management settings. It will simply stay on until the battery reaches 8% and then just turn off instantly with a "click" noise (I think the sound is the hard drive).

I'm tempted to try another distro to see if it is a Ubuntu specific issue. I've got a few hours before bed time. It might be worth it. Any recommendations?

---

### Post by twrock on 2007-08-26
(deleted original post data)
Another weird thing I just noticed. The shortest time to activate a power saving mode was 11 minutes, ... until I went in and activated a screen saver. All of a sudden I could lower those times down to one minute more than whatever I had set the screensaver at. Maybe that's why I recall that the power saver settings were lower before.

---

### Post by twrock on 2007-08-29
Here is an active thread concerning some power management issues: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

