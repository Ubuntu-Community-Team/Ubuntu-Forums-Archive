---
title: "bypass login"
date: 2008-08-06
forum: General Help
---

### Post by weweboom on 2008-08-06
I used a program to change my login screen, but i screwed it up and now after the boot screen, the screen turns orange, and the cursor just keeps spinning, without logging in. is there some way to bypass the login screen and just login so I can fix what I broke?

---

### Post by tamoneya on 2008-08-06
you can go into recovery mode.  When grub is loading (this occurs directly after the bios) hit escape.  Then select recovery.  This will load you into a root shell where you can reconfigure your login from.

---

### Post by weweboom on 2008-08-06
thanks, but I'm pretty new at ubuntu, could you please give me a step-by-step

---

### Post by Crafty Kisses on 2008-08-06
> **weweboom said:**
> thanks, but I'm pretty new at ubuntu, could you please give me a step-by-step

Right before you actually boot into Ubuntu the GRUB menu should list an option called "Recovery" boot into that, and there you go.

---

### Post by weweboom on 2008-08-06
thank you, i know that but how do you bypass login (not tty) and actually login to your computer using that?

---

### Post by Crafty Kisses on 2008-08-06
> **weweboom said:**
> thank you, i know that but how do you bypass login (not tty) and actually login to your computer using that?

You can log in through recovery mode (from GRUB) and type ```
cat /etc/passwd
```

This will give a list of all available users, you should be able to find your username in there somewhere. 

If you forgot your password, then you have a tad problem, you can always add a new user in recovery mode and add it to some of the admin groups.

---

### Post by weweboom on 2008-08-06
Thank you but it didn't work
after I put that in it showed a bunch of lines of code, as if I had installed something, and when i tried to login it still hung, but the screen was covered in black lines, is there someway to restore ubuntu to an earlier time maybe?

---

### Post by tamoneya on 2008-08-07
> **weweboom said:**
> Thank you but it didn't work
after I put that in it showed a bunch of lines of code, as if I had installed something, and when i tried to login it still hung, but the screen was covered in black lines, is there someway to restore ubuntu to an earlier time maybe?

Try this code:```
sudo dpkg-reconfigure ubuntu-desktop
```

---

