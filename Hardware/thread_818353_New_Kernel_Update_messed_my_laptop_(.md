---
title: "New Kernel Update messed my laptop :("
date: 2008-06-04
forum: Hardware
---

### Post by cespinal on 2008-06-04
I made a System Update last night, it contained a new version of the Linux Kernel, among other things. BUT:

Emerald themer stopped working.

Flash movies on Firefox stopped working as well even tho I re-installed the restricted extras and Flash plugins. 

Now it takes AGES for the laptop to recognise Wi-Fi signal, this was done instantaneously before. This one is preTty irritating.
 
Last but not least, If I click on the Log out icon, the upper and lower taskbars dissapear so im not able to resume working, leaving forced shutting down with the power button as my only way out of it

I need HELP, this is driving my laptop completely disfunctional and I do not wanna go back to Vista! 

Thanks!!!

---

### Post by sergiom99 on 2008-06-04
same thing here.
compiz/emerald now suck and when I poweroff/reboot from Kmenu I got this black screen and can only resume the process when I click ctrl+alt+del.
If I write poweroff/reboot from Konsole, it works just fine.

---

### Post by stchman on 2008-06-04
> **cespinal said:**
> I made a System Update last night, it contained a new version of the Linux Kernel, among other things. BUT:

Emerald themer stopped working.

Flash movies on Firefox stopped working as well even tho I re-installed the restricted extras and Flash plugins. 

Now it takes AGES for the laptop to recognise Wi-Fi signal, this was done instantaneously before. This one is preTty irritating.
 
Last but not least, If I click on the Log out icon, the upper and lower taskbars dissapear so im not able to resume working, leaving forced shutting down with the power button as my only way out of it

I need HELP, this is driving my laptop completely disfunctional and I do not wanna go back to Vista! 

Thanks!!!

If you hit ESC during bootup it will bring up GRUB.  You can select the -17 kernel and using StartUpManager make it the default.

Ubuntu leaves the old kernel on the machine for compatibility purposes.

The -18 kernel worked perfectly on all 3 of my PCs.

---

### Post by cespinal on 2008-06-04
It did not work :( I restarted it just to find the old kernel was still there, so I booted it up... but I still had the same problems...

---

### Post by stchman on 2008-06-04
> **cespinal said:**
> It did not work :( I restarted it just to find the old kernel was still there, so I booted it up... but I still had the same problems...

You said the -17 kernel worked perfectly.  It should still work perfectly.

Best thing to do is to see if the new kernel is giving you problems.  If it is then switch back to the old kernel.  DO not install a bunch of software and muck around.  Just use the old kernel.

---

### Post by ohiomoto on 2008-06-04
Did mine in too!  I was able to fix it.  Here is the link to my post...use at own risk-I'm no expert, but I did sleep at a Holiday Inn Express last night.

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

Good luck!

---

### Post by cespinal on 2008-06-04
I will try this as soon as I get home... 

Im no expert either but maybe the new Kernel is conflicting with the old ones.. 

Lesson learned from this: dont do any major update unless you check the forums to see the reactions from the very first victims lol 

wish me luck...

---

### Post by sergim on 2008-06-04
I don't know if my problem was the same, but to solve it I had to install the graphics driver again. The official ones not the ones in rpositories 

P.S. Ati user

---

### Post by cespinal on 2008-06-04
thats it... al already solve this by deleting the old generic kernels!!!

---

