---
title: "Login window partially displays, is scaled wrong"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by gnoel on 2009-01-04
This is a new, fresh install of 8.04 that I have configured and running well.  One last little problem is that only the top left portion of the login window displays on my ViewSonic CRT monitor.  I can't see the login name and password, though typing them in does enable me to log in.  I'm using the installed "human circle of ubuntu" image, and the same problem exists for other default images as well.

How can I get the login window to scale properly on my monitor?  Is this a screen resolution setting issue?  Once logged in, my desktop is at 1280 X 1024 and it looks great.  In case it matters, I'm using an old GEforce3 card with the nvidia driver.

Thanks!

---

### Post by gnoel on 2009-01-05
I'm wondering if (and how) this might be solved by tinkering with the GDM config file.  Anyone?

---

### Post by gnoel on 2009-01-06
Since literally dozens of you have viewed this thread and enjoyed my conversation with myself, I'd like to update my fans on the latest in my mini-drama of trying to get the greeter screen to display properly.

I decided to experiment with my xorg.conf file, and discovered that gdm uses the first screen resolution in the Modes list (of the Display Subsection of the Screen Section).  The first mode listed was 800x600@60, so that was the resolution I got.

I simply inserted another mode in the list in front of that one and experimented to find the best combination, in this case 1792x1344 for my ViewSonic 19" CRT.  Abracadabra: my Ubuntu "circle of friends" was finally there to greet me.

Since I have been providing all of you with hours of suspense and excitement these past few days, I will hold off marking this thread as solved until someone can explain 1) why it works this way, and 2) if there is any other way to control this (for example, in /etc/gdm/gdm.conf-custom?).

Thanks for your interest!

---

