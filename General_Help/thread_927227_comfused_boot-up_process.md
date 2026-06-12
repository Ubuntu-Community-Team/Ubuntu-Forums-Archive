---
title: "comfused boot-up process"
date: 2008-09-22
forum: General Help
---

### Post by eotakos on 2008-09-22
There are two things that i installed manually (no apt/synaptic) that were added to the boot-up process. The first was HP's device manager for my printer, the other one was the Personal Solution Pack for my MGE ups.

Ever since I installed the second one, the startup procedure isn't that consistent; one time the one of the two won't start, the other time the other, and sometimes none of them will start. I've also noticed that when it's time for the system to run a fsck at boot-up, it's almost certain that the ups program won't start.

any ideas? where to look?

---

### Post by cariboo on 2008-09-22
Just to let you know, the hp drivers are installed by default in hardy, You have  to install the gui, if you need it.

The only thing I can see that would cause a problem is the order the services are started on boot up. You can go to /etc/rc1.d to /etc/rc6.d
and check what order the services are started you should see something like this:

```
S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-09-19 11:16 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-09-19 10:57 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-09-19 10:56 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-09-19 11:02 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
```

This is only a short snippet, but it should give you the idea how it is setup.

Jim

---

### Post by eotakos on 2008-09-23
that was new to me so, thanks!

the way i knew was through the boot up manager (bum) and the startup services shown at the system->preferences->sessions. But with neither of those would I make any difference.

actually when the ups program doesn't start, i know how to start it manually. Should I try to edit any of those scripts under the init.d? but then... how come and most of the time it works?... nothing happens accidentaly...(!) does it?  

if it rings any bell, the complete procedure to make the ups program work goes like this:

1st i have to start the driver 

2nd there is a program linking the driver with the frontend that should be started

and 3rd comes the program itself.

what i think that happens is that steps 1 and 2 aren't completed and so the program can't ran. I'm saying this because if try to run the program itself, it wouldn't ran; but if i complete steps 1 and 2, everything will run normally.

i don't know if i said too much, but thanks for your time anyway! :-)

---

