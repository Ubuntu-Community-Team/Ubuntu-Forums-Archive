---
title: "X server seems to be failing"
date: 2008-07-02
forum: Hardware
---

### Post by toddpedlar on 2008-07-02
After moving my PC (running Feisty Fawn) from one office to another, and after one successful boot (almost - the ethernet had issues, so I rebooted) I have yet to be able to get the computer up and running properly.

The symptom is this:  upon reboot, the Ubuntu screen comes up, then the NVIDIA logo appears - then nothing.  Then a flash to the standard brown background, then the NVIDIA logo again - then nothing.  This cycle repeats 6 times, and then I get a complaint that things can't start up and I shouldn't do anything for 2 minutes on display :0.  

So... does this sound familiar, and what in the world could have happened?  The move was uneventful - no bumps to the case of the computer, no nothing.  This is a 1 year old machine which has worked swimmingly since I bought it last summer.

---

### Post by phidia on 2008-07-02
I guess I would check the /var/log/xorg files or even dmesg from CLI (you can open commandline by pressing Ctrl+Alt+F1) (F1 thru F7) maybe there is something there to work with?
Also you can edit your /etc/X11/xorg.conf 
Replace the "nvidia" driver with "nv" or "vesa" and see what happens.

---

