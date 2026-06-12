---
title: "No splash screen and two kernels available after update"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by pbrugs on 2009-06-27
Hello, I just ran an update on ubuntu and everything went fine, but now when i boot, there are two ubuntu kernels in GRUB. each one is exactly the same and the system has the same settings on both. but why are there two? also each one does not show the ubuntu splash screen when i boot. the screen is just black and then the login window appears. it isnt really a problem except i would like to know what is going on.

---

### Post by mikewhatever on 2009-06-27
Are you sure the kernels are the same? There has, recently, been an update from 2.6.28-11 to 2.6.28-13. When the kernel is updated, the old one is usually retained just in case.

---

### Post by pbrugs on 2009-06-27
well that makes sense. i remember getting a kernal upgrade. but what about the missing startup screen

---

### Post by mikewhatever on 2009-06-28
No idea about the starup/splash screen.

---

### Post by chngr on 2009-07-02
I am having the same problem. Besides not showing splash screen,
My computer is getting unstable after the kernel upgrade to 2.6.28-13,
Opera, Firefox crashes constantly or screen completely freezes.

Any idea ?

---

### Post by techrascal on 2009-07-02
hey....
same prolem here.......system crashed after this kernel upgrade....

when i try to boot into ubuntu i get the following error:

/lib/lsb/init-functions: 1: syntax error: newline unexpected
error:'/etc/initd/rc' exited outside the expected codeflow
init: rcS main process(852) terminated with exit status2
/lib/lsb/init-functions: 1: syntax error: newline unexpected
error:'/etc/initd/rc' exited outside the expected codeflow
init: rc2 main process(861) terminated with exit status2



then it refuses to budge and i have to hard quit...


also....i'm running ubuntu9.04 on an external hard drive with dual boot with vista.....
the recovery mode is not able to repair broken packages with dpkg....

while booting it also showed error 21.....

---

### Post by raymondh on 2009-07-02
use the older, working kernel.

If, and when, booted properly, you can edit menu.lst to default to that kernel or, install startupmanager and edit from there as it also writes to the menu.lst.  

Use the older kernel while tweaking the newer, problematic kernel until ready.

---

### Post by chngr on 2009-07-02
Hey guys,
I think I found a solution to *splash screen*. But I don't know how this was done :)

First, I checked UUID of swap partiton if it's OK in
```

/etc/initramfs-tools/conf.d/resume
```
and then i issued
```

sudo update-initramfs -u
```
When I reboot the computer, I saw the splash screen. This was done completely unconciously, I just only wanted my computer to suspend and
resume from flawlesly. I couldn't resume from suspend but splash screen is back. I hope this works for you.
And What about suspend and hibernate ?

---

