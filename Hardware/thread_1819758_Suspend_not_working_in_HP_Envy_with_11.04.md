---
title: "Suspend not working in HP Envy with 11.04"
date: 2011-08-06
forum: Hardware
---

### Post by nubela on 2011-08-06
So I tried a suspend, the system goes out to the login screen, and when I try to login, it says that the Power Management is irresponsive. I am given the option to force close it, of which I did. Then the system suspends to ram. Trying to turn it back on leads to a black screen which can only be resolved by hard rebooting it.

Does anyone have an idea how I can fix this? Thanks!

---

### Post by 3602 on 2011-08-06
You cannot.
It's a BIOS fault.
Even if you upgrade to the newest BIOS, that is by installing Windows and running Insyde H2O, the newest one still doesn't support suspend (nor hibernate).

---

### Post by nubela on 2011-08-06
Are you serious? Do you have certain citations? I googled and apparently it did work in 10.10.

---

### Post by 3602 on 2011-08-06
My citation is me.

---

### Post by 3602 on 2011-08-06
Is what I did anyway. BIOS shipped was F.14, installed XP, ran Insyde H2O, upgraded to F.27. Still cannot suspend nor hibernate. My problem is even worse than yours as a hard reboot will *not* bring it out. Only by removing all operating power sources (DC adapter and battery) can it be brought back.

---

### Post by nubela on 2011-08-07
sorry, but thats not the most helpful reply. anyone else could help?

---

### Post by eric3938 on 2011-08-07
> **3602 said:**
> Is what I did anyway. BIOS shipped was F.14, installed XP, ran Insyde H2O, upgraded to F.27. Still cannot suspend nor hibernate. My problem is even worse than yours as a hard reboot will *not* bring it out. Only by removing all operating power sources (DC adapter and battery) can it be brought back.

I've had this same problem since I first installed Ubuntu on my HP Pavilion laptop over a year ago. I've researched many times looking for a solution (actually why I was here) and it seems nobody has yet found a fix.

Ubuntu 10.04.3

---

### Post by 3602 on 2011-08-07
> **nubela said:**
> sorry, but thats not the most helpful reply. anyone else could help?
lulz? Last time I checked the most current BIOS was F.27. Buhlieve me I also saw the "update your BIOS and receive suspend functions!" on the Interwebs, but after I did update (to F.27) it still doesn't work. What does that mean? That means whatever they're saying might indeed be valid, but it would be a BIOS somewhere between F.14 and F.27. And where to find those? Contact HP. Either that or welcome to Linux.

---

### Post by OpenSage on 2011-09-21
> **nubela said:**
> So I tried a suspend, the system goes out to the login screen, and when I try to login, it says that the Power Management is irresponsive. I am given the option to force close it, of which I did. Then the system suspends to ram. Trying to turn it back on leads to a black screen which can only be resolved by hard rebooting it.

Does anyone have an idea how I can fix this? Thanks!





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---

