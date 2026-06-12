---
title: "[SOLVED] Problems with NVIDIA GeForce 7300GT on Feisty"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by JawsThemeSwimming428 on 2007-07-15
I recently did a clean install of Feisty on my PC that has a NVIDIA GeForce 7300GT 256MB DDR2 graphics card. The card displays the screen but it is slightly off center ( the trash icon in the bottom right and the Shutdown Icon on the top right are almost completely off the screen). I think I need to enable to restricted drivers and I tried doing this with the Restricted Drivers Manager. In the Drivers Manager there is an entry for the NVIDIA Accelerated Graphics Driver with shows it is not in use. I click to check the Enabled check box and then click Enable Driver in the Dialog box that pops up. It grays out the entry for 2 seconds and then it comes active again but the box is not checked and it still says not in use. I do not currently have Internet access on this machine because I am having an issue with the WUSB54Gv4 Linksys wireless adapter so my resources are limited. Anyone help would be greatly appreciated!!!!

---

### Post by w4ett on 2007-07-15
The question I have:   Have you tried adjusting your monitor's Horizontal and Vertical  display Position Control?

---

### Post by nwadams on 2007-07-15
i had that problem too, can't remember what i did to fix it, if anything, but that was using 6.06, things just seem to work now in 7.04

---

### Post by JawsThemeSwimming428 on 2007-07-15
w4ett,

How do I do that? Are you talking about adjusting something on the monitor menu itself or in Ubuntu? If you can, elaborate a little more because I want to try that! Thanks for the quick response!

---

### Post by nwadams on 2007-07-15
on the monitor itself

---

### Post by w4ett on 2007-07-15
> **nwadams said:**
> on the monitor itself

DITTO...on the monitor

---

### Post by JawsThemeSwimming428 on 2007-07-15
Thanks! I'll try that tonight when I get home...I'll let you know if that's all it was.

---

### Post by JawsThemeSwimming428 on 2007-07-15
Thanks for the solution, although now I have another slight issue. I have two PC's KVM'd together with a little iogear KVM. On the PC running Feisty I pushed the Auto button on my SyncMaster 172T 17" LCD monitor and it adjusted the screen properly so that it all was viewable. However, when I toggled back to my Windows XP Pro machine the screen was slightly off like the Feisty one was originally. If I push the Auto button again it adjusts the Windows machine correctly but not the Feisty one. Will I have to do this each time I toggle back and forth or is there a way to make them use the same setting?

---

### Post by w4ett on 2007-07-15
> **JawsThemeSwimming428 said:**
> Thanks for the solution, although now I have another slight issue. I have two PC's KVM'd together with a little iogear KVM. On the PC running Feisty I pushed the Auto button on my SyncMaster 172T 17" LCD monitor and it adjusted the screen properly so that it all was viewable. However, when I toggled back to my Windows XP Pro machine the screen was slightly off like the Feisty one was originally. If I push the Auto button again it adjusts the Windows machine correctly but not the Feisty one. Will I have to do this each time I toggle back and forth or is there a way to make them use the same setting?

I've read reports of this in the past.  It seems that Linux and the Xserver handle resolution and refresh rates a little less "Exactly" as MS Windows does.....The Horiz and Vert settings can be off by  .10-.20 %  (that's point 10%)...a small amount, but enough so you will notice the difference switching from MS to Ubuntu,

I see it myself in my setup, but since i boot into windows so rarely (once a month or so), I don't worry about it. :)

---

### Post by JawsThemeSwimming428 on 2007-07-16
OK well I am glad I am not the only one! But is there a workaround so that the resolutions are closer or more precise so I don't have to adjust each time? I still use Windows XP pretty frequently.

---

### Post by JawsThemeSwimming428 on 2007-07-17
I have been looking and I haven't found a definite solution yet. Anyone have any clue how to correct this issue? Or can you point me in the right direction?

---

### Post by w4ett on 2007-07-17
I can't think of any solution immediately....Why don't you mark this thread as SOLVED, and start a new one referencing the KVM Switch, 2 OS,  separate video input resolution problem....you might find someone  has a solution.

---

### Post by JawsThemeSwimming428 on 2007-07-17
OK, Thanks for everything!!

---

### Post by w4ett on 2007-07-17
No Problem...Good Luck!!

---

