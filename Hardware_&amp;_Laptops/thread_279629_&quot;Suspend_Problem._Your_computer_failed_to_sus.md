---
title: "&quot;Suspend Problem. Your computer failed to suspend.&quot;"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-10-18
I left my laptop in suspend mode (or so I though) for the night, with its lid closed.

This morning when I opened the lid, I was greeted with the unlock screen (as expected), but when proceeded to the desktop, I got a short message at the bottom-right of the screen:
> 
"**Suspend Problem. Your computer failed to suspend.**"

Check the [FAQ page]("http://www.gnome.org/projects/gnome-power-manager/faq.html") for common problems.

Well, I saw it, but I have no clue which one of those frequently questions pertain to my case. ](*,) 

Is there a log file where I can find the actual messages described in that FAQ? How do I start researching for the cause of the problem?

Thanks!
Alex

---

### Post by xyz on 2006-10-18
Hi,

As an alternative, check my sig for Suspend/Hibernate Laptops...it worked great for me. Let us know if it does the trick for you. Good luck.

---

### Post by xp_newbie on 2006-10-19
XYZ, thanks for providing this resource. I will read it and see what can be applied to my case. At the moment, I am mostly interested to know whether there is a log file that logs (and possibly details) all those "Your computer failed to suspend" events. I hope that I can find that piece of information in your impressive article.

Thanks,
Alex

---

### Post by xyz on 2006-10-19
Just to make one thingy clear: it's not MY article!!lol
Good luck !

---

### Post by xp_newbie on 2006-10-27
OK - I finally got to read this great article, but unfortunately I couldn't derive from it the help I need to troubleshoot and solve my problem.

You see, all the scripts and mechanisms are already implemented and in place by Ubuntu 6.0.6. I only need to know where this error message I am getting goes to in the **log file**, so that I can make better sense of what I read in the FAQ to which that error message is referring.

Any idea where to find those detailed lines relating to ACPI and suspend?

Thanks,
Alex

---

### Post by levis501 on 2006-11-06
I'm experiencing this problem, too, and have found that adding the command line argument --verbose to gnome-power-manager gave lots of log messages.  If this doesn't help (I don't expect it will, but maybe worth a try), go ahead and file a bug with gnome-power-manager and use other power saving techniques  (like hibernate) until you get a response.

Best Wishes!

---

