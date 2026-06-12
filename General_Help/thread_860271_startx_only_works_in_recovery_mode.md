---
title: "startx only works in recovery mode"
date: 2008-07-15
forum: General Help
---

### Post by noarc on 2008-07-15
GUI hardy graphical install gave me a blank screen. I installed with the alternate install disk. 

Now, when I boot using the normal (first) grub entry to Ubuntu, it also gives me a blank screen (after showing the Ubuntu loading screen, when it should go into X). However, if I boot using the recovery option, and go into the terminal prompt and type `startx', then it displays gnome fine (high resolution, full colors) and I'm typing this note from there. 

Can anyone help diagnose the problem? I'm thinking it's not display drivers, but some other weird error.

---

### Post by overdrank on 2008-07-15
> **noarc said:**
> GUI hardy graphical install gave me a blank screen. I installed with the alternate install disk. 

Now, when I boot using the normal (first) grub entry to Ubuntu, it also gives me a blank screen (after showing the Ubuntu loading screen, when it should go into X). However, if I boot using the recovery option, and go into the terminal prompt and type `startx', then it displays gnome fine (high resolution, full colors) and I'm typing this note from there. 

Can anyone help diagnose the problem? I'm thinking it's not display drivers, but some other weird error.

HI and could you give us some system specs like graphics card, memory?

---

### Post by noarc on 2008-07-15
it's an intel 965 on-board graphic chip and 1 gb of ram; the 1 gb of ram is low, but gnome should still work with that, right? and since startx works fine from the root terminal of the recovery mode, then it seems my graphic chip is supported. can i post anything else that would help?

---

### Post by overdrank on 2008-07-15
> **noarc said:**
> it's an intel 965 on-board graphic chip and 1 gb of ram

Hi and yes that does seem weird. The intel graphics are usually pretty good with ubuntu and you have enough memory it should have enough shared with it. Did you check the cd for errors before install and also check and verify the ISO before burning.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by noarc on 2008-07-15
Yes, I checked both ISOs (regular and alternate) for errors and both passed all checks.

Can I pass a command to grub to boot into a console (but using the regular kernel otherwise)? I tried doing CTRL+ALT+F* at the blank screen but that wasn't responding either. What are the differences between the recovery mode and the regular kernel that might cause one to work and not the other?

I really need this to work!

---

