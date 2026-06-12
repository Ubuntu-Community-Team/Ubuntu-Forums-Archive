---
title: "New processes start very slowly after suspend / standby"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by ceekay on 2005-01-24
I have an IBM Thinkpad 600X and I used to run gentoo on it. After I broke something and didn't feel like spending two days reinstalling, I decided to try Ubuntu on it. I'm really liking it, but I'm having problems putting it into suspend mode- well, rather, using it after I've suspended and resumed.

**The problem:** 
I put the laptop to sleep using "sudo apm -s". It suspends fine, just as it used to in Gentoo. When I bring it back, it seems to come back fine-- until I try to start a new process. Even opening a terminal takes like 25 seconds.

**Things I have tried:** 
[list]
[*]Using APM
[*]Using ACPI
[*]Updating my kernel (running 2.6.10-2 now)
[*]Stopping X before suspend
[*]Restarting X after resume
[*]Disabling acpid/apmd scripts
[*]Using X.org instead of XF86
[*]Upgrading to hoary
[*]Ejecting pcmcia cards before/after suspend/resume
[/list]

The only thing that seems to fix it is restarting the computer. Unfortunately, that means my suspend functionality is basically worthless. I had it working on a 2.6.9 kernel in Gentoo, so I know this is possible with this laptop. I am thinking maybe it is a service that doesn't like to be suspended. Has anyone else seen this type of behavior?

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=ceekay]I have an IBM Thinkpad 600X and I used to run gentoo on it. After I broke something and didn't feel like spending two days reinstalling, I decided to try Ubuntu on it. I'm really liking it, but I'm having problems putting it into suspend mode- well, rather, using it after I've suspended and resumed.

**The problem:** 
I put the laptop to sleep using "sudo apm -s". It suspends fine, just as it used to in Gentoo. When I bring it back, it seems to come back fine-- until I try to start a new process. Even opening a terminal takes like 25 seconds.

**Things I have tried:** 
[list]
[*]Using APM
[*]Using ACPI
[*]Updating my kernel (running 2.6.10-2 now)
[*]Stopping X before suspend
[*]Restarting X after resume
[*]Disabling acpid/apmd scripts
[*]Using X.org instead of XF86
[*]Upgrading to hoary
[*]Ejecting pcmcia cards before/after suspend/resume
[/list]

The only thing that seems to fix it is restarting the computer. Unfortunately, that means my suspend functionality is basically worthless. I had it working on a 2.6.9 kernel in Gentoo, so I know this is possible with this laptop. I am thinking maybe it is a service that doesn't like to be suspended. Has anyone else seen this type of behavior?[/QUOTE]

I've heard that using APM instead of APCI in Warty works better.

Using Hoary might make the problem worse- it is unstable!

---

### Post by ceekay on 2005-01-31
No, apm exhibits this behavior in warty too.

---

### Post by jalexstark on 2005-03-23
Ideas?

I am getting similar problems.  They are strange.  I have 2.8.6.1-5-386.

Symptoms:
Applications are slow to start.  Sometimes, eg terminal window, they are quicker to start subsequently.  Evolution sometimes takes ages to open a reply window.

This looks to me like some sort of Gnome or maybe network problem.  The actual processing does not seem to be a problem, rather something appears to be waiting.

dmesg, /var/log/message, top do not suggest anything unusual.

/Alex.

---

