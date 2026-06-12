---
title: "pass word blocking me."
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by tenderfootW on 2009-05-17
I just installed ubuntu and everything seemed to be going well.  Upon reboot, pass word screen came up but would not accept my password, where it had done so earlier.  I couldn't rectify the situation by trying variations of the password.  
I tried re-installing, but again, when the pass word screen came up, it would not accept my password.
What do I need to do to get back into the os?

Wade

---

### Post by cariboo on 2009-05-17
Start in recovery mode, when you gedt to the menu choose drop to root prompt. At the prompt type:

```
passwd <username>
```

where <username> is your user name. The above command will allow you to create a new password. Once you have created a new password, type exit at the prompt, then select resume to continue on to your desktop.

---

### Post by Peter09 on 2009-05-17
Remember that the password is case sensitive -Capitals and Lowercase matter.

---

