---
title: "Java issue with 9.10"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by Eric B on 2009-09-16
I upgraded to 9.10 a little early, and now I cannot access a java app. I see 5 is not working in the repositories. I tried manually installing that to see if it fixes my issues using the instructions at Sun, and I installed to the /usr/lib/jvm/ directory. However, update-java-alternatives -l does not list it. 

Anyone know how I can get 5 up and running on 9.10, as I believe that the app will not run on 6?

---

### Post by Mighty_Joe on 2009-09-17
> **Eric B said:**
> I believe that the app will not run on 6?

Did you try running your app with Java 1.6?  Java's pretty good about being backwards-compatible.

---

### Post by Eric B on 2009-09-17
It doesn't even open using 6. I think it specifically looks for 5. I once had to edit the pluginreg.dat for Mozilla to specifically say that 5 was there, but if I do that now, the file is overwritten every time I start Firefox.

---

### Post by Eric B on 2009-09-17
Got it to work. The way the app was written, it was looking specifically for update 13. I basically lied to it by editing the pluginreg.dat user ~/.mozilla

---

