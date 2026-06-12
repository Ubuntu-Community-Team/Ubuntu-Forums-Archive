---
title: "Can't update Ubuntu Hardy"
date: 2008-11-15
forum: General Help
---

### Post by dkev on 2008-11-15
When I try to update I get this error
 The method driver /usr/lib/apt/methods/HTTP could not be found.
I've tried installing different apts, but no luck. I don't have any problem downloading software from the repositories and I have tried multiple servers. I'm pretty new at this but I am learning. Any help would be appreciated.

---

### Post by SunnyRabbiera on 2008-11-15
open up a terminal and copy and paste this command:
sudo apt-get update

Lets start there.
Are you using add/remove by the way?

---

### Post by dkev on 2008-11-15
That error was copied directly from the terminal using the sudo update command.
I can download software both from the add/remove and synaptic.

---

### Post by SunnyRabbiera on 2008-11-15
alright, did you try a restart?
Sometimes apt hangs in the background and makes a mess, and sometimes a restart works.

---

### Post by dkev on 2008-11-15
Actually, I just tried updating my programs list from the add/remove (it told me the list was out of date) and I got the same error. Ive rebooted several times.

---

### Post by SunnyRabbiera on 2008-11-15
> **dkev said:**
> Actually, I just tried updating my programs list from the add/remove (it told me the list was out of date) and I got the same error. Ive rebooted several times.

Hmm, did you try sudo dpkg --configure -a

I will try to throw commands at you and see if I can at least get you started.

---

