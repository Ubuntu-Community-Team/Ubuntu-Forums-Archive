---
title: "need help with a dual booting prblm, winxp/ubuntu"
date: 2008-09-17
forum: General Help
---

### Post by amdunca on 2008-09-17
recently I haven't been able to boot into windows XP, i can't think of any changes I've made to create this problem.  Im running grub, and whenever I select winXP it shows the windows splash screen with the loading bar, but then immediately cuts to a blue screen (not the typical BSOD) and then shuts off quickly (i cant even read what the blue screen says)

has anyone else had similar issues? if so, i would appreciate any assistance

---

### Post by caljohnsmith on 2008-09-17
If you can get that far in the Windows booting process, I don't think the problem would have anything to do with Grub. First I would run:
```
chkdsk /r
```
From the Windows Install CD. If that doesn't work, your best bet might be to do a "Windows repair" with your Windows Install CD. Let me know if you want details of how to do that.

---

### Post by amdunca on 2008-09-17
I dont have my install disk with me, i left it at home when I came up to college. i should be going home in the next couple weeks though

---

### Post by caljohnsmith on 2008-09-17
Since you don't have access to your Windows Install CD, one thing you could do is download the [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"); from that CD you could run the "chkdsk /r" command, because it should be compatible with your Windows XP installation (I don't think that command has even changed between Vista and XP, and if it has, I'm sure Microsoft would make it backwards compatible). That might be enough to get your Windows working again, and then you wouldn't have to wait a couple of weeks until you go home. :)

---

### Post by amdunca on 2008-09-17
problem solved, i had accidentally set my bios settings to default, but there was a value that needed to be set to something else, thank you for your help though!

---

### Post by amdunca on 2008-09-17
oh, and now your thank yous are up to 300! you earn +5 charisma!

---

