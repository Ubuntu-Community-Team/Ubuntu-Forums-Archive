---
title: "Upgraded to 9.04 and now ubuntu wont start"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by thermobee on 2009-04-24
Hey guys,

I just upgraded to the new ubuntu and after the restart i get the loading screen and then it just turns black with some messed up graphics on the bottom third of the screen. I had this problem when i first installed ubuntu, but the difference is that it would load about half the time. This time ive tried about 10-15 times and it still hasnt loaded. I am not 100% sure but i think the problem before was the video card and the proprietery drivers. I have an ATI X850XT. No clue what to do since i cant get into the OS at all. Please advice.

Thank you

---

### Post by mwacky on 2009-04-24
Boot into the (Recovery Mode) single user mode and you should get to the shell, hopefully someone can tell you what to do there to fix your video issue.

---

### Post by tomdkat on 2009-04-24
> **thermobee said:**
> Hey guys,

I just upgraded to the new ubuntu and after the restart i get the loading screen and then it just turns black with some messed up graphics on the bottom third of the screen. I had this problem when i first installed ubuntu, but the difference is that it would load about half the time. This time ive tried about 10-15 times and it still hasnt loaded. I am not 100% sure but i think the problem before was the video card and the proprietery drivers. I have an ATI X850XT. No clue what to do since i cant get into the OS at all. Please advice.

Thank youI had this same problem even though I have a different ATI video adapter than you.  I ended up re-installing the xserver-xorg package and that worked for me.  You can read about my issue [here](http://ubuntuforums.org/showthread.php?t=1134841).

Peace...

---

### Post by thermobee on 2009-04-24
> **tomdkat said:**
> I had this same problem even though I have a different ATI video adapter than you.  I ended up re-installing the xserver-xorg package and that worked for me.  You can read about my issue [here](http://ubuntuforums.org/showthread.php?t=1134841).

Peace...

Thanks

---

### Post by thermobee on 2009-04-24
The reinstall of the xserver-xorg did not help me. What was the command to get the /etc/Xll/xorg.conf. file so i can adjust the display from there?

---

### Post by thermobee on 2009-04-24
bump

---

### Post by thermobee on 2009-04-24
Ok i figured it out, but it said that i cant open the file, so i need more help figuring out the problem. Please Help

---

### Post by thermobee on 2009-04-26
someone please give any advice

---

