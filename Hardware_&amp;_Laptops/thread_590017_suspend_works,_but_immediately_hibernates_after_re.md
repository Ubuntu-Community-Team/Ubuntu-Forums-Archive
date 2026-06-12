---
title: "suspend works, but immediately hibernates after resume"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by flar on 2007-10-24
My Acer laptop suspends to RAM and resumes perfectly if I do do it manually (ie: hit the suspend button or go to system>quit>suspend)

I have it set to suspend (sleep) in the gnome-power-manager when idle.  When idle, it suspends fine. Upon resume, the desktop comes back seemingly fine, but in the bottom left corner there is a box saying suspend failed.  Before I can do anything, the laptop hibernates.  When I turn it back on, it resumes from hibernating perfectly fine, but also says hibernate failed.  It didn't fail though, everything works perfectly fine.  


How can I stop it from hibernating immediately after resuming from suspend? And why is there different behaviour when suspending manually and automatically?

---

### Post by flar on 2007-10-24
If I disable hibernate in gnome-power-manager settings (have to do it in gconf-editor), then when it returns from suspend it works fine although it still says suspend failed. 

This is unacceptable though, because I would like to use hibernate too.  

Anyone familiar with gnome-power-manager?

Is there a script I could modify so it doesn't try to hibernate after resuming?

---

### Post by flar on 2007-10-24
didn't really fix the problem, but this hack works for now:

download the gnome-power-manager source code

edit src/gpm-manager.c

comment out line 737 (this line tells it to try hibernating if suspend fails)

then rebuild and install

---

### Post by flar on 2007-10-25
my crappy hack doesn't really work because gnome-power-manager still views the suspend as a failure and disables and further suspending  when idle.

---

### Post by CowzRule on 2007-10-25
I also have an Acer laptop, an Aspire 3000. I have the same exact suspend/hibernate problem as you.
I believe it's an acpi/hardware incompatibility. The reason I say this is from what I have to do to get the wireless to work. It's has a Broadcom 4318 which is a rather popular card, but the standard method of getting the card to work with ndiswrapper doesn't work. With Acer laptops and this card you have to get another package and build a file from it called "acer_acpi.ko" and copy it to \lib\modules\2.6.22-14-generic\kernel\drivers\char.
Also, I've done a search in these forums for "Acer" to get a feel for how this laptop will perform with Ubuntu and from the threads I've browsed I've got the impression that the laptop will perform rather well overall but with a couple hardware incompatibilities.
So even though you'll see threads here about how people are having problems with Gutsy's suspend, I believe our problem is with our hardware.

---

### Post by flar on 2007-10-25
Yes, I'm quite pleased overall.  This suspend issue is actually the only little sticking point with my Acer, everything else works fine : sound, webcam, function keys, etc..

---

### Post by agapito on 2007-10-25
I have exactly the same problem on my Fujitsu/Siemens laptop... Suspend and hibernate were working fine on Feisty and the problem only started after I upgraded to Gutsy. This means that, at least in my case, the problem is software related. Has anyone found a solution for this?

---

### Post by rsf33 on 2008-01-07
I am seeing the exact same hibernate-after-resume-from-suspend behavior on my HP Pavilion a6200n desktop running Ubuntu 7.10. If I suspend using the suspend key, resume works fine. If the computer suspends due to idleness, then a few seconds after resuming the computer hibernates.

Has anybody figured out what the problem is? Does anybody have any suggestions for how to troubleshoot this problem?

Thanks!
- Roger

---

### Post by kriegaffe on 2008-01-08
I think I have the same problem. Quite sure really. 

Ubuntu 7.10, HP pavillion ze2247ea. In 7.04 it returned unresponsive most everytime it tried to suspend (sometimes even after the screensaver kicking in). That problem went away when i stopped using the proprietary ATI driver. 

I'd like to second rsf33: How does one go about finding the root off the problem?

---

### Post by kriegaffe on 2008-01-08
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149665]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149665")

---

### Post by rsf33 on 2008-01-08
Thank you kriegaffe for the reference URL. So it looks like other people are experiencing the same behavior we are. But from reading through the thread you cited, it isn't clear to me what the resolution is. Is there a way to work around the problem so that gnome-power-manager can safely suspend the computer when it is idle? Or is there a new version of gnome-power-manager coming soon?

---

### Post by kriegaffe on 2008-01-22
Sorry, didn't notice we were on the second page here, which is why my reply is a bit late.

Suppose these two posts (which I didn't notice the last time I read the link), can offer some insight? I've disabled can_suspend through gconf-editor. Will post if it makes a difference.

>  Justin Sunseri  wrote on 2007-10-26:  (permalink)

This bug really needs to be moved to gnome-power-manager. After disabling
can_hibernate in the gnome-power-manager section with the gconf editor i no
longer have the problem.
 
>  Oliver Grawert  wrote on 2007-10-27:  (permalink)

i'm waiting for upstream to release 2.20.1, since its filed and fixed upstream i expect the fix to be in there, please be patient :)


---

### Post by rsf33 on 2008-01-22
Disabling hibernate in gconf-editor mostly fixes the hibernate-after-resume problem on my HP Pavilion a6200n desktop running Gutsy. I say "mostly" because when the system resumes, a window appears saying the computer failed to suspend.

Is there an ETA on when gconf-power-manager 2.20.1 will be made available?

---

### Post by Xanf on 2008-04-13
I have the same problem on my desktop HP d530S.

Any news on the final fix for that?

---

### Post by rsf33 on 2008-04-13
I have not learned anything new on this subject in the almost 3 months since my last post. Disabling Hibernate worked most of the time, but about one time in five my HP Pavillion a6200n desktop would fail to resume from Suspend. In this case I would have to physically power cycle the machine.

I switched to Linux from Windows to get away from that sort of thing. So, on my system, the Suspend and Hibernate features of Ubuntu 7.10 are just too unstable to use. So I leave my computer on all the time and waste electricity instead. :-(

- Roger

---

### Post by glennric on 2008-05-01
I am having this issue in Hardy Heron (Ubuntu 8.04).  Does anyone know of a better workaround than disabling hibernation?

---

