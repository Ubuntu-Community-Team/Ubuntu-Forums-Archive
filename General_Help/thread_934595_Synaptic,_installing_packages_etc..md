---
title: "Synaptic, installing packages etc."
date: 2008-09-30
forum: General Help
---

### Post by mkcarter on 2008-09-30
I'm kinda new to ubuntu, I hope this isn't too remedial...anyway, I tried to install some software that i downloaded, got halfway through the setup, the installation stalled on me so i closed it out. When I tried to run the install again it said that I had to close another synaptic package before continuing. and when i try to open the synaptics package manager i get this message:


"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
"

how do i close the other open package or whatever?

---

### Post by oldos2er on 2008-09-30
Run "sudo dpkg --configure -a" in a terminal.

---

### Post by mkcarter on 2008-09-30
well i did that, but I cant figure out what i need to do from there

---

### Post by karlr42 on 2008-09-30
Have you tried opening Synaptics since?

---

### Post by mkcarter on 2008-09-30
actually it worrkked this time...go figure. thanks!

---

### Post by oldos2er on 2008-10-01
> **mkcarter said:**
> well i did that, but I cant figure out what i need to do from there

 If the command ran with no further output, you should be good to go.

---

