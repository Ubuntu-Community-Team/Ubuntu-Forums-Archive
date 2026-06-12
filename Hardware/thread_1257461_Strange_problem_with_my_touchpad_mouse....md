---
title: "Strange problem with my touchpad mouse..."
date: 2009-09-03
forum: Hardware
---

### Post by eddhead on 2009-09-03
(Hey everybody!)

I recently switched my Dell Latitude C640 from Windows XP to Ubuntu. Overall, I am absolutely loving it and can't believe I didn't switch earlier. Now for my problem. Every time I have booted Ubuntu, my cursor acts as if it is getting sucked into the top-right corner of my screen. What I mean is the cursor starts in the corner as soon as Ubuntu boots. Then, whenever I try to move it via touchpad mouse, it moves a bit before getting "sucked" back into the corner. I've also tried plugging in my USB mouse and having the exact same problem. But here's where it gets strange.

When I plug in a "traditional" mouse (i.e. one that plugs into the keyboard/mouse port in the back of the laptop) IT works just fine. Then, when I unplug it, the touchpad mouse works perfectly fine. I should also mention that at this point, the "touchpad mouse" tab in the "mouse preferences" window just isn't there at all. It's there BEFORE I plug the "traditional" mouse in. So what I'm assuming is that after plugging in the "traditional" mouse, it thinks that the touchpad is also a traditional.

So, ultimately, my question is, why doesn't the touchpad work in the first place? (Thanks for your help!!)

---

### Post by earthpigg on 2009-09-03
easiest way to find out if it is a hardware or software issue:

boot from an Ubuntu Live CD and see if the problem persists.

if the problem persists, it is probably a hardware problem.

if the problem goes away when in the Live CD, then it is a software problem.

---

### Post by eddhead on 2009-09-03
Yeah, I tried running the Live CD and it did the same thing. Which is weird, because it worked just fine with before the switch. Whatever, I guess I'll be looking for a nice "traditional" mouse on ebay tonight!

Thanks for the help, earthpigg!! (can't believe I didn't think to try that myself)

---

### Post by earthpigg on 2009-09-03
to super-duper-5000%-absolutely rule out the possibility of it being a software issue before you could try some other distributions.... BSD, other linux distros, Windows LiveCD (o wait...), etc.

buuuuut its probably easier just to buy a mouse, yes.

or modify your xorg.conf to disable your touchpad.

---

