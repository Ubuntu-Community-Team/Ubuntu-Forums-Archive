---
title: "Install drivers for Nvidia GTX 1050 Ti (Asus laptop)"
date: 2019-03-12
forum: Hardware
---

### Post by ViridisKnight on 2019-03-12
Hello guys!

I feel a bit defeated for having to ask for help here, but seems I can't solve this on my own :(

I've got a new laptop (Asus ROG GL703GE-GC199) and I've tried to install Ubuntu 18.04. Everything went fine, except I froze after login. So I found solution [here]("https://medium.com/@nitinpatel_20236/fixing-the-problems-installing-ubuntu-on-asus-rog-laptop-asus-gl503ge-5b6f497201b8") and it worked partially. I can now login using nouveau, but that's not proper solution. Btw, I updated kernel to 5.0, and regained functionality of Fn keys, which is cool.

Then I manually downloaded latest drivers from [nvidia website]("https://www.nvidia.com/Download/driverResults.aspx/142958/en-us") (418.43), but now when I get to login screen I get into infinite loop, just gets me back there immediately when I login.

Then I found very similar thread here on the forum: [https://ubuntuforums.org/showthread.php?t=2377560](https://ubuntuforums.org/showthread.php?t=2377560)

But again, it doesn't work. There is some improvement tho, now screen doesn't freeze immediately after clicking login. Now it loads desktop and freezes then :)

So I'd be very grateful if someone has an idea what can I attempt next?

EDIT: seems this freeze is now 'permanent', as I can't even log with nouveau.modeset=0, just freezes on desktop.[URL="https://ubuntuforums.org/showthread.php?t=2377560"]
[/URL]

---

### Post by ViridisKnight on 2019-03-12
Omg, it's a miracle, it works!

I re-installed the system and did the steps above and now it all works for some reason. Hopefuly permanently :)

EDIT: Sorry for bothering y'all.

---

### Post by Autodave on 2019-03-12
No bother at all.  Try to never use programs/drivers that are not in the official repositories: that only leads to problems.

Welcome to Ubuntu and the forums!

---

### Post by ViridisKnight on 2019-03-15
Duly noted :)

---

