---
title: "Entering password to terminal"
date: 2008-11-04
forum: General Help
---

### Post by Wakeupdead on 2008-11-04
alright guys, im a total noob to linux/ubuntu
i just bought a new harddrive and installed ubuntu onto it and im  going to use it like, always, as my main comp, anyway, im trying to install some stuff, and in the tutorial on the forum it sais to put some code into the terminal, so i do but then it comes up with enter my password, so i try to, but when i type nothing shows up in the terminal, i kno this is proboly some retardedly easy question but plz help

---

### Post by drs305 on 2008-11-04
That is a security feature. The password is being entered, you (and others) just cannot see it or even how long it is. Type it in and hit ENTER.

---

### Post by Wakeupdead on 2008-11-04
why couldnt they just make it show up as dots lol, would be so much easyer, anyhow, thx, i tanked you in the thread i guess thats like rep in these forums lol

---

### Post by drs305 on 2008-11-04
The thinking I suppose is that others can't even see the length of the password, which would make it harder to guess by onlookers. It does catch new users by surprise however.

Would you please mark this thread solved? It assists others looking for solutions and allows 'helpers' concentrate on unresolved issues. You do it from within the 'Thread Tools' link at the top right of the original post. (You can also return it to 'unsolved' from there.)

Welcome to the ubuntu forums. :-)

Just for grins:
I might as well add another newbie gotcha - the first time you try to update something via command line and it fails, you will get a message to run 'dpkg --configure -a'.  When you get that message, you will need to run it with 'sudo' in front of it:  sudo dpkg --configure -a

---

