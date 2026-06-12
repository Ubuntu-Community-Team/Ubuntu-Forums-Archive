---
title: "some issue with root"
date: 2008-10-17
forum: General Help
---

### Post by qbektrix on 2008-10-17
Hi,
First off, i am a new user to linux and Ubuntu is my first. Today is my first day. All my life i have used win 2k & win xp. I am a poweruser. So the urge to mess around is high.
I ran "apt-get update" in the terminal and the whole thing went fine. I closed the terminal and tried "apt-get install openvpn" and i got an error message. I tried "apt-get update" once again and i got the same error message.

The error message:
[I]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

Any clue what went wrong?
Thanks

---

### Post by Ryadt on 2008-10-17
Use sudo before apt-get```
 sudo apt-get update
```

---

### Post by llebegue on 2008-10-17
Only one program is allowed to deal with package management at a time. Make sure you don't have a synaptic running ...

---

### Post by qbektrix on 2008-10-17
Thanks Ryadt. SUDO was the problem.
llebegue, i shall keep you advice for the next screw up.
Thanks alot.

---

