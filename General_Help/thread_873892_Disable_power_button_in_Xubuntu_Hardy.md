---
title: "Disable power button in Xubuntu Hardy?"
date: 2008-07-29
forum: General Help
---

### Post by imotlaw on 2008-07-29
Hi all. I have a kid who likes to push buttons, and so I had previously set up my installation of Xubuntu (feisty) to not do anything when the power button was pushed (I did this by commenting out a line in /etc/acpi/powerbtn.sh). I just upgraded to hardy, and all of a sudden whenever my kid pushes the power button, I get the "power down" option box (switch user, log out, restart, shut down, suspend, hibernate). I found (from reading the threads) that Xubuntu is now using gnome-power-management. I tried to disable the part in powerbtn.sh that appeared to cede control to gpm, but that didn't work. Then I actually moved powerbtn.sh to another file, and that still didn't work. Somehow gpm is now the only thing catching the power button signal, and I have no idea how to stop it from getting the signal.

Now, from my reading of past threads, it appears that older versions of ubuntu with gpm had an option (under the gnome-power-management preferences gui) to set gpm to do nothing when the power button was pushed. This option is inexplicably absent in my version; that is, under Applications->Settings->Power Management->"General" Tab->"when the power button is pressed", I have only the options "Ask Me", "Suspend", "Hibernate", and "Shut Down". 

Does anyone have any suggestions? Or can anyone confirm that this is a bug with the gpm gui? Or a bug with Xubuntu's use of the gpm gui? Or anything?

Help!

---

### Post by aomlives on 2008-07-31
I can confirm that I have the same four options when I go to Power Management in my Xubuntu. Did a quick Google search and this thread came up first :). I guess that doesn't mean any good regarding a solution to your problem...

Good luck anyway

---

### Post by geirha on 2008-07-31
I guess it's a bug with the GUI. You can still change the value to nothing though. Hit Alt+F2 and run "gconf-editor". Browse to apps -> gnome-power-manager -> buttons and change the "power" value to "nothing"

---

### Post by aomlives on 2008-07-31
I had to install gconf-editor first in Xubuntu, but then it worked!

 I didn't really need this option (I don't have children :D) but good to know anyway.

Cheers

---

### Post by imotlaw on 2008-07-31
Thanks, geirha! This is exactly what I needed.

---

### Post by joshzam on 2010-04-12
Thank you, geirha!!!

Also, in case anyone was curious, there is no similar option for the Reset button (I've tried). This button is like God, trumping all OS or even BIOS settings. The only way to disable the Reset button is by physically unplugging it from the motherboard.

---

