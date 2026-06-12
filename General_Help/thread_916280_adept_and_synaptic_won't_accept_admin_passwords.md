---
title: "adept and synaptic won't accept admin passwords"
date: 2008-09-10
forum: General Help
---

### Post by ticthak@AOL.com on 2008-09-10
I'm running  Gutsy, Hardy, and Mandriva in different partitions with varying amounts of (of course self-induced) aggravation and breakage; one thing that really mystifies me is that Synaptic and Adept from the Gutsy install won't accept any pw anymore (not root, user, or any of the old ones from previous installs and recoveries)- I can sudo in on the terminal OK, but how could those permissions change without some really major badness on the side occurring? Any ideas? I'm interested more from design/theory approach.

---

### Post by pytheas22 on 2008-09-10
What happens if you try to start Synaptic from the command-line by typing:
```

sudo synaptic
```

Also, do other graphical utilities that require you to enter a password (the System>Network setup program, for example) accept the password that you give them?

I'm thinking that perhaps the issue is with gksudo (the graphical version of sudo), and the results of the above tests would help to figure that out.

---

### Post by ticthak@AOL.com on 2008-09-11
yep, sudo synaptic works, other admin stuff, so following your hint here about gksudo (I've run into some odd issues w/kdesu, but I think these are unrelated)- just ran gksudo from the CLI and noticed that neither option for pw or passthrough was checked, checked the pw box and it seems to work fine now. Would this setting have been wiped by an update maybe? Honestly, since I started back with Linux this time, I've actually done more coding in the past year than in the past 17 years...this old fart may learn some new tricks yet...I  just tried adept again from the System menu and it works fine, I'll mark this as SOLVED!! with many thanks.

---

### Post by pytheas22 on 2008-09-11
I'm glad you figured it out.  I don't know what might have changed the gksudo settings, but I'd put my money on a bad update.

---

