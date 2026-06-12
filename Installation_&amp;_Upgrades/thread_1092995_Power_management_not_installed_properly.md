---
title: "Power management not installed properly"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by imparja2 on 2009-03-11
I have ubuntu hardy heron 8.04 I was in the middle of updating my computer when it crashed. So now I find I can't launch any of the applications I was updating because they're not installed properly. I've found sbackup in my c:/ but it won't open. My computer says Powermanagement isn't installed properly and I should contact the administrator. There's also usually many icons in the time bar but now there's only the sound and time  any step by step advice I'm a real beginner?

---

### Post by Partyboi2 on 2009-03-11
Press Ctrl+Alt+F2 when you are at the desktop or login screen to get to a terminal and see if you can continue the upgrade by typing
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by imparja2 on 2009-03-11
oh that was easy cheers

---

