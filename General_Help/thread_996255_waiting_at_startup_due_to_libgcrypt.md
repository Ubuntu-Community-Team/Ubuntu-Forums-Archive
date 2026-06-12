---
title: "waiting at startup due to libgcrypt"
date: 2008-11-28
forum: General Help
---

### Post by ecinar on 2008-11-28
Hi all,

I have recently upgraded my Ubuntu to 8.10 and realized that at startup when the Ubuntu logo comes, it gets stuck for a while and waits a bit long time. When I press alt+f1, I observed that it waits when the system performs this step: 
[I]
resume: libgcrypt version: 1.4.1 [/I]

can I make the system skip this step for me ? Is this a really important thing for the system ? This makes my ubuntu to startup in a longer time. 

Thanks for your help and ideas

Eyup

---

### Post by jperelli on 2010-05-19
I have the same issue...

Somebody knows something about this?

What is libgcrypt for? Can I just uninstall it?

---

### Post by Mr_Leo on 2010-06-02
I have a similar problem with the boot process hanging before the ubuntu splash screen with the message "resume: libgcrypt version 1.4.x". After 10- 15 sec., the splash screen comes up and system boots smoothly to login and otherwise works fine.

---

### Post by alainpannetier on 2010-06-04
Hi all,

I've noticed this message as well since I upgraded to Lucid Lynx.
The "resume" keyword and a little bit of  googling around enabled me to discover that the message 
[B][FONT=Courier New][SIZE=2]"resume: libgcrypt version xxxx" 
[/SIZE][/FONT][/B]comes from the uswsusp package (s2ram/s2disk).

I could trace the source to [FONT=Courier New]**resume.c**[/FONT] version 1.27 (line 714). 
Please see the source on sourceforge corresponding [CVS source code]("http://suspend.cvs.sourceforge.net/viewvc/suspend/suspend/resume.c?revision=1.27&view=markup").

So I uninstalled uswsusp but the only result was that the message was not shown anymore.  My startup took as long as before however, with the disk still spinning a lot.
I suspect the "resume: libgcrypt version" is only the last thing that make it to the screen before the startup really gets into full swing. Not the real culprit then.
As for me I've got so many things starting up on that machine (oracle 11gR2, mysql 6, plenty of Java servers...) that what I really need is a "boot profiler" to find out how long each step takes....

I also checked that hibernate/resume still work. They do.

---

### Post by Stifflers_mom on 2010-12-04
no solution for that? 
I have the same issue with Lucid. I think also, the message is there, since i installed uswsusp. Uninstalling uswsusp didn't change anything.
Is there any chance to get rid of this than a new install of Ubuntu?

---

### Post by Stifflers_mom on 2010-12-06
push...

---

